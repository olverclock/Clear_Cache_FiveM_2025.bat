@echo off
color 0A
title OLVER CLOCK

REM Exibe o logotipo "OLVER CLOCK"
echo:
echo  ██████╗ ██╗      ██╗   ██╗███████╗██████╗ 
echo ██╔═══██╗██║      ██║   ██║██╔════╝██╔══██╗
echo ██║   ██║██║      ██║   ██║█████╗  ██████╔╝
echo ██║   ██║██║      ██║   ██║██╔══╝  ██╔══██╗
echo ╚██████╔╝███████╗ ╚██████╔╝███████╗██║  ██║
echo  ╚═════╝ ╚══════╝  ╚═════╝ ╚══════╝╚═╝  ╚═╝
echo:
echo ==============================================
echo            Limpando Cache do FiveM
echo ==============================================

REM Definindo pastas para limpar
set "folders=%userprofile%\AppData\Local\FiveM\FiveM.app\data\cache
%userprofile%\AppData\Local\FiveM\FiveM.app\data\nui-storage
%userprofile%\AppData\Local\FiveM\FiveM.app\data\server-cache
%userprofile%\AppData\Local\FiveM\FiveM.app\data\server-cache-priv
%LocalAppData%\FiveM\FiveM.app\plugins
%LocalAppData%\FiveM\FiveM.app\mods
%LocalAppData%\FiveM\FiveM.app\logs
%LocalAppData%\FiveM\FiveM.app\crashes"
set "file=%LocalAppData%\FiveM\FiveM.app\adhesive.dll"

REM Contador de progresso
setlocal enabledelayedexpansion
set count=0
for %%A in (%folders%) do (
    set /a count+=1
)
set total=!count!
set count=0

REM Deletando Pastas com Status
for %%A in (%folders%) do (
    set /a count+=1
    echo Excluindo: %%A
    rmdir /s /q "%%A" 2>nul
    set /a progress=(!count!*100)/!total!
    echo Progresso: !progress!%%
    echo ----------------------------------------------
)

REM Deletando Arquivo
if exist "%file%" (
    echo Excluindo: %file%
    del /s /q /f "%file%" 2>nul
    echo Arquivo Excluído!
) else (
    echo Arquivo não encontrado: %file%
)

echo ==============================================
echo             Limpeza Concluída!
echo ==============================================
pause
