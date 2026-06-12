---
title: "Wubi install error looking for ISO"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by wmfinck on 2009-07-03
I have tried several times to install Ubuntu 9.04 (downloaded from MIT on July 2nd) inside of windows XP, allowing space from 17 up to 30 GB, and it fails continually with the same error message, informing me to check a log file. I will paste in the log file below. It apparently is trying to download an .ISO, and I do not understand why, because I am installing from a CD that I made from the downloaded ISO ! Please Help! I would very much appreciate it, Thank You! Here is the log file:
```
 
07-02 23:29 INFO root: === wubi 9.04 rev128 ===
07-02 23:29 DEBUG root: Logfile is c:\docume~1\linuxpc\locals~1\temp\wubi-9.04-rev128.log
07-02 23:29 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
07-02 23:29 DEBUG CommonBackend: data_dir=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\data
07-02 23:29 DEBUG WindowsBackend: 7z=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\bin\7z.exe
07-02 23:29 DEBUG CommonBackend: Fetching basic info...
07-02 23:29 DEBUG CommonBackend: original_exe=D:\wubi.exe
07-02 23:29 DEBUG CommonBackend: platform=win32
07-02 23:29 DEBUG CommonBackend: osname=nt
07-02 23:29 DEBUG CommonBackend: language=en_US
07-02 23:29 DEBUG CommonBackend: encoding=cp1252
07-02 23:29 DEBUG WindowsBackend: arch=i386
07-02 23:29 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\data\isolist.ini
07-02 23:29 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-02 23:29 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-02 23:29 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-02 23:29 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-02 23:29 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-02 23:29 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-02 23:29 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-02 23:29 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-02 23:29 DEBUG WindowsBackend: Fetching host info...
07-02 23:29 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-02 23:29 DEBUG WindowsBackend: windows version=xp
07-02 23:29 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-02 23:29 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-02 23:29 DEBUG WindowsBackend: windows_build=2600
07-02 23:29 DEBUG WindowsBackend: gmt=-6
07-02 23:29 DEBUG WindowsBackend: country=US
07-02 23:29 DEBUG WindowsBackend: timezone=America/Chicago
07-02 23:29 DEBUG WindowsBackend: windows_username=LinuxPC
07-02 23:29 DEBUG WindowsBackend: user_full_name=LinuxPC
07-02 23:29 DEBUG WindowsBackend: user_directory=LinuxPC
07-02 23:29 DEBUG WindowsBackend: windows_language_code=1033
07-02 23:29 DEBUG WindowsBackend: windows_language=English
07-02 23:29 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.66GHz
07-02 23:29 DEBUG WindowsBackend: bootloader=xp
07-02 23:29 DEBUG WindowsBackend: system_drive=Drive(C: hd 102548.90625 mb free )
07-02 23:29 DEBUG WindowsBackend: drive=Drive(C: hd 102548.90625 mb free )
07-02 23:29 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-02 23:29 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-02 23:29 DEBUG WindowsBackend: uninstaller_path=None
07-02 23:29 DEBUG WindowsBackend: previous_target_dir=None
07-02 23:29 DEBUG WindowsBackend: previous_distro_name=None
07-02 23:29 DEBUG WindowsBackend: keyboard_id=67699721
07-02 23:29 DEBUG WindowsBackend: keyboard_layout=us
07-02 23:29 DEBUG WindowsBackend: keyboard_variant=
07-02 23:29 DEBUG CommonBackend: locale=en_US.UTF-8
07-02 23:29 DEBUG WindowsBackend: total_memory_mb=511.0
07-02 23:29 DEBUG CommonBackend: Searching ISOs on USB devices
07-02 23:29 DEBUG CommonBackend: Searching for local CDs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Ubuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Ubuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Kubuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Kubuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Xubuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Xubuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Mythbuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp is a valid Mythbuntu CD
07-02 23:29 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\casper\filesystem.squashfs
07-02 23:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:29 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-02 23:29 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-02 23:29 DEBUG Distro: wrong arch: i386 != amd64
07-02 23:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:29 INFO Distro: Found a valid CD for Ubuntu: D:\
07-02 23:29 INFO root: Running the CD menu...
07-02 23:29 DEBUG WindowsFrontend: __init__...
07-02 23:29 DEBUG WindowsFrontend: on_init...
07-02 23:29 INFO root: CD menu finished
07-02 23:29 INFO root: Running the installer...
07-02 23:29 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=linuxpc
07-02 23:29 INFO root: Received settings
07-02 23:29 DEBUG TaskList: # Running tasklist...
07-02 23:29 DEBUG TaskList: ## Running select_target_dir...
07-02 23:29 INFO WindowsBackend: Installing into C:\ubuntu
07-02 23:29 DEBUG TaskList: ## Finished select_target_dir
07-02 23:29 DEBUG TaskList: ## Running create_dir_structure...
07-02 23:29 DEBUG CommonBackend: Creating dir C:\ubuntu
07-02 23:29 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
07-02 23:29 DEBUG CommonBackend: Creating dir C:\ubuntu\install
07-02 23:29 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
07-02 23:29 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
07-02 23:29 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-02 23:29 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-02 23:29 DEBUG TaskList: ## Finished create_dir_structure
07-02 23:29 DEBUG TaskList: ## Running uncompress_target_dir...
07-02 23:29 DEBUG TaskList: ## Finished uncompress_target_dir
07-02 23:29 DEBUG TaskList: ## Running create_uninstaller...
07-02 23:29 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-02 23:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-02 23:29 DEBUG TaskList: ## Finished create_uninstaller
07-02 23:29 DEBUG TaskList: ## Running copy_installation_files...
07-02 23:29 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-02 23:29 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\winboot -> C:\ubuntu\winboot
07-02 23:29 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl72.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-02 23:29 DEBUG TaskList: ## Finished copy_installation_files
07-02 23:29 DEBUG TaskList: ## Running get_iso...
07-02 23:29 DEBUG TaskList: New task copy_file
07-02 23:29 DEBUG TaskList: ### Running copy_file...
07-02 23:32 DEBUG TaskList: ### Finished copy_file
07-02 23:32 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
07-02 23:32 DEBUG TaskList: # Cancelling tasklist
07-02 23:32 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
07-02 23:32 DEBUG TaskList: New task check_iso
07-02 23:32 DEBUG CommonBackend: Searching for local ISO
07-02 23:32 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-02 23:32 DEBUG TaskList: New task get_metalink
07-02 23:32 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-02 23:32 DEBUG TaskList: # Cancelling tasklist
07-02 23:32 DEBUG TaskList: # Finished tasklist
07-02 23:33 INFO root: === wubi 9.04 rev128 ===
07-02 23:33 DEBUG root: Logfile is c:\docume~1\linuxpc\locals~1\temp\wubi-9.04-rev128.log
07-02 23:33 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
07-02 23:33 DEBUG CommonBackend: data_dir=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\data
07-02 23:33 DEBUG WindowsBackend: 7z=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\bin\7z.exe
07-02 23:33 DEBUG CommonBackend: Fetching basic info...
07-02 23:33 DEBUG CommonBackend: original_exe=D:\wubi.exe
07-02 23:33 DEBUG CommonBackend: platform=win32
07-02 23:33 DEBUG CommonBackend: osname=nt
07-02 23:33 DEBUG CommonBackend: language=en_US
07-02 23:33 DEBUG CommonBackend: encoding=cp1252
07-02 23:33 DEBUG WindowsBackend: arch=i386
07-02 23:33 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\data\isolist.ini
07-02 23:33 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-02 23:33 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-02 23:33 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-02 23:33 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-02 23:33 DEBUG WindowsBackend: Fetching host info...
07-02 23:33 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-02 23:33 DEBUG WindowsBackend: windows version=xp
07-02 23:33 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-02 23:33 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-02 23:33 DEBUG WindowsBackend: windows_build=2600
07-02 23:33 DEBUG WindowsBackend: gmt=-6
07-02 23:33 DEBUG WindowsBackend: country=US
07-02 23:33 DEBUG WindowsBackend: timezone=America/Chicago
07-02 23:33 DEBUG WindowsBackend: windows_username=LinuxPC
07-02 23:33 DEBUG WindowsBackend: user_full_name=LinuxPC
07-02 23:33 DEBUG WindowsBackend: user_directory=LinuxPC
07-02 23:33 DEBUG WindowsBackend: windows_language_code=1033
07-02 23:33 DEBUG WindowsBackend: windows_language=English
07-02 23:33 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.66GHz
07-02 23:33 DEBUG WindowsBackend: bootloader=xp
07-02 23:33 DEBUG WindowsBackend: system_drive=Drive(C: hd 101851.011719 mb free )
07-02 23:33 DEBUG WindowsBackend: drive=Drive(C: hd 101851.011719 mb free )
07-02 23:33 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-02 23:33 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-02 23:33 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-02 23:33 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
07-02 23:33 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-02 23:33 DEBUG WindowsBackend: keyboard_id=67699721
07-02 23:33 DEBUG WindowsBackend: keyboard_layout=us
07-02 23:33 DEBUG WindowsBackend: keyboard_variant=
07-02 23:33 DEBUG CommonBackend: locale=en_US.UTF-8
07-02 23:33 DEBUG WindowsBackend: total_memory_mb=511.0
07-02 23:33 DEBUG CommonBackend: Searching ISOs on USB devices
07-02 23:33 DEBUG CommonBackend: Searching for local CDs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Ubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Ubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Kubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Kubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Xubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Xubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Mythbuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Mythbuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:33 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-02 23:33 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-02 23:33 DEBUG Distro: wrong arch: i386 != amd64
07-02 23:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:33 INFO Distro: Found a valid CD for Ubuntu: D:\
07-02 23:33 INFO root: Running the CD menu...
07-02 23:33 DEBUG WindowsFrontend: __init__...
07-02 23:33 DEBUG WindowsFrontend: on_init...
07-02 23:33 INFO root: CD menu finished
07-02 23:33 INFO root: Already installed, running the uninstaller...
07-02 23:33 INFO root: Running the uninstaller...
07-02 23:33 INFO CommonBackend: This is the uninstaller running
07-02 23:33 INFO root: Received settings
07-02 23:33 DEBUG TaskList: # Running tasklist...
07-02 23:33 DEBUG TaskList: ## Running Backup ISO...
07-02 23:33 DEBUG TaskList: ## Finished Backup ISO
07-02 23:33 DEBUG TaskList: ## Running Remove bootloader entry...
07-02 23:33 ERROR WindowsBackend: Cannot find bcdedit
07-02 23:33 DEBUG WindowsBackend: undo_bootini C:
07-02 23:33 DEBUG WindowsBackend: undo_configsys Drive(C: hd 101851.011719 mb free )
07-02 23:33 DEBUG TaskList: ## Finished Remove bootloader entry
07-02 23:33 DEBUG TaskList: ## Running Remove target dir...
07-02 23:33 DEBUG CommonBackend: Deleting C:\ubuntu
07-02 23:33 DEBUG TaskList: ## Finished Remove target dir
07-02 23:33 DEBUG TaskList: ## Running Remove registry key...
07-02 23:33 DEBUG TaskList: ## Finished Remove registry key
07-02 23:33 DEBUG TaskList: # Finished tasklist
07-02 23:33 INFO root: Almost finished uninstalling
07-02 23:33 INFO root: Finished uninstallation
07-02 23:33 DEBUG CommonBackend: Fetching basic info...
07-02 23:33 DEBUG CommonBackend: original_exe=D:\wubi.exe
07-02 23:33 DEBUG CommonBackend: platform=win32
07-02 23:33 DEBUG CommonBackend: osname=nt
07-02 23:33 DEBUG CommonBackend: language=en_US
07-02 23:33 DEBUG CommonBackend: encoding=cp1252
07-02 23:33 DEBUG WindowsBackend: arch=i386
07-02 23:33 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\data\isolist.ini
07-02 23:33 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-02 23:33 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-02 23:33 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-02 23:33 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-02 23:33 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-02 23:33 DEBUG WindowsBackend: Fetching host info...
07-02 23:33 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-02 23:33 DEBUG WindowsBackend: windows version=xp
07-02 23:33 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-02 23:33 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-02 23:33 DEBUG WindowsBackend: windows_build=2600
07-02 23:33 DEBUG WindowsBackend: gmt=-6
07-02 23:33 DEBUG WindowsBackend: country=US
07-02 23:33 DEBUG WindowsBackend: timezone=America/Chicago
07-02 23:33 DEBUG WindowsBackend: windows_username=LinuxPC
07-02 23:33 DEBUG WindowsBackend: user_full_name=LinuxPC
07-02 23:33 DEBUG WindowsBackend: user_directory=LinuxPC
07-02 23:33 DEBUG WindowsBackend: windows_language_code=1033
07-02 23:33 DEBUG WindowsBackend: windows_language=English
07-02 23:33 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.66GHz
07-02 23:33 DEBUG WindowsBackend: bootloader=xp
07-02 23:33 DEBUG WindowsBackend: system_drive=Drive(C: hd 102550.847656 mb free )
07-02 23:33 DEBUG WindowsBackend: drive=Drive(C: hd 102550.847656 mb free )
07-02 23:33 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-02 23:33 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-02 23:33 DEBUG WindowsBackend: uninstaller_path=None
07-02 23:33 DEBUG WindowsBackend: previous_target_dir=None
07-02 23:33 DEBUG WindowsBackend: previous_distro_name=None
07-02 23:33 DEBUG WindowsBackend: keyboard_id=67699721
07-02 23:33 DEBUG WindowsBackend: keyboard_layout=us
07-02 23:33 DEBUG WindowsBackend: keyboard_variant=
07-02 23:33 DEBUG CommonBackend: locale=en_US.UTF-8
07-02 23:33 DEBUG WindowsBackend: total_memory_mb=511.0
07-02 23:33 DEBUG CommonBackend: Searching ISOs on USB devices
07-02 23:33 DEBUG CommonBackend: Searching for local CDs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Ubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Ubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Kubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Kubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Xubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Xubuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Mythbuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp is a valid Mythbuntu CD
07-02 23:33 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\casper\filesystem.squashfs
07-02 23:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:33 DEBUG Distro: wrong arch: i386 != amd64
07-02 23:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:33 INFO Distro: Found a valid CD for Ubuntu: D:\
07-02 23:33 INFO root: Running the installer...
07-02 23:33 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=linuxpc
07-02 23:33 INFO root: Received settings
07-02 23:33 DEBUG TaskList: # Running tasklist...
07-02 23:33 DEBUG TaskList: ## Running select_target_dir...
07-02 23:33 INFO WindowsBackend: Installing into C:\ubuntu
07-02 23:33 DEBUG TaskList: ## Finished select_target_dir
07-02 23:33 DEBUG TaskList: ## Running create_dir_structure...
07-02 23:33 DEBUG CommonBackend: Creating dir C:\ubuntu
07-02 23:33 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
07-02 23:33 DEBUG CommonBackend: Creating dir C:\ubuntu\install
07-02 23:33 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
07-02 23:33 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
07-02 23:33 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-02 23:33 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-02 23:33 DEBUG TaskList: ## Finished create_dir_structure
07-02 23:33 DEBUG TaskList: ## Running uncompress_target_dir...
07-02 23:33 DEBUG TaskList: ## Finished uncompress_target_dir
07-02 23:33 DEBUG TaskList: ## Running create_uninstaller...
07-02 23:33 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-02 23:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-02 23:33 DEBUG TaskList: ## Finished create_uninstaller
07-02 23:33 DEBUG TaskList: ## Running copy_installation_files...
07-02 23:33 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-02 23:33 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\winboot -> C:\ubuntu\winboot
07-02 23:33 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl73.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-02 23:33 DEBUG TaskList: ## Finished copy_installation_files
07-02 23:33 DEBUG TaskList: ## Running get_iso...
07-02 23:33 DEBUG TaskList: New task copy_file
07-02 23:33 DEBUG TaskList: ### Running copy_file...
07-02 23:38 DEBUG TaskList: ### Finished copy_file
07-02 23:38 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
07-02 23:38 DEBUG TaskList: # Cancelling tasklist
07-02 23:38 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
07-02 23:38 DEBUG TaskList: New task check_iso
07-02 23:38 DEBUG CommonBackend: Searching for local ISO
07-02 23:38 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-02 23:38 DEBUG TaskList: New task get_metalink
07-02 23:38 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-02 23:38 DEBUG TaskList: # Cancelling tasklist
07-02 23:38 DEBUG TaskList: # Finished tasklist
07-02 23:41 INFO root: === wubi 9.04 rev128 ===
07-02 23:41 DEBUG root: Logfile is c:\docume~1\linuxpc\locals~1\temp\wubi-9.04-rev128.log
07-02 23:41 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-02 23:41 DEBUG CommonBackend: data_dir=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\data
07-02 23:41 DEBUG WindowsBackend: 7z=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\bin\7z.exe
07-02 23:41 DEBUG CommonBackend: Fetching basic info...
07-02 23:41 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-02 23:41 DEBUG CommonBackend: platform=win32
07-02 23:41 DEBUG CommonBackend: osname=nt
07-02 23:41 DEBUG CommonBackend: language=en_US
07-02 23:41 DEBUG CommonBackend: encoding=cp1252
07-02 23:41 DEBUG WindowsBackend: arch=i386
07-02 23:41 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\data\isolist.ini
07-02 23:41 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-02 23:41 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-02 23:41 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-02 23:41 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-02 23:41 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-02 23:41 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-02 23:41 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-02 23:41 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-02 23:41 DEBUG WindowsBackend: Fetching host info...
07-02 23:41 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-02 23:41 DEBUG WindowsBackend: windows version=xp
07-02 23:41 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-02 23:41 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-02 23:41 DEBUG WindowsBackend: windows_build=2600
07-02 23:41 DEBUG WindowsBackend: gmt=-6
07-02 23:41 DEBUG WindowsBackend: country=US
07-02 23:41 DEBUG WindowsBackend: timezone=America/Chicago
07-02 23:41 DEBUG WindowsBackend: windows_username=LinuxPC
07-02 23:41 DEBUG WindowsBackend: user_full_name=LinuxPC
07-02 23:41 DEBUG WindowsBackend: user_directory=LinuxPC
07-02 23:41 DEBUG WindowsBackend: windows_language_code=1033
07-02 23:41 DEBUG WindowsBackend: windows_language=English
07-02 23:41 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.66GHz
07-02 23:41 DEBUG WindowsBackend: bootloader=xp
07-02 23:41 DEBUG WindowsBackend: system_drive=Drive(C: hd 101850.664063 mb free )
07-02 23:41 DEBUG WindowsBackend: drive=Drive(C: hd 101850.664063 mb free )
07-02 23:41 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-02 23:41 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-02 23:41 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-02 23:41 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
07-02 23:41 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-02 23:41 DEBUG WindowsBackend: keyboard_id=67699721
07-02 23:41 DEBUG WindowsBackend: keyboard_layout=us
07-02 23:41 DEBUG WindowsBackend: keyboard_variant=
07-02 23:41 DEBUG CommonBackend: locale=en_US.UTF-8
07-02 23:41 DEBUG WindowsBackend: total_memory_mb=511.0
07-02 23:41 DEBUG CommonBackend: Searching ISOs on USB devices
07-02 23:41 DEBUG CommonBackend: Searching for local CDs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Xubuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Xubuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Mythbuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp is a valid Mythbuntu CD
07-02 23:41 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
07-02 23:41 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:41 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-02 23:41 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-02 23:41 DEBUG Distro: wrong arch: i386 != amd64
07-02 23:41 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-02 23:41 INFO Distro: Found a valid CD for Ubuntu: D:\
07-02 23:41 INFO root: Running the uninstaller...
07-02 23:41 INFO CommonBackend: This is the uninstaller running
07-02 23:41 DEBUG WindowsFrontend: __init__...
07-02 23:41 DEBUG WindowsFrontend: on_init...
07-02 23:41 INFO root: Received settings
07-02 23:41 DEBUG TaskList: # Running tasklist...
07-02 23:41 DEBUG TaskList: ## Running Backup ISO...
07-02 23:41 DEBUG TaskList: ## Finished Backup ISO
07-02 23:41 DEBUG TaskList: ## Running Remove bootloader entry...
07-02 23:41 ERROR WindowsBackend: Cannot find bcdedit
07-02 23:41 DEBUG WindowsBackend: undo_bootini C:
07-02 23:41 DEBUG WindowsBackend: undo_configsys Drive(C: hd 101850.664063 mb free )
07-02 23:41 DEBUG TaskList: ## Finished Remove bootloader entry
07-02 23:41 DEBUG TaskList: ## Running Remove target dir...
07-02 23:41 DEBUG CommonBackend: Deleting C:\ubuntu
07-02 23:41 DEBUG TaskList: ## Finished Remove target dir
07-02 23:41 DEBUG TaskList: ## Running Remove registry key...
07-02 23:41 DEBUG TaskList: ## Finished Remove registry key
07-02 23:41 DEBUG TaskList: # Finished tasklist
07-02 23:41 INFO root: Almost finished uninstalling
07-02 23:41 INFO root: Finished uninstallation
07-02 23:41 DEBUG root: application.quit
07-02 23:41 DEBUG WindowsFrontend: frontend.quit
07-02 23:41 DEBUG WindowsFrontend: frontend.on_quit
07-02 23:41 DEBUG root: application.on_quit
07-02 23:41 INFO root: sys.exit
07-03 07:56 INFO root: === wubi 9.04 rev128 ===
07-03 07:56 DEBUG root: Logfile is c:\docume~1\linuxpc\locals~1\temp\wubi-9.04-rev128.log
07-03 07:56 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
07-03 07:56 DEBUG CommonBackend: data_dir=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\data
07-03 07:56 DEBUG WindowsBackend: 7z=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
07-03 07:56 DEBUG CommonBackend: Fetching basic info...
07-03 07:56 DEBUG CommonBackend: original_exe=D:\wubi.exe
07-03 07:56 DEBUG CommonBackend: platform=win32
07-03 07:56 DEBUG CommonBackend: osname=nt
07-03 07:56 DEBUG CommonBackend: language=en_US
07-03 07:56 DEBUG CommonBackend: encoding=cp1252
07-03 07:56 DEBUG WindowsBackend: arch=i386
07-03 07:56 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
07-03 07:56 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-03 07:56 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-03 07:56 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-03 07:56 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-03 07:56 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-03 07:56 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-03 07:56 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-03 07:56 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-03 07:56 DEBUG WindowsBackend: Fetching host info...
07-03 07:56 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 07:56 DEBUG WindowsBackend: windows version=xp
07-03 07:56 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-03 07:56 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-03 07:56 DEBUG WindowsBackend: windows_build=2600
07-03 07:56 DEBUG WindowsBackend: gmt=-6
07-03 07:56 DEBUG WindowsBackend: country=US
07-03 07:56 DEBUG WindowsBackend: timezone=America/Chicago
07-03 07:56 DEBUG WindowsBackend: windows_username=LinuxPC
07-03 07:56 DEBUG WindowsBackend: user_full_name=LinuxPC
07-03 07:56 DEBUG WindowsBackend: user_directory=LinuxPC
07-03 07:56 DEBUG WindowsBackend: windows_language_code=1033
07-03 07:56 DEBUG WindowsBackend: windows_language=English
07-03 07:56 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.66GHz
07-03 07:56 DEBUG WindowsBackend: bootloader=xp
07-03 07:56 DEBUG WindowsBackend: system_drive=Drive(C: hd 102548.175781 mb free )
07-03 07:56 DEBUG WindowsBackend: drive=Drive(C: hd 102548.175781 mb free )
07-03 07:56 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-03 07:56 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-03 07:56 DEBUG WindowsBackend: uninstaller_path=None
07-03 07:56 DEBUG WindowsBackend: previous_target_dir=None
07-03 07:56 DEBUG WindowsBackend: previous_distro_name=None
07-03 07:56 DEBUG WindowsBackend: keyboard_id=67699721
07-03 07:56 DEBUG WindowsBackend: keyboard_layout=us
07-03 07:56 DEBUG WindowsBackend: keyboard_variant=
07-03 07:56 DEBUG CommonBackend: locale=en_US.UTF-8
07-03 07:56 DEBUG WindowsBackend: total_memory_mb=511.0
07-03 07:56 DEBUG CommonBackend: Searching ISOs on USB devices
07-03 07:56 DEBUG CommonBackend: Searching for local CDs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 07:56 DEBUG Distro: does not contain C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 07:56 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-03 07:56 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-03 07:56 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-03 07:56 DEBUG Distro: wrong arch: i386 != amd64
07-03 07:56 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-03 07:56 INFO Distro: Found a valid CD for Ubuntu: D:\
07-03 07:56 INFO root: Running the CD menu...
07-03 07:56 DEBUG WindowsFrontend: __init__...
07-03 07:56 DEBUG WindowsFrontend: on_init...
07-03 07:56 INFO root: CD menu finished
07-03 07:56 INFO root: Running the installer...
07-03 07:56 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=English, username=linuxpc
07-03 07:56 INFO root: Received settings
07-03 07:56 DEBUG TaskList: # Running tasklist...
07-03 07:56 DEBUG TaskList: ## Running select_target_dir...
07-03 07:56 INFO WindowsBackend: Installing into C:\ubuntu
07-03 07:56 DEBUG TaskList: ## Finished select_target_dir
07-03 07:56 DEBUG TaskList: ## Running create_dir_structure...
07-03 07:56 DEBUG CommonBackend: Creating dir C:\ubuntu
07-03 07:56 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
07-03 07:56 DEBUG CommonBackend: Creating dir C:\ubuntu\install
07-03 07:56 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
07-03 07:56 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
07-03 07:56 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-03 07:56 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-03 07:56 DEBUG TaskList: ## Finished create_dir_structure
07-03 07:56 DEBUG TaskList: ## Running uncompress_target_dir...
07-03 07:56 DEBUG TaskList: ## Finished uncompress_target_dir
07-03 07:56 DEBUG TaskList: ## Running create_uninstaller...
07-03 07:56 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 07:56 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 07:56 DEBUG TaskList: ## Finished create_uninstaller
07-03 07:56 DEBUG TaskList: ## Running copy_installation_files...
07-03 07:56 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-03 07:56 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\winboot -> C:\ubuntu\winboot
07-03 07:56 DEBUG WindowsBackend: Copying C:\DOCUME~1\LinuxPC\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-03 07:56 DEBUG TaskList: ## Finished copy_installation_files
07-03 07:56 DEBUG TaskList: ## Running get_iso...
07-03 07:56 DEBUG TaskList: New task copy_file
07-03 07:56 DEBUG TaskList: ### Running copy_file...
07-03 07:59 DEBUG TaskList: ### Finished copy_file
07-03 07:59 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
07-03 07:59 DEBUG TaskList: # Cancelling tasklist
07-03 07:59 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
07-03 07:59 DEBUG TaskList: New task check_iso
07-03 07:59 DEBUG CommonBackend: Searching for local ISO
07-03 07:59 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-03 07:59 DEBUG TaskList: New task get_metalink
07-03 07:59 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 07:59 DEBUG TaskList: # Cancelling tasklist
07-03 07:59 DEBUG TaskList: # Finished tasklist
```

---

### Post by philinux on 2009-07-03
When i installed wubi on a friends lappy I let it download the iso.

However the faq's on the wubi site explain the install that you are attempting with a mention of corrupted iso etc.

[http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)
Scroll down the page.

---

