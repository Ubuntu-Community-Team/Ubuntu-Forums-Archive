---
title: "WUBI 9.10 wont install :("
date: 2009-10-08
forum: New to Ubuntu
---

### Post by blooboy on 2009-10-08
Hi Everybody!

I have Windows XP Prof. installed in my system. I wanted to install Ubuntu 9.04 via WUBI installation, but for some reason after half-way installation suddenly stops saying that permission is denied !!. The error message shows a permission denied message and an instruction to read the error log file wubi-9.04-rev128.log.

I dont understand why I cant install wubi for Ubuntu 9.04. Previously I had successfully installed and run Ubuntu 8.10 and Mint7 on it too. I am trying to install it in my D: drive. The C: drive is formatted and a new windows installation is on it.

Kindly help me.

```

PS: Contents of error log file ->
10-03 15:47 INFO   root: === wubi 9.04 rev128 ===
10-03 15:47 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-03 15:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
10-03 15:47 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\data
10-03 15:47 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\bin\7z.exe
10-03 15:47 DEBUG  CommonBackend: Fetching basic info...
10-03 15:47 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-03 15:47 DEBUG  CommonBackend: platform=win32
10-03 15:47 DEBUG  CommonBackend: osname=nt
10-03 15:47 DEBUG  CommonBackend: language=en_US
10-03 15:47 DEBUG  CommonBackend: encoding=cp1252
10-03 15:47 DEBUG  WindowsBackend: arch=amd64
10-03 15:47 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\data\isolist.ini
10-03 15:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-03 15:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-03 15:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-03 15:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-03 15:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-03 15:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-03 15:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-03 15:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-03 15:47 DEBUG  WindowsBackend: Fetching host info...
10-03 15:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-03 15:47 DEBUG  WindowsBackend: windows version=xp
10-03 15:47 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-03 15:47 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-03 15:47 DEBUG  WindowsBackend: windows_build=2600
10-03 15:47 DEBUG  WindowsBackend: gmt=5
10-03 15:47 DEBUG  WindowsBackend: country=US
10-03 15:47 DEBUG  WindowsBackend: timezone=America/New_York
10-03 15:47 DEBUG  WindowsBackend: windows_username=alex
10-03 15:47 DEBUG  WindowsBackend: user_full_name=alex
10-03 15:47 DEBUG  WindowsBackend: user_directory=alex
10-03 15:47 DEBUG  WindowsBackend: windows_language_code=1033
10-03 15:47 DEBUG  WindowsBackend: windows_language=English
10-03 15:47 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-03 15:47 DEBUG  WindowsBackend: bootloader=xp
10-03 15:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8055.4375 mb free )
10-03 15:47 DEBUG  WindowsBackend: drive=Drive(C: hd 8055.4375 mb free )
10-03 15:47 DEBUG  WindowsBackend: drive=Drive(D: hd 33188.2304688 mb free ntfs)
10-03 15:47 DEBUG  WindowsBackend: drive=Drive(E: hd 5385.04296875 mb free ntfs)
10-03 15:47 DEBUG  WindowsBackend: drive=Drive(F: hd 674.53515625 mb free ntfs)
10-03 15:47 DEBUG  WindowsBackend: drive=Drive(G: hd 6190.49609375 mb free ntfs)
10-03 15:47 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-03 15:47 DEBUG  WindowsBackend: uninstaller_path=None
10-03 15:47 DEBUG  WindowsBackend: previous_target_dir=None
10-03 15:47 DEBUG  WindowsBackend: previous_distro_name=None
10-03 15:47 DEBUG  WindowsBackend: keyboard_id=67699721
10-03 15:47 DEBUG  WindowsBackend: keyboard_layout=us
10-03 15:47 DEBUG  WindowsBackend: keyboard_variant=
10-03 15:47 DEBUG  CommonBackend: locale=en_US.UTF-8
10-03 15:47 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-03 15:47 DEBUG  CommonBackend: Searching ISOs on USB devices
10-03 15:47 DEBUG  CommonBackend: Searching for local CDs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 15:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-03 15:47 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-03 15:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-03 15:47 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-03 15:47 INFO   root: Running the CD menu...
10-03 15:47 DEBUG  WindowsFrontend: __init__...
10-03 15:47 DEBUG  WindowsFrontend: on_init...
10-03 15:47 INFO   root: CD menu finished
10-03 15:47 INFO   root: Running the installer...
10-03 15:48 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=15000MB, distro_name=Ubuntu, language=English, username=alex
10-03 15:48 INFO   root: Received settings
10-03 15:48 DEBUG  TaskList: # Running tasklist...
10-03 15:48 DEBUG  TaskList: ## Running select_target_dir...
10-03 15:48 INFO   WindowsBackend: Installing into D:\ubuntu
10-03 15:48 DEBUG  TaskList: ## Finished select_target_dir
10-03 15:48 DEBUG  TaskList: ## Running create_dir_structure...
10-03 15:48 DEBUG  TaskList: ## Finished create_dir_structure
10-03 15:48 DEBUG  TaskList: ## Running uncompress_target_dir...
10-03 15:48 DEBUG  TaskList: ## Finished uncompress_target_dir
10-03 15:48 DEBUG  TaskList: ## Running create_uninstaller...
10-03 15:48 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-03 15:48 DEBUG  TaskList: ## Finished create_uninstaller
10-03 15:48 DEBUG  TaskList: ## Running copy_installation_files...
10-03 15:48 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl55.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-03 15:48 ERROR  TaskList: [Errno 17] File exists: 'D:\\ubuntu\\install\\custom-installation'
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 150, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\shutil.py", line 102, in copytree
OSError: [Errno 17] File exists: 'D:\\ubuntu\\install\\custom-installation'
10-03 15:48 DEBUG  TaskList: # Cancelling tasklist
10-03 15:48 ERROR  root: [Errno 17] File exists: 'D:\\ubuntu\\install\\custom-installation'
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
OSError: [Errno 17] File exists: 'D:\\ubuntu\\install\\custom-installation'
10-03 15:48 DEBUG  TaskList: # Finished tasklist
10-03 15:48 INFO   root: === wubi 9.04 rev128 ===
10-03 15:48 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-03 15:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
10-03 15:48 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\data
10-03 15:48 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\bin\7z.exe
10-03 15:48 DEBUG  CommonBackend: Fetching basic info...
10-03 15:48 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-03 15:48 DEBUG  CommonBackend: platform=win32
10-03 15:48 DEBUG  CommonBackend: osname=nt
10-03 15:48 DEBUG  CommonBackend: language=en_US
10-03 15:48 DEBUG  CommonBackend: encoding=cp1252
10-03 15:48 DEBUG  WindowsBackend: arch=amd64
10-03 15:48 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\data\isolist.ini
10-03 15:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-03 15:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-03 15:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-03 15:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-03 15:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-03 15:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-03 15:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-03 15:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-03 15:48 DEBUG  WindowsBackend: Fetching host info...
10-03 15:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-03 15:48 DEBUG  WindowsBackend: windows version=xp
10-03 15:48 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-03 15:48 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-03 15:48 DEBUG  WindowsBackend: windows_build=2600
10-03 15:48 DEBUG  WindowsBackend: gmt=5
10-03 15:48 DEBUG  WindowsBackend: country=US
10-03 15:48 DEBUG  WindowsBackend: timezone=America/New_York
10-03 15:48 DEBUG  WindowsBackend: windows_username=alex
10-03 15:48 DEBUG  WindowsBackend: user_full_name=alex
10-03 15:48 DEBUG  WindowsBackend: user_directory=alex
10-03 15:48 DEBUG  WindowsBackend: windows_language_code=1033
10-03 15:48 DEBUG  WindowsBackend: windows_language=English
10-03 15:48 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-03 15:48 DEBUG  WindowsBackend: bootloader=xp
10-03 15:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8055.29296875 mb free )
10-03 15:48 DEBUG  WindowsBackend: drive=Drive(C: hd 8055.29296875 mb free )
10-03 15:48 DEBUG  WindowsBackend: drive=Drive(D: hd 33611.4296875 mb free ntfs)
10-03 15:48 DEBUG  WindowsBackend: drive=Drive(E: hd 5385.04296875 mb free ntfs)
10-03 15:48 DEBUG  WindowsBackend: drive=Drive(F: hd 674.53515625 mb free ntfs)
10-03 15:48 DEBUG  WindowsBackend: drive=Drive(G: hd 6190.49609375 mb free ntfs)
10-03 15:48 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-03 15:48 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-03 15:48 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-03 15:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-03 15:48 DEBUG  WindowsBackend: keyboard_id=67699721
10-03 15:48 DEBUG  WindowsBackend: keyboard_layout=us
10-03 15:48 DEBUG  WindowsBackend: keyboard_variant=
10-03 15:48 DEBUG  CommonBackend: locale=en_US.UTF-8
10-03 15:48 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-03 15:48 DEBUG  CommonBackend: Searching ISOs on USB devices
10-03 15:48 DEBUG  CommonBackend: Searching for local CDs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 15:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-03 15:48 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-03 15:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-03 15:48 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-03 15:48 INFO   root: Running the CD menu...
10-03 15:48 DEBUG  WindowsFrontend: __init__...
10-03 15:48 DEBUG  WindowsFrontend: on_init...
10-03 15:48 INFO   root: CD menu finished
10-03 15:48 INFO   root: Running the installer...
10-03 15:48 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Ubuntu, language=English, username=alex
10-03 15:48 INFO   root: Received settings
10-03 15:48 DEBUG  TaskList: # Running tasklist...
10-03 15:48 DEBUG  TaskList: ## Running select_target_dir...
10-03 15:48 INFO   WindowsBackend: Installing into D:\ubuntu
10-03 15:48 DEBUG  TaskList: ## Finished select_target_dir
10-03 15:48 DEBUG  TaskList: ## Running create_dir_structure...
10-03 15:48 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-03 15:48 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-03 15:48 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-03 15:48 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-03 15:48 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-03 15:48 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-03 15:48 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-03 15:48 DEBUG  TaskList: ## Finished create_dir_structure
10-03 15:48 DEBUG  TaskList: ## Running uncompress_target_dir...
10-03 15:48 DEBUG  TaskList: ## Finished uncompress_target_dir
10-03 15:48 DEBUG  TaskList: ## Running create_uninstaller...
10-03 15:48 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-03 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-03 15:48 DEBUG  TaskList: ## Finished create_uninstaller
10-03 15:48 DEBUG  TaskList: ## Running copy_installation_files...
10-03 15:48 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-03 15:48 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\winboot -> D:\ubuntu\winboot
10-03 15:48 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl56.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-03 15:48 DEBUG  TaskList: ## Finished copy_installation_files
10-03 15:48 DEBUG  TaskList: ## Running get_iso...
10-03 15:48 DEBUG  TaskList: New task copy_file
10-03 15:48 DEBUG  TaskList: ### Running copy_file...
10-03 15:51 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
10-03 15:51 DEBUG  TaskList: # Cancelling tasklist
10-03 15:51 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
10-03 15:51 DEBUG  TaskList: New task check_iso
10-03 15:51 DEBUG  CommonBackend: Searching for local ISO
10-03 15:51 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-03 15:51 DEBUG  TaskList: New task get_metalink
10-03 15:51 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-03 15:51 DEBUG  TaskList: # Cancelling tasklist
10-03 15:51 DEBUG  TaskList: # Finished tasklist
10-03 15:53 INFO   root: === wubi 9.04 rev128 ===
10-03 15:53 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-03 15:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-03 15:53 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\data
10-03 15:53 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\bin\7z.exe
10-03 15:53 DEBUG  CommonBackend: Fetching basic info...
10-03 15:53 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-03 15:53 DEBUG  CommonBackend: platform=win32
10-03 15:53 DEBUG  CommonBackend: osname=nt
10-03 15:53 DEBUG  CommonBackend: language=en_US
10-03 15:53 DEBUG  CommonBackend: encoding=cp1252
10-03 15:53 DEBUG  WindowsBackend: arch=amd64
10-03 15:53 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\data\isolist.ini
10-03 15:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-03 15:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-03 15:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-03 15:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-03 15:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-03 15:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-03 15:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-03 15:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-03 15:53 DEBUG  WindowsBackend: Fetching host info...
10-03 15:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-03 15:53 DEBUG  WindowsBackend: windows version=xp
10-03 15:53 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-03 15:53 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-03 15:53 DEBUG  WindowsBackend: windows_build=2600
10-03 15:53 DEBUG  WindowsBackend: gmt=5
10-03 15:53 DEBUG  WindowsBackend: country=US
10-03 15:53 DEBUG  WindowsBackend: timezone=America/New_York
10-03 15:53 DEBUG  WindowsBackend: windows_username=alex
10-03 15:53 DEBUG  WindowsBackend: user_full_name=alex
10-03 15:53 DEBUG  WindowsBackend: user_directory=alex
10-03 15:53 DEBUG  WindowsBackend: windows_language_code=1033
10-03 15:53 DEBUG  WindowsBackend: windows_language=English
10-03 15:53 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-03 15:53 DEBUG  WindowsBackend: bootloader=xp
10-03 15:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8052.89453125 mb free )
10-03 15:53 DEBUG  WindowsBackend: drive=Drive(C: hd 8052.89453125 mb free )
10-03 15:53 DEBUG  WindowsBackend: drive=Drive(D: hd 33186.5039063 mb free ntfs)
10-03 15:53 DEBUG  WindowsBackend: drive=Drive(E: hd 5385.04296875 mb free ntfs)
10-03 15:53 DEBUG  WindowsBackend: drive=Drive(F: hd 674.53515625 mb free ntfs)
10-03 15:53 DEBUG  WindowsBackend: drive=Drive(G: hd 6190.49609375 mb free ntfs)
10-03 15:53 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-03 15:53 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-03 15:53 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-03 15:53 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-03 15:53 DEBUG  WindowsBackend: keyboard_id=67699721
10-03 15:53 DEBUG  WindowsBackend: keyboard_layout=us
10-03 15:53 DEBUG  WindowsBackend: keyboard_variant=
10-03 15:53 DEBUG  CommonBackend: locale=en_US.UTF-8
10-03 15:53 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-03 15:53 DEBUG  CommonBackend: Searching ISOs on USB devices
10-03 15:53 DEBUG  CommonBackend: Searching for local CDs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl57.tmp\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 15:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 15:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-03 15:53 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-03 15:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-03 15:53 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-03 15:53 INFO   root: Running the uninstaller...
10-03 15:53 INFO   CommonBackend: This is the uninstaller running
10-03 15:53 DEBUG  WindowsFrontend: __init__...
10-03 15:53 DEBUG  WindowsFrontend: on_init...
10-03 15:53 INFO   root: Received settings
10-03 15:53 DEBUG  TaskList: # Running tasklist...
10-03 15:53 DEBUG  TaskList: ## Running Backup ISO...
10-03 15:53 DEBUG  TaskList: ## Finished Backup ISO
10-03 15:53 DEBUG  TaskList: ## Running Remove bootloader entry...
10-03 15:53 ERROR  WindowsBackend: Cannot find bcdedit
10-03 15:53 DEBUG  WindowsBackend: undo_bootini C:
10-03 15:53 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8052.89453125 mb free )
10-03 15:53 DEBUG  WindowsBackend: undo_bootini D:
10-03 15:53 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 33186.5039063 mb free ntfs)
10-03 15:53 DEBUG  WindowsBackend: undo_bootini E:
10-03 15:53 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 5385.04296875 mb free ntfs)
10-03 15:53 DEBUG  WindowsBackend: undo_bootini F:
10-03 15:53 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 674.53515625 mb free ntfs)
10-03 15:53 DEBUG  WindowsBackend: undo_bootini G:
10-03 15:53 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 6190.49609375 mb free ntfs)
10-03 15:53 DEBUG  TaskList: ## Finished Remove bootloader entry
10-03 15:53 DEBUG  TaskList: ## Running Remove target dir...
10-03 15:53 DEBUG  CommonBackend: Deleting D:\ubuntu
10-03 15:53 DEBUG  TaskList: ## Finished Remove target dir
10-03 15:53 DEBUG  TaskList: ## Running Remove registry key...
10-03 15:53 DEBUG  TaskList: ## Finished Remove registry key
10-03 15:53 DEBUG  TaskList: # Finished tasklist
10-03 15:53 INFO   root: Almost finished uninstalling
10-03 15:53 INFO   root: Finished uninstallation
10-03 15:53 DEBUG  root: application.quit
10-03 15:53 DEBUG  WindowsFrontend: frontend.quit
10-03 15:53 DEBUG  WindowsFrontend: frontend.on_quit
10-03 15:53 DEBUG  root: application.on_quit
10-03 15:53 INFO   root: sys.exit
10-03 16:04 INFO   root: === wubi 9.04 rev128 ===
10-03 16:04 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-03 16:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
10-03 16:04 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\data
10-03 16:04 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\bin\7z.exe
10-03 16:04 DEBUG  CommonBackend: Fetching basic info...
10-03 16:04 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-03 16:04 DEBUG  CommonBackend: platform=win32
10-03 16:04 DEBUG  CommonBackend: osname=nt
10-03 16:04 DEBUG  CommonBackend: language=en_US
10-03 16:04 DEBUG  CommonBackend: encoding=cp1252
10-03 16:04 DEBUG  WindowsBackend: arch=amd64
10-03 16:04 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\data\isolist.ini
10-03 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-03 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-03 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-03 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-03 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-03 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-03 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-03 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-03 16:04 DEBUG  WindowsBackend: Fetching host info...
10-03 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-03 16:04 DEBUG  WindowsBackend: windows version=xp
10-03 16:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-03 16:04 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-03 16:04 DEBUG  WindowsBackend: windows_build=2600
10-03 16:04 DEBUG  WindowsBackend: gmt=5
10-03 16:04 DEBUG  WindowsBackend: country=US
10-03 16:04 DEBUG  WindowsBackend: timezone=America/New_York
10-03 16:04 DEBUG  WindowsBackend: windows_username=alex
10-03 16:04 DEBUG  WindowsBackend: user_full_name=alex
10-03 16:04 DEBUG  WindowsBackend: user_directory=alex
10-03 16:04 DEBUG  WindowsBackend: windows_language_code=1033
10-03 16:04 DEBUG  WindowsBackend: windows_language=English
10-03 16:04 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-03 16:04 DEBUG  WindowsBackend: bootloader=xp
10-03 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8052.70703125 mb free )
10-03 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 8052.70703125 mb free )
10-03 16:04 DEBUG  WindowsBackend: drive=Drive(D: hd 28491.4296875 mb free ntfs)
10-03 16:04 DEBUG  WindowsBackend: drive=Drive(E: hd 5385.04296875 mb free ntfs)
10-03 16:04 DEBUG  WindowsBackend: drive=Drive(F: hd 674.53515625 mb free ntfs)
10-03 16:04 DEBUG  WindowsBackend: drive=Drive(G: hd 11310.4960938 mb free ntfs)
10-03 16:04 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-03 16:04 DEBUG  WindowsBackend: uninstaller_path=None
10-03 16:04 DEBUG  WindowsBackend: previous_target_dir=None
10-03 16:04 DEBUG  WindowsBackend: previous_distro_name=None
10-03 16:04 DEBUG  WindowsBackend: keyboard_id=67699721
10-03 16:04 DEBUG  WindowsBackend: keyboard_layout=us
10-03 16:04 DEBUG  WindowsBackend: keyboard_variant=
10-03 16:04 DEBUG  CommonBackend: locale=en_US.UTF-8
10-03 16:04 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-03 16:04 DEBUG  CommonBackend: Searching ISOs on USB devices
10-03 16:04 DEBUG  CommonBackend: Searching for local CDs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 16:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-03 16:04 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-03 16:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-03 16:04 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-03 16:04 INFO   root: Running the CD menu...
10-03 16:04 DEBUG  WindowsFrontend: __init__...
10-03 16:04 DEBUG  WindowsFrontend: on_init...
10-03 16:04 INFO   root: CD menu finished
10-03 16:04 INFO   root: Running the installer...
10-03 16:04 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Ubuntu, language=English, username=alex
10-03 16:04 INFO   root: Received settings
10-03 16:04 DEBUG  TaskList: # Running tasklist...
10-03 16:04 DEBUG  TaskList: ## Running select_target_dir...
10-03 16:04 INFO   WindowsBackend: Installing into D:\ubuntu
10-03 16:04 DEBUG  TaskList: ## Finished select_target_dir
10-03 16:04 DEBUG  TaskList: ## Running create_dir_structure...
10-03 16:04 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-03 16:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-03 16:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-03 16:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-03 16:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-03 16:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-03 16:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-03 16:04 DEBUG  TaskList: ## Finished create_dir_structure
10-03 16:04 DEBUG  TaskList: ## Running uncompress_target_dir...
10-03 16:04 DEBUG  TaskList: ## Finished uncompress_target_dir
10-03 16:04 DEBUG  TaskList: ## Running create_uninstaller...
10-03 16:04 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-03 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-03 16:04 DEBUG  TaskList: ## Finished create_uninstaller
10-03 16:04 DEBUG  TaskList: ## Running copy_installation_files...
10-03 16:04 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-03 16:04 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\winboot -> D:\ubuntu\winboot
10-03 16:04 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl58.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-03 16:04 DEBUG  TaskList: ## Finished copy_installation_files
10-03 16:04 DEBUG  TaskList: ## Running get_iso...
10-03 16:04 DEBUG  TaskList: New task copy_file
10-03 16:04 DEBUG  TaskList: ### Running copy_file...
10-03 16:06 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
10-03 16:06 DEBUG  TaskList: # Cancelling tasklist
10-03 16:06 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
10-03 16:06 DEBUG  TaskList: New task check_iso
10-03 16:06 DEBUG  CommonBackend: Searching for local ISO
10-03 16:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-03 16:06 DEBUG  TaskList: New task get_metalink
10-03 16:06 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-03 16:06 DEBUG  TaskList: # Cancelling tasklist
10-03 16:06 DEBUG  TaskList: # Finished tasklist
10-03 16:10 INFO   root: === wubi 9.04 rev128 ===
10-03 16:10 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-03 16:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-03 16:10 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\data
10-03 16:10 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\bin\7z.exe
10-03 16:10 DEBUG  CommonBackend: Fetching basic info...
10-03 16:10 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-03 16:10 DEBUG  CommonBackend: platform=win32
10-03 16:10 DEBUG  CommonBackend: osname=nt
10-03 16:10 DEBUG  CommonBackend: language=en_US
10-03 16:10 DEBUG  CommonBackend: encoding=cp1252
10-03 16:10 DEBUG  WindowsBackend: arch=amd64
10-03 16:10 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\data\isolist.ini
10-03 16:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-03 16:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-03 16:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-03 16:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-03 16:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-03 16:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-03 16:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-03 16:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-03 16:10 DEBUG  WindowsBackend: Fetching host info...
10-03 16:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-03 16:10 DEBUG  WindowsBackend: windows version=xp
10-03 16:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-03 16:10 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-03 16:10 DEBUG  WindowsBackend: windows_build=2600
10-03 16:10 DEBUG  WindowsBackend: gmt=5
10-03 16:10 DEBUG  WindowsBackend: country=US
10-03 16:10 DEBUG  WindowsBackend: timezone=America/New_York
10-03 16:10 DEBUG  WindowsBackend: windows_username=alex
10-03 16:10 DEBUG  WindowsBackend: user_full_name=alex
10-03 16:10 DEBUG  WindowsBackend: user_directory=alex
10-03 16:10 DEBUG  WindowsBackend: windows_language_code=1033
10-03 16:10 DEBUG  WindowsBackend: windows_language=English
10-03 16:10 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-03 16:10 DEBUG  WindowsBackend: bootloader=xp
10-03 16:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8052.390625 mb free )
10-03 16:10 DEBUG  WindowsBackend: drive=Drive(C: hd 8052.390625 mb free )
10-03 16:10 DEBUG  WindowsBackend: drive=Drive(D: hd 28066.5039063 mb free ntfs)
10-03 16:10 DEBUG  WindowsBackend: drive=Drive(E: hd 5385.04296875 mb free ntfs)
10-03 16:10 DEBUG  WindowsBackend: drive=Drive(F: hd 674.53515625 mb free ntfs)
10-03 16:10 DEBUG  WindowsBackend: drive=Drive(G: hd 11310.4960938 mb free ntfs)
10-03 16:10 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-03 16:10 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-03 16:10 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-03 16:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-03 16:10 DEBUG  WindowsBackend: keyboard_id=67699721
10-03 16:10 DEBUG  WindowsBackend: keyboard_layout=us
10-03 16:10 DEBUG  WindowsBackend: keyboard_variant=
10-03 16:10 DEBUG  CommonBackend: locale=en_US.UTF-8
10-03 16:10 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-03 16:10 DEBUG  CommonBackend: Searching ISOs on USB devices
10-03 16:10 DEBUG  CommonBackend: Searching for local CDs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl59.tmp\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 16:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-03 16:10 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-03 16:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-03 16:10 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-03 16:10 INFO   root: Running the uninstaller...
10-03 16:10 INFO   CommonBackend: This is the uninstaller running
10-03 16:10 DEBUG  WindowsFrontend: __init__...
10-03 16:10 DEBUG  WindowsFrontend: on_init...
10-03 16:10 INFO   root: Received settings
10-03 16:10 DEBUG  TaskList: # Running tasklist...
10-03 16:10 DEBUG  TaskList: ## Running Backup ISO...
10-03 16:10 DEBUG  TaskList: ## Finished Backup ISO
10-03 16:10 DEBUG  TaskList: ## Running Remove bootloader entry...
10-03 16:10 ERROR  WindowsBackend: Cannot find bcdedit
10-03 16:10 DEBUG  WindowsBackend: undo_bootini C:
10-03 16:10 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8052.390625 mb free )
10-03 16:10 DEBUG  WindowsBackend: undo_bootini D:
10-03 16:10 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 28066.5039063 mb free ntfs)
10-03 16:10 DEBUG  WindowsBackend: undo_bootini E:
10-03 16:10 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 5385.04296875 mb free ntfs)
10-03 16:10 DEBUG  WindowsBackend: undo_bootini F:
10-03 16:10 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 674.53515625 mb free ntfs)
10-03 16:10 DEBUG  WindowsBackend: undo_bootini G:
10-03 16:10 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 11310.4960938 mb free ntfs)
10-03 16:10 DEBUG  TaskList: ## Finished Remove bootloader entry
10-03 16:10 DEBUG  TaskList: ## Running Remove target dir...
10-03 16:10 DEBUG  CommonBackend: Deleting D:\ubuntu
10-03 16:10 DEBUG  TaskList: ## Finished Remove target dir
10-03 16:10 DEBUG  TaskList: ## Running Remove registry key...
10-03 16:10 DEBUG  TaskList: ## Finished Remove registry key
10-03 16:10 DEBUG  TaskList: # Finished tasklist
10-03 16:10 INFO   root: Almost finished uninstalling
10-03 16:10 INFO   root: Finished uninstallation
10-03 16:10 DEBUG  root: application.quit
10-03 16:10 DEBUG  WindowsFrontend: frontend.quit
10-03 16:10 DEBUG  WindowsFrontend: frontend.on_quit
10-03 16:10 DEBUG  root: application.on_quit
10-03 16:10 INFO   root: sys.exit
10-03 16:12 INFO   root: === wubi 9.04 rev128 ===
10-03 16:12 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-03 16:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
10-03 16:12 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\data
10-03 16:12 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\bin\7z.exe
10-03 16:12 DEBUG  CommonBackend: Fetching basic info...
10-03 16:12 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-03 16:12 DEBUG  CommonBackend: platform=win32
10-03 16:12 DEBUG  CommonBackend: osname=nt
10-03 16:12 DEBUG  CommonBackend: language=en_US
10-03 16:12 DEBUG  CommonBackend: encoding=cp1252
10-03 16:12 DEBUG  WindowsBackend: arch=amd64
10-03 16:12 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\data\isolist.ini
10-03 16:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-03 16:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-03 16:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-03 16:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-03 16:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-03 16:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-03 16:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-03 16:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-03 16:12 DEBUG  WindowsBackend: Fetching host info...
10-03 16:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-03 16:12 DEBUG  WindowsBackend: windows version=xp
10-03 16:12 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-03 16:12 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-03 16:12 DEBUG  WindowsBackend: windows_build=2600
10-03 16:12 DEBUG  WindowsBackend: gmt=5
10-03 16:12 DEBUG  WindowsBackend: country=US
10-03 16:12 DEBUG  WindowsBackend: timezone=America/New_York
10-03 16:12 DEBUG  WindowsBackend: windows_username=alex
10-03 16:12 DEBUG  WindowsBackend: user_full_name=alex
10-03 16:12 DEBUG  WindowsBackend: user_directory=alex
10-03 16:12 DEBUG  WindowsBackend: windows_language_code=1033
10-03 16:12 DEBUG  WindowsBackend: windows_language=English
10-03 16:12 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-03 16:12 DEBUG  WindowsBackend: bootloader=xp
10-03 16:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8050.87109375 mb free )
10-03 16:12 DEBUG  WindowsBackend: drive=Drive(C: hd 8050.87109375 mb free )
10-03 16:12 DEBUG  WindowsBackend: drive=Drive(D: hd 28491.4140625 mb free ntfs)
10-03 16:12 DEBUG  WindowsBackend: drive=Drive(E: hd 5385.04296875 mb free ntfs)
10-03 16:12 DEBUG  WindowsBackend: drive=Drive(F: hd 674.53515625 mb free ntfs)
10-03 16:12 DEBUG  WindowsBackend: drive=Drive(G: hd 11310.4960938 mb free ntfs)
10-03 16:12 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-03 16:12 DEBUG  WindowsBackend: uninstaller_path=None
10-03 16:12 DEBUG  WindowsBackend: previous_target_dir=None
10-03 16:12 DEBUG  WindowsBackend: previous_distro_name=None
10-03 16:12 DEBUG  WindowsBackend: keyboard_id=67699721
10-03 16:12 DEBUG  WindowsBackend: keyboard_layout=us
10-03 16:12 DEBUG  WindowsBackend: keyboard_variant=
10-03 16:12 DEBUG  CommonBackend: locale=en_US.UTF-8
10-03 16:12 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-03 16:12 DEBUG  CommonBackend: Searching ISOs on USB devices
10-03 16:12 DEBUG  CommonBackend: Searching for local CDs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-03 16:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-03 16:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-03 16:12 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-03 16:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-03 16:12 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-03 16:12 INFO   root: Running the CD menu...
10-03 16:12 DEBUG  WindowsFrontend: __init__...
10-03 16:12 DEBUG  WindowsFrontend: on_init...
10-03 16:12 INFO   root: CD menu finished
10-03 16:12 INFO   root: Running the installer...
10-03 16:13 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Ubuntu, language=English, username=alex
10-03 16:13 INFO   root: Received settings
10-03 16:13 DEBUG  TaskList: # Running tasklist...
10-03 16:13 DEBUG  TaskList: ## Running select_target_dir...
10-03 16:13 INFO   WindowsBackend: Installing into D:\ubuntu
10-03 16:13 DEBUG  TaskList: ## Finished select_target_dir
10-03 16:13 DEBUG  TaskList: ## Running create_dir_structure...
10-03 16:13 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-03 16:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-03 16:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-03 16:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-03 16:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-03 16:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-03 16:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-03 16:13 DEBUG  TaskList: ## Finished create_dir_structure
10-03 16:13 DEBUG  TaskList: ## Running uncompress_target_dir...
10-03 16:13 DEBUG  TaskList: ## Finished uncompress_target_dir
10-03 16:13 DEBUG  TaskList: ## Running create_uninstaller...
10-03 16:13 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-03 16:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-03 16:13 DEBUG  TaskList: ## Finished create_uninstaller
10-03 16:13 DEBUG  TaskList: ## Running copy_installation_files...
10-03 16:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-03 16:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\winboot -> D:\ubuntu\winboot
10-03 16:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5A.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-03 16:13 DEBUG  TaskList: ## Finished copy_installation_files
10-03 16:13 DEBUG  TaskList: ## Running get_iso...
10-03 16:13 DEBUG  TaskList: New task copy_file
10-03 16:13 DEBUG  TaskList: ### Running copy_file...
10-03 16:15 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
10-03 16:15 DEBUG  TaskList: # Cancelling tasklist
10-03 16:15 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
10-03 16:15 DEBUG  TaskList: New task check_iso
10-03 16:15 DEBUG  CommonBackend: Searching for local ISO
10-03 16:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-03 16:15 DEBUG  TaskList: New task get_metalink
10-03 16:15 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-03 16:15 DEBUG  TaskList: # Cancelling tasklist
10-03 16:15 DEBUG  TaskList: # Finished tasklist
10-05 12:02 INFO   root: === wubi 9.04 rev128 ===
10-05 12:02 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-05 12:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-05 12:02 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\data
10-05 12:02 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\bin\7z.exe
10-05 12:02 DEBUG  CommonBackend: Fetching basic info...
10-05 12:02 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-05 12:02 DEBUG  CommonBackend: platform=win32
10-05 12:02 DEBUG  CommonBackend: osname=nt
10-05 12:02 DEBUG  CommonBackend: language=en_US
10-05 12:02 DEBUG  CommonBackend: encoding=cp1252
10-05 12:02 DEBUG  WindowsBackend: arch=amd64
10-05 12:02 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\data\isolist.ini
10-05 12:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 12:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 12:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 12:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 12:02 DEBUG  WindowsBackend: Fetching host info...
10-05 12:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 12:02 DEBUG  WindowsBackend: windows version=xp
10-05 12:02 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 12:02 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-05 12:02 DEBUG  WindowsBackend: windows_build=2600
10-05 12:02 DEBUG  WindowsBackend: gmt=5
10-05 12:02 DEBUG  WindowsBackend: country=US
10-05 12:02 DEBUG  WindowsBackend: timezone=America/New_York
10-05 12:02 DEBUG  WindowsBackend: windows_username=alex
10-05 12:02 DEBUG  WindowsBackend: user_full_name=alex
10-05 12:02 DEBUG  WindowsBackend: user_directory=alex
10-05 12:02 DEBUG  WindowsBackend: windows_language_code=1033
10-05 12:02 DEBUG  WindowsBackend: windows_language=English
10-05 12:02 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-05 12:02 DEBUG  WindowsBackend: bootloader=xp
10-05 12:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7401.23828125 mb free )
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(C: hd 7401.23828125 mb free )
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(D: hd 21330.75 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(E: hd 5383.828125 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(F: hd 674.5390625 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(G: hd 18048.5 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(Z: hd 68.396484375 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-05 12:02 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-05 12:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-05 12:02 DEBUG  WindowsBackend: keyboard_id=67699721
10-05 12:02 DEBUG  WindowsBackend: keyboard_layout=us
10-05 12:02 DEBUG  WindowsBackend: keyboard_variant=
10-05 12:02 DEBUG  CommonBackend: locale=en_US.UTF-8
10-05 12:02 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-05 12:02 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 12:02 DEBUG  CommonBackend: Searching for local CDs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-05 12:02 INFO   root: === wubi 9.04 rev128 ===
10-05 12:02 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-05 12:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
10-05 12:02 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\data
10-05 12:02 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
10-05 12:02 DEBUG  CommonBackend: Fetching basic info...
10-05 12:02 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-05 12:02 DEBUG  CommonBackend: platform=win32
10-05 12:02 DEBUG  CommonBackend: osname=nt
10-05 12:02 DEBUG  CommonBackend: language=en_US
10-05 12:02 DEBUG  CommonBackend: encoding=cp1252
10-05 12:02 DEBUG  WindowsBackend: arch=amd64
10-05 12:02 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
10-05 12:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 12:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 12:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 12:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 12:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 12:02 DEBUG  WindowsBackend: Fetching host info...
10-05 12:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 12:02 DEBUG  WindowsBackend: windows version=xp
10-05 12:02 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 12:02 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-05 12:02 DEBUG  WindowsBackend: windows_build=2600
10-05 12:02 DEBUG  WindowsBackend: gmt=5
10-05 12:02 DEBUG  WindowsBackend: country=US
10-05 12:02 DEBUG  WindowsBackend: timezone=America/New_York
10-05 12:02 DEBUG  WindowsBackend: windows_username=alex
10-05 12:02 DEBUG  WindowsBackend: user_full_name=alex
10-05 12:02 DEBUG  WindowsBackend: user_directory=alex
10-05 12:02 DEBUG  WindowsBackend: windows_language_code=1033
10-05 12:02 DEBUG  WindowsBackend: windows_language=English
10-05 12:02 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-05 12:02 DEBUG  WindowsBackend: bootloader=xp
10-05 12:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7401.2265625 mb free )
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(C: hd 7401.2265625 mb free )
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(D: hd 21330.75 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(E: hd 5383.828125 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(F: hd 674.5390625 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(G: hd 18048.5 mb free ntfs)
10-05 12:02 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-05 12:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-05 12:02 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-05 12:02 INFO   root: Running the uninstaller...
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-05 12:02 DEBUG  WindowsBackend: drive=Drive(Z: hd 68.396484375 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-05 12:02 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-05 12:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-05 12:02 DEBUG  WindowsBackend: keyboard_id=67699721
10-05 12:02 DEBUG  WindowsBackend: keyboard_layout=us
10-05 12:02 DEBUG  WindowsBackend: keyboard_variant=
10-05 12:02 DEBUG  CommonBackend: locale=en_US.UTF-8
10-05 12:02 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-05 12:02 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 12:02 DEBUG  CommonBackend: Searching for local CDs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:02 INFO   CommonBackend: This is the uninstaller running
10-05 12:02 DEBUG  WindowsFrontend: __init__...
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  WindowsFrontend: on_init...
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-05 12:02 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-05 12:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-05 12:02 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-05 12:02 INFO   root: Running the CD menu...
10-05 12:02 DEBUG  WindowsFrontend: __init__...
10-05 12:02 DEBUG  WindowsFrontend: on_init...
10-05 12:02 INFO   root: Received settings
10-05 12:02 DEBUG  TaskList: # Running tasklist...
10-05 12:02 DEBUG  TaskList: ## Running Backup ISO...
10-05 12:02 DEBUG  TaskList: ## Finished Backup ISO
10-05 12:02 DEBUG  TaskList: ## Running Remove bootloader entry...
10-05 12:02 ERROR  WindowsBackend: Cannot find bcdedit
10-05 12:02 DEBUG  WindowsBackend: undo_bootini C:
10-05 12:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 7401.23828125 mb free )
10-05 12:02 DEBUG  WindowsBackend: undo_bootini D:
10-05 12:02 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 21330.75 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: undo_bootini E:
10-05 12:02 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 5383.828125 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: undo_bootini F:
10-05 12:02 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 674.5390625 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: undo_bootini G:
10-05 12:02 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 18048.5 mb free ntfs)
10-05 12:02 DEBUG  WindowsBackend: undo_bootini Z:
10-05 12:02 DEBUG  WindowsBackend: undo_configsys Drive(Z: hd 68.396484375 mb free ntfs)
10-05 12:02 DEBUG  TaskList: ## Finished Remove bootloader entry
10-05 12:02 DEBUG  TaskList: ## Running Remove target dir...
10-05 12:02 DEBUG  CommonBackend: Deleting D:\ubuntu
10-05 12:02 DEBUG  TaskList: ## Finished Remove target dir
10-05 12:02 DEBUG  TaskList: ## Running Remove registry key...
10-05 12:02 DEBUG  TaskList: ## Finished Remove registry key
10-05 12:02 DEBUG  TaskList: # Finished tasklist
10-05 12:02 INFO   root: Almost finished uninstalling
10-05 12:02 INFO   root: Finished uninstallation
10-05 12:02 DEBUG  root: application.quit
10-05 12:02 DEBUG  WindowsFrontend: frontend.quit
10-05 12:02 DEBUG  WindowsFrontend: frontend.on_quit
10-05 12:02 DEBUG  root: application.on_quit
10-05 12:02 INFO   root: sys.exit
10-05 12:03 INFO   root: CD menu finished
10-05 12:03 INFO   root: Running the installer...
10-05 12:03 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=12000MB, distro_name=Ubuntu, language=English, username=alex
10-05 12:03 INFO   root: Received settings
10-05 12:03 DEBUG  TaskList: # Running tasklist...
10-05 12:03 DEBUG  TaskList: ## Running select_target_dir...
10-05 12:03 INFO   WindowsBackend: Installing into G:\ubuntu
10-05 12:03 DEBUG  TaskList: ## Finished select_target_dir
10-05 12:03 DEBUG  TaskList: ## Running create_dir_structure...
10-05 12:03 DEBUG  CommonBackend: Creating dir G:\ubuntu
10-05 12:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
10-05 12:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
10-05 12:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
10-05 12:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
10-05 12:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
10-05 12:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
10-05 12:03 DEBUG  TaskList: ## Finished create_dir_structure
10-05 12:03 DEBUG  TaskList: ## Running uncompress_target_dir...
10-05 12:03 DEBUG  TaskList: ## Finished uncompress_target_dir
10-05 12:03 DEBUG  TaskList: ## Running create_uninstaller...
10-05 12:03 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-05 12:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-05 12:03 DEBUG  TaskList: ## Finished create_uninstaller
10-05 12:03 DEBUG  TaskList: ## Running copy_installation_files...
10-05 12:03 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
10-05 12:03 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\winboot -> G:\ubuntu\winboot
10-05 12:03 DEBUG  WindowsBackend: Copying C:\DOCUME~1\alex\LOCALS~1\Temp\pyl6.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
10-05 12:03 DEBUG  TaskList: ## Finished copy_installation_files
10-05 12:03 DEBUG  TaskList: ## Running get_iso...
10-05 12:03 DEBUG  TaskList: New task copy_file
10-05 12:03 DEBUG  TaskList: ### Running copy_file...
10-05 12:05 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
10-05 12:05 DEBUG  TaskList: # Cancelling tasklist
10-05 12:05 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
10-05 12:05 DEBUG  TaskList: New task check_iso
10-05 12:06 DEBUG  CommonBackend: Searching for local ISO
10-05 12:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-05 12:06 DEBUG  TaskList: New task get_metalink
10-05 12:06 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-05 12:06 DEBUG  TaskList: # Cancelling tasklist
10-05 12:06 DEBUG  TaskList: # Finished tasklist
10-05 12:07 INFO   root: === wubi 9.04 rev128 ===
10-05 12:07 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-05 12:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
10-05 12:07 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\data
10-05 12:07 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
10-05 12:07 DEBUG  CommonBackend: Fetching basic info...
10-05 12:07 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
10-05 12:07 DEBUG  CommonBackend: platform=win32
10-05 12:07 DEBUG  CommonBackend: osname=nt
10-05 12:07 DEBUG  CommonBackend: language=en_US
10-05 12:07 DEBUG  CommonBackend: encoding=cp1252
10-05 12:07 DEBUG  WindowsBackend: arch=amd64
10-05 12:07 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
10-05 12:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 12:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 12:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 12:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 12:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 12:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 12:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 12:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 12:07 DEBUG  WindowsBackend: Fetching host info...
10-05 12:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 12:07 DEBUG  WindowsBackend: windows version=xp
10-05 12:07 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 12:07 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-05 12:07 DEBUG  WindowsBackend: windows_build=2600
10-05 12:07 DEBUG  WindowsBackend: gmt=5
10-05 12:07 DEBUG  WindowsBackend: country=US
10-05 12:07 DEBUG  WindowsBackend: timezone=America/New_York
10-05 12:07 DEBUG  WindowsBackend: windows_username=alex
10-05 12:07 DEBUG  WindowsBackend: user_full_name=alex
10-05 12:07 DEBUG  WindowsBackend: user_directory=alex
10-05 12:07 DEBUG  WindowsBackend: windows_language_code=1033
10-05 12:07 DEBUG  WindowsBackend: windows_language=English
10-05 12:07 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-05 12:07 DEBUG  WindowsBackend: bootloader=xp
10-05 12:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7407.53125 mb free )
10-05 12:07 DEBUG  WindowsBackend: drive=Drive(C: hd 7407.53125 mb free )
10-05 12:07 DEBUG  WindowsBackend: drive=Drive(D: hd 21753.8203125 mb free ntfs)
10-05 12:07 DEBUG  WindowsBackend: drive=Drive(E: hd 5383.828125 mb free ntfs)
10-05 12:07 DEBUG  WindowsBackend: drive=Drive(F: hd 674.5390625 mb free ntfs)
10-05 12:07 DEBUG  WindowsBackend: drive=Drive(G: hd 17623.5429688 mb free ntfs)
10-05 12:07 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-05 12:07 DEBUG  WindowsBackend: drive=Drive(Z: hd 68.396484375 mb free ntfs)
10-05 12:07 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
10-05 12:07 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
10-05 12:07 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-05 12:07 DEBUG  WindowsBackend: keyboard_id=67699721
10-05 12:07 DEBUG  WindowsBackend: keyboard_layout=us
10-05 12:07 DEBUG  WindowsBackend: keyboard_variant=
10-05 12:07 DEBUG  CommonBackend: locale=en_US.UTF-8
10-05 12:07 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-05 12:07 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 12:07 DEBUG  CommonBackend: Searching for local CDs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-05 12:07 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-05 12:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-05 12:07 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-05 12:07 INFO   root: Running the uninstaller...
10-05 12:07 INFO   CommonBackend: This is the uninstaller running
10-05 12:07 DEBUG  WindowsFrontend: __init__...
10-05 12:07 DEBUG  WindowsFrontend: on_init...
10-05 12:08 INFO   root: Received settings
10-05 12:08 DEBUG  TaskList: # Running tasklist...
10-05 12:08 DEBUG  TaskList: ## Running Backup ISO...
10-05 12:08 DEBUG  TaskList: ## Finished Backup ISO
10-05 12:08 DEBUG  TaskList: ## Running Remove bootloader entry...
10-05 12:08 ERROR  WindowsBackend: Cannot find bcdedit
10-05 12:08 DEBUG  WindowsBackend: undo_bootini C:
10-05 12:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 7407.53125 mb free )
10-05 12:08 DEBUG  WindowsBackend: undo_bootini D:
10-05 12:08 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 21753.8203125 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: undo_bootini E:
10-05 12:08 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 5383.828125 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: undo_bootini F:
10-05 12:08 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 674.5390625 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: undo_bootini G:
10-05 12:08 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 17623.5429688 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: undo_bootini Z:
10-05 12:08 DEBUG  WindowsBackend: undo_configsys Drive(Z: hd 68.396484375 mb free ntfs)
10-05 12:08 DEBUG  TaskList: ## Finished Remove bootloader entry
10-05 12:08 DEBUG  TaskList: ## Running Remove target dir...
10-05 12:08 DEBUG  CommonBackend: Deleting G:\ubuntu
10-05 12:08 DEBUG  TaskList: ## Finished Remove target dir
10-05 12:08 DEBUG  TaskList: ## Running Remove registry key...
10-05 12:08 DEBUG  TaskList: ## Finished Remove registry key
10-05 12:08 DEBUG  TaskList: # Finished tasklist
10-05 12:08 INFO   root: Almost finished uninstalling
10-05 12:08 INFO   root: Finished uninstallation
10-05 12:08 DEBUG  root: application.quit
10-05 12:08 DEBUG  WindowsFrontend: frontend.quit
10-05 12:08 DEBUG  WindowsFrontend: frontend.on_quit
10-05 12:08 DEBUG  root: application.on_quit
10-05 12:08 INFO   root: sys.exit
10-05 12:08 INFO   root: === wubi 9.04 rev128 ===
10-05 12:08 DEBUG  root: Logfile is c:\docume~1\alex\locals~1\temp\wubi-9.04-rev128.log
10-05 12:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
10-05 12:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\data
10-05 12:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\bin\7z.exe
10-05 12:08 DEBUG  CommonBackend: Fetching basic info...
10-05 12:08 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-05 12:08 DEBUG  CommonBackend: platform=win32
10-05 12:08 DEBUG  CommonBackend: osname=nt
10-05 12:08 DEBUG  CommonBackend: language=en_US
10-05 12:08 DEBUG  CommonBackend: encoding=cp1252
10-05 12:08 DEBUG  WindowsBackend: arch=amd64
10-05 12:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\data\isolist.ini
10-05 12:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 12:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 12:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 12:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 12:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 12:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 12:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 12:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 12:08 DEBUG  WindowsBackend: Fetching host info...
10-05 12:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 12:08 DEBUG  WindowsBackend: windows version=xp
10-05 12:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 12:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-05 12:08 DEBUG  WindowsBackend: windows_build=2600
10-05 12:08 DEBUG  WindowsBackend: gmt=5
10-05 12:08 DEBUG  WindowsBackend: country=US
10-05 12:08 DEBUG  WindowsBackend: timezone=America/New_York
10-05 12:08 DEBUG  WindowsBackend: windows_username=alex
10-05 12:08 DEBUG  WindowsBackend: user_full_name=alex
10-05 12:08 DEBUG  WindowsBackend: user_directory=alex
10-05 12:08 DEBUG  WindowsBackend: windows_language_code=1033
10-05 12:08 DEBUG  WindowsBackend: windows_language=English
10-05 12:08 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
10-05 12:08 DEBUG  WindowsBackend: bootloader=xp
10-05 12:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7407.4921875 mb free )
10-05 12:08 DEBUG  WindowsBackend: drive=Drive(C: hd 7407.4921875 mb free )
10-05 12:08 DEBUG  WindowsBackend: drive=Drive(D: hd 21753.8203125 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: drive=Drive(E: hd 5383.828125 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: drive=Drive(F: hd 674.5390625 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: drive=Drive(G: hd 18048.46875 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-05 12:08 DEBUG  WindowsBackend: drive=Drive(Z: hd 68.396484375 mb free ntfs)
10-05 12:08 DEBUG  WindowsBackend: uninstaller_path=None
10-05 12:08 DEBUG  WindowsBackend: previous_target_dir=None
10-05 12:08 DEBUG  WindowsBackend: previous_distro_name=None
10-05 12:08 DEBUG  WindowsBackend: keyboard_id=67699721
10-05 12:08 DEBUG  WindowsBackend: keyboard_layout=us
10-05 12:08 DEBUG  WindowsBackend: keyboard_variant=
10-05 12:08 DEBUG  CommonBackend: locale=en_US.UTF-8
10-05 12:08 DEBUG  WindowsBackend: total_memory_mb=503.234375
10-05 12:08 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 12:08 DEBUG  CommonBackend: Searching for local CDs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain C:\DOCUME~1\alex\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-05 12:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-05 12:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-05 12:08 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-05 12:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-05 12:08 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-05 12:08 INFO   root: Running the CD menu...
10-05 12:08 DEBUG  WindowsFrontend: __init__...
10-05 12:08 DEBUG  WindowsFrontend: on_init...
10-05 12:08 INFO   WindowsFrontend: Operation cancelled
10-05 12:08 DEBUG  WindowsFrontend: frontend.quit
10-05 12:08 DEBUG  WindowsFrontend: frontend.on_quit
10-05 12:08 DEBUG  root: application.on_quit
10-05 12:08 INFO   root: sys.exit
```

Edit - please use code tags [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by RichardLinx on 2009-10-08
That is one long error message! Is your D: drive an actual hard drive? Usually D: is allocated to the optical drive, not always though. Most likely your D: drive has nothing on it and isn't even formatted to any sort of file system so Wubi won't install on it. Wubi is meant for installing on Windows (almost like an application) so if you try installing it on a seperate drive while in Windows it's going to fail.

If the D: drive/partition is an actual HDD then you're much better off dual booting if you want to give Ubuntu a go.

---

### Post by blooboy on 2009-10-08
I have 3 partitions on my system. Win XP is the primary OS in my C: drive. Drive D: and E: are for storage purposes. I have seen that WUBI wont install in either D: or E:.

Somebody please quickly go through the error log and guide me.

Thanks in anticipation.

---

### Post by RichardLinx on 2009-10-08
> **blooboy said:**
> I have 3 partitions on my system. Win XP is the primary OS in my C: drive. Drive D: and E: are for storage purposes. I have seen that WUBI wont install in either D: or E:.

Somebody please **quickly** go through the error log and guide me.

Thanks in anticipation.

Lol.

Was this just an Ubuntu CD?
```
10-03 16:04 DEBUG CommonBackend: Adding distro Xubuntu-i386
10-03 16:04 DEBUG CommonBackend: Adding distro Xubuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Kubuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Mythbuntu-i386
10-03 16:04 DEBUG CommonBackend: Adding distro Ubuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Ubuntu-i386
10-03 16:04 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Kubuntu-i386
```
Because it looks like it tried to install four versions of Ubuntu. There are a ton of errors going down the log (I didn't look through the whole thing). I think you have a bad disk.

---

### Post by blooboy on 2009-10-08
> **RichardLinx said:**
> Lol.

Was this just an Ubuntu CD?
```
10-03 16:04 DEBUG CommonBackend: Adding distro Xubuntu-i386
10-03 16:04 DEBUG CommonBackend: Adding distro Xubuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Kubuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Mythbuntu-i386
10-03 16:04 DEBUG CommonBackend: Adding distro Ubuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Ubuntu-i386
10-03 16:04 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
10-03 16:04 DEBUG CommonBackend: Adding distro Kubuntu-i386
```
Because it looks like it tried to install four versions of Ubuntu. There are a ton of errors going down the log (I didn't look through the whole thing). I think you have a bad disk.

This is what amazes me most. I tried to install 9.04 and this error log shows soo many distronames !!! The partition D: works perfectly fine in windows.

---

### Post by nhasian on 2009-10-08
I know its not exactly the answer you were looking for, but since you are already familiar with partitioning a hard disk, why not use one of those, or create a new partition for ubuntu instead of using wubi?

> **blooboy said:**
> I have 3 partitions on my system. Win XP is the primary OS in my C: drive. Drive D: and E: are for storage purposes. I have seen that WUBI wont install in either D: or E:.

Somebody please quickly go through the error log and guide me.

Thanks in anticipation.

---

### Post by blooboy on 2009-10-12
Thanks everybody for your suggestions. I figured out that the installation cd was bad. Created a new cd from the ISO I had.... Now Ubuntu via WUBI is working fine :)

---

