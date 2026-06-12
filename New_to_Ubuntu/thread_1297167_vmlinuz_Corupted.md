---
title: "vmlinuz Corupted"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by mtariqniaz on 2009-10-21
Hello
when i install ubuntu 9.04 on my systen its gave an error after intaltion that give blow
 
"[IMG]http://tariqniaz.com/error.jpg[/IMG]
 
and the log file is 
 
```
11-19 15:11 INFO root: === wubi 9.04 rev128 ===
11-19 15:11 DEBUG root: Logfile is c:\docume~1\admin\locals~1\temp\wubi-9.04-rev128.log
11-19 15:11 DEBUG root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
11-19 15:11 DEBUG CommonBackend: data_dir=C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\data
11-19 15:11 DEBUG WindowsBackend: 7z=C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\bin\7z.exe
11-19 15:11 DEBUG CommonBackend: Fetching basic info...
11-19 15:11 DEBUG CommonBackend: original_exe=G:\wubi.exe
11-19 15:11 DEBUG CommonBackend: platform=win32
11-19 15:11 DEBUG CommonBackend: osname=nt
11-19 15:11 DEBUG CommonBackend: language=en_US
11-19 15:11 DEBUG CommonBackend: encoding=cp1252
11-19 15:11 DEBUG WindowsBackend: arch=amd64
11-19 15:11 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\data\isolist.ini
11-19 15:11 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-19 15:11 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-19 15:11 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-19 15:11 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-19 15:11 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-19 15:11 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-19 15:11 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-19 15:11 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-19 15:11 DEBUG WindowsBackend: Fetching host info...
11-19 15:11 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-19 15:11 DEBUG WindowsBackend: windows version=xp
11-19 15:11 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-19 15:11 DEBUG WindowsBackend: windows_sp=Service Pack 2
11-19 15:11 DEBUG WindowsBackend: windows_build=2600
11-19 15:11 DEBUG WindowsBackend: gmt=5
11-19 15:11 DEBUG WindowsBackend: country=US
11-19 15:11 DEBUG WindowsBackend: timezone=America/New_York
11-19 15:11 DEBUG WindowsBackend: windows_username=admin
11-19 15:11 DEBUG WindowsBackend: user_full_name=admin
11-19 15:11 DEBUG WindowsBackend: user_directory=admin
11-19 15:11 DEBUG WindowsBackend: windows_language_code=1033
11-19 15:11 DEBUG WindowsBackend: windows_language=English
11-19 15:11 DEBUG WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-56
11-19 15:11 DEBUG WindowsBackend: bootloader=xp
11-19 15:11 DEBUG WindowsBackend: system_drive=Drive(C: hd 32870.9375 mb free )
11-19 15:11 DEBUG WindowsBackend: drive=Drive(C: hd 32870.9375 mb free )
11-19 15:11 DEBUG WindowsBackend: drive=Drive(D: hd 19992.96875 mb free fat32)
11-19 15:11 DEBUG WindowsBackend: drive=Drive(E: hd 22399.5390625 mb free ntfs)
11-19 15:11 DEBUG WindowsBackend: drive=Drive(F: hd 18003.4375 mb free ntfs)
11-19 15:11 DEBUG WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-19 15:11 DEBUG WindowsBackend: uninstaller_path=None
11-19 15:11 DEBUG WindowsBackend: previous_target_dir=None
11-19 15:11 DEBUG WindowsBackend: previous_distro_name=None
11-19 15:11 DEBUG WindowsBackend: keyboard_id=67699721
11-19 15:11 DEBUG WindowsBackend: keyboard_layout=us
11-19 15:11 DEBUG WindowsBackend: keyboard_variant=
11-19 15:11 DEBUG CommonBackend: locale=en_US.UTF-8
11-19 15:11 DEBUG WindowsBackend: total_memory_mb=2047.99999905
11-19 15:11 DEBUG CommonBackend: Searching ISOs on USB devices
11-19 15:11 DEBUG CommonBackend: Searching for local CDs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
11-19 15:11 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:11 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
11-19 15:11 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
11-19 15:11 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
11-19 15:11 INFO Distro: Found a valid CD for Ubuntu: G:\
11-19 15:11 INFO root: Running the CD menu...
11-19 15:11 DEBUG WindowsFrontend: __init__...
11-19 15:11 DEBUG WindowsFrontend: on_init...
11-19 15:11 INFO root: CD menu finished
11-19 15:11 INFO root: Running the installer...
11-19 15:12 INFO WindowsFrontend: Operation cancelled
11-19 15:12 DEBUG WindowsFrontend: frontend.quit
11-19 15:12 DEBUG WindowsFrontend: frontend.on_quit
11-19 15:12 DEBUG root: application.on_quit
11-19 15:12 INFO root: sys.exit
11-19 15:12 INFO root: === wubi 9.04 rev128 ===
11-19 15:12 DEBUG root: Logfile is c:\docume~1\admin\locals~1\temp\wubi-9.04-rev128.log
11-19 15:12 DEBUG root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
11-19 15:12 DEBUG CommonBackend: data_dir=C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\data
11-19 15:12 DEBUG WindowsBackend: 7z=C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\bin\7z.exe
11-19 15:12 DEBUG CommonBackend: Fetching basic info...
11-19 15:12 DEBUG CommonBackend: original_exe=G:\wubi.exe
11-19 15:12 DEBUG CommonBackend: platform=win32
11-19 15:12 DEBUG CommonBackend: osname=nt
11-19 15:12 DEBUG CommonBackend: language=en_US
11-19 15:12 DEBUG CommonBackend: encoding=cp1252
11-19 15:12 DEBUG WindowsBackend: arch=amd64
11-19 15:12 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\data\isolist.ini
11-19 15:12 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-19 15:12 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-19 15:12 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-19 15:12 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-19 15:12 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-19 15:12 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-19 15:12 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-19 15:12 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-19 15:12 DEBUG WindowsBackend: Fetching host info...
11-19 15:12 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-19 15:12 DEBUG WindowsBackend: windows version=xp
11-19 15:12 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-19 15:12 DEBUG WindowsBackend: windows_sp=Service Pack 2
11-19 15:12 DEBUG WindowsBackend: windows_build=2600
11-19 15:12 DEBUG WindowsBackend: gmt=5
11-19 15:12 DEBUG WindowsBackend: country=US
11-19 15:12 DEBUG WindowsBackend: timezone=America/New_York
11-19 15:12 DEBUG WindowsBackend: windows_username=admin
11-19 15:12 DEBUG WindowsBackend: user_full_name=admin
11-19 15:12 DEBUG WindowsBackend: user_directory=admin
11-19 15:12 DEBUG WindowsBackend: windows_language_code=1033
11-19 15:12 DEBUG WindowsBackend: windows_language=English
11-19 15:12 DEBUG WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-56
11-19 15:12 DEBUG WindowsBackend: bootloader=xp
11-19 15:12 DEBUG WindowsBackend: system_drive=Drive(C: hd 32870.8125 mb free )
11-19 15:12 DEBUG WindowsBackend: drive=Drive(C: hd 32870.8125 mb free )
11-19 15:12 DEBUG WindowsBackend: drive=Drive(D: hd 19992.96875 mb free fat32)
11-19 15:12 DEBUG WindowsBackend: drive=Drive(E: hd 22399.5390625 mb free ntfs)
11-19 15:12 DEBUG WindowsBackend: drive=Drive(F: hd 18003.4375 mb free ntfs)
11-19 15:12 DEBUG WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-19 15:12 DEBUG WindowsBackend: uninstaller_path=None
11-19 15:12 DEBUG WindowsBackend: previous_target_dir=None
11-19 15:12 DEBUG WindowsBackend: previous_distro_name=None
11-19 15:12 DEBUG WindowsBackend: keyboard_id=67699721
11-19 15:12 DEBUG WindowsBackend: keyboard_layout=us
11-19 15:12 DEBUG WindowsBackend: keyboard_variant=
11-19 15:12 DEBUG CommonBackend: locale=en_US.UTF-8
11-19 15:12 DEBUG WindowsBackend: total_memory_mb=2047.99999905
11-19 15:12 DEBUG CommonBackend: Searching ISOs on USB devices
11-19 15:12 DEBUG CommonBackend: Searching for local CDs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
11-19 15:12 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
11-19 15:12 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
11-19 15:12 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
11-19 15:12 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
11-19 15:12 INFO Distro: Found a valid CD for Ubuntu: G:\
11-19 15:12 INFO root: Running the CD menu...
11-19 15:12 DEBUG WindowsFrontend: __init__...
11-19 15:12 DEBUG WindowsFrontend: on_init...
11-19 15:12 INFO root: CD menu finished
11-19 15:12 INFO root: Running the installer...
11-19 15:12 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=19000MB, distro_name=Ubuntu, language=English, username=ultimate
11-19 15:12 INFO root: Received settings
11-19 15:12 DEBUG TaskList: # Running tasklist...
11-19 15:12 DEBUG TaskList: ## Running select_target_dir...
11-19 15:12 INFO WindowsBackend: Installing into D:\ubuntu
11-19 15:12 DEBUG TaskList: ## Finished select_target_dir
11-19 15:12 DEBUG TaskList: ## Running create_dir_structure...
11-19 15:12 DEBUG CommonBackend: Creating dir D:\ubuntu
11-19 15:12 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
11-19 15:12 DEBUG CommonBackend: Creating dir D:\ubuntu\install
11-19 15:12 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
11-19 15:12 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
11-19 15:12 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-19 15:12 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-19 15:12 DEBUG TaskList: ## Finished create_dir_structure
11-19 15:12 DEBUG TaskList: ## Running uncompress_target_dir...
11-19 15:12 ERROR WindowsBackend: Error executing command
>>command=compact D:\ubuntu /U /A /F
>>retval=1
>>stderr=
Uncompressing files in D:\
 
ubuntu [ERR]
ubuntu: The file system does not support compression.
 
0 files within 1 directories were uncompressed.
 
 
>>stdout=
11-19 15:12 DEBUG TaskList: ## Finished uncompress_target_dir
11-19 15:12 DEBUG TaskList: ## Running create_uninstaller...
11-19 15:12 DEBUG WindowsBackend: Copying uninstaller G:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-19 15:12 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-19 15:12 DEBUG TaskList: ## Finished create_uninstaller
11-19 15:12 DEBUG TaskList: ## Running copy_installation_files...
11-19 15:12 DEBUG WindowsBackend: Copying C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-19 15:12 DEBUG WindowsBackend: Copying C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\winboot -> D:\ubuntu\winboot
11-19 15:12 DEBUG WindowsBackend: Copying C:\DOCUME~1\admin\LOCALS~1\Temp\pyl12.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-19 15:12 DEBUG TaskList: ## Finished copy_installation_files
11-19 15:12 DEBUG TaskList: ## Running get_iso...
11-19 15:12 DEBUG TaskList: New task copy_file
11-19 15:12 DEBUG TaskList: ### Running copy_file...
11-19 15:17 DEBUG TaskList: ### Finished copy_file
11-19 15:17 DEBUG TaskList: New task check_iso
11-19 15:17 DEBUG TaskList: ### Running check_iso...
11-19 15:17 DEBUG CommonBackend: Checking D:\ubuntu\install\installation.iso
11-19 15:17 DEBUG WindowsBackend: extracting .disk\info from D:\ubuntu\install\installation.iso
11-19 15:17 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
11-19 15:17 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
11-19 15:17 DEBUG CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
11-19 15:17 DEBUG TaskList: New task get_metalink
11-19 15:17 DEBUG TaskList: #### Running get_metalink...
11-19 15:17 DEBUG downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > D:\ubuntu\install
11-19 15:17 ERROR CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
11-19 15:17 DEBUG downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) > D:\ubuntu\install
11-19 15:17 ERROR CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
11-19 15:17 DEBUG TaskList: #### Finished get_metalink
11-19 15:17 ERROR CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu\install\installation.iso, ignoring
11-19 15:17 DEBUG TaskList: ### Finished check_iso
11-19 15:17 DEBUG TaskList: ## Finished get_iso
11-19 15:17 DEBUG TaskList: ## Running extract_kernel...
11-19 15:17 DEBUG CommonBackend: Copying files from CD G:\
11-19 15:17 DEBUG CommonBackend: Checking kernel, initrd and md5sums
11-19 15:17 DEBUG CommonBackend: checking D:\ubuntu\install\boot\vmlinuz
11-19 15:17 DEBUG CommonBackend: D:\ubuntu\install\boot\vmlinuz md5 = 54504771f055ef163da244f84729efd5 != da3a16e8bd2392c4eabf52d8fc22e947
11-19 15:17 ERROR TaskList: File D:\ubuntu\install\boot\vmlinuz is corrupted
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 516, in extract_kernel
Exception: File D:\ubuntu\install\boot\vmlinuz is corrupted
11-19 15:17 DEBUG TaskList: # Cancelling tasklist
11-19 15:17 DEBUG TaskList: # Finished tasklist
11-19 15:17 ERROR root: File D:\ubuntu\install\boot\vmlinuz is corrupted
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: File D:\ubuntu\install\boot\vmlinuz is corrupted
""
 
 
and my system config is 
 
------------------
System Information
------------------
Time of this report: 11/19/2009, 23:06:29
Machine name: HOSTING
Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_rtm.040803-2158)
Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
System Model: HP Pavilion dv6000 (GA451UA#ABA) 
BIOS: PhoenixBIOS 4.0 Release 6.1 
Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-56, MMX, 3DNow (2 CPUs), ~1.8GHz
Memory: 2494MB RAM
Page File: 278MB used, 3404MB available
Windows Dir: C:\WINDOWS
DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
DxDiag Version: 5.03.2600.2180 32bit Unicode
------------
DxDiag Notes
------------
DirectX Files Tab: No problems found.
Display Tab 1: No problems found.
Sound Tab 1: No problems found.
Music Tab: No problems found.
Input Tab: No problems found.
Network Tab: No problems found.
--------------------
DirectX Debug Levels
--------------------
Direct3D: 0/4 (n/a)
DirectDraw: 0/4 (retail)
DirectInput: 0/5 (n/a)
DirectMusic: 0/5 (n/a)
DirectPlay: 0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow: 0/6 (retail)
---------------
Display Devices
---------------
Card name: NVIDIA GeForce Go 6150
Manufacturer: NVIDIA
Chip type: GeForce Go 6150
DAC type: Integrated RAMDAC
Device Key: Enum\PCI\VEN_10DE&DEV_0244&SUBSYS_30B7103C&REV_A2
Display Memory: 256.0 MB
Current Mode: 1280 x 800 (32 bit) (60Hz)
Monitor: Default Monitor
Monitor Max Res: 
Driver Name: nv4_disp.dll
Driver Version: 6.14.0010.8602 (English)
DDI Version: 9 (or higher)
Driver Attributes: Final Retail
Driver Date/Size: 7/20/2006 20:58:00, 3989504 bytes
WHQL Logo'd: Yes
WHQL Date Stamp: n/a
VDD: n/a
Mini VDD: nv4_mini.sys
Mini VDD Date: 7/20/2006 20:58:00, 3685152 bytes
Device Identifier: {D7B71E3E-4104-11CF-1652-BD1003C2CB35}
Vendor ID: 0x10DE
Device ID: 0x0244
SubSys ID: 0x30B7103C
Revision ID: 0x00A2
Revision ID: 0x00A2
Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D ModeWMV9_B ModeWMV9_A 
Deinterlace Caps: {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
{335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
{212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
{335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
{212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
{335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
{212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
{335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
Registry: OK
DDraw Status: Enabled
D3D Status: Enabled
AGP Status: Enabled
DDraw Test Result: Not run
D3D7 Test Result: Not run
D3D8 Test Result: Not run
D3D9 Test Result: Not run
-------------
Sound Devices
-------------
Description: Conexant HD Audio output
Default Sound Playback: Yes
Default Voice Playback: Yes
Hardware ID: HDAUDIO\FUNC_01&VEN_14F1&DEV_5045&SUBSYS_103C30B7&REV_1001
Manufacturer ID: 1
Product ID: 100
Type: WDM
Driver Name: CHDAud.sys
Driver Version: 3.26.0000.0000 (English)
Driver Attributes: Final Retail
WHQL Logo'd: Yes
Date and Size: 7/28/2006 03:44:42, 581632 bytes
Other Files: 
Driver Provider: Conexant
HW Accel Level: Full
Cap Flags: 0xB5B
Min/Max Sample Rate: 8000, 192000
Static/Strm HW Mix Bufs: 13, 12
Static/Strm HW 3D Bufs: 0, 0
HW Memory: 0
Voice Management: No
EAX(tm) 2.0 Listen/Src: No, No
I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No
Registry: OK
Sound Test Result: Not run
---------------------
Sound Capture Devices
---------------------
Description: Conexant HD Audio input
Default Sound Capture: Yes
Default Voice Capture: Yes
Driver Name: CHDAud.sys
Driver Version: 3.26.0000.0000 (English)
Driver Attributes: Final Retail
Date and Size: 7/28/2006 03:44:42, 581632 bytes
Cap Flags: 0x41
Format Flags: 0xCCC
-----------
DirectMusic
-----------
DLS Path: C:\WINDOWS\SYSTEM32\drivers\GM.DLS
DLS Version: 1.00.0016.0002
Acceleration: n/a
Ports: Microsoft Synthesizer, Software (Not Kernel Mode), Output, DLS, Internal, Default Port
Microsoft MIDI Mapper [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
Microsoft GS Wavetable SW Synth [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
Registry: OK
Test Result: Not run
-------------------
DirectInput Devices
-------------------
Device Name: Mouse
Attached: 1
Controller ID: n/a
Vendor/Product ID: n/a
FF Driver: n/a
Device Name: Keyboard
Attached: 1
Controller ID: n/a
Vendor/Product ID: n/a
FF Driver: n/a
Poll w/ Interrupt: No
Registry: OK
-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x10DE, 0x026D
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 8/4/2004 04:05:44, 57600 bytes
| Driver: usbd.sys, 8/23/2001 16:00:00, 4736 bytes
----------------
Gameport Devices
----------------
------------
PS/2 Devices
------------
+ Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| Driver: i8042prt.sys, 8/4/2004 04:05:44, 52736 bytes
| Driver: kbdclass.sys, 8/4/2004 04:05:44, 24576 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 01:01:08, 40840 bytes
| Driver: kbdclass.sys, 8/4/2004 04:05:44, 24576 bytes
| 
+ PS/2 Compatible Mouse
| Matching Device ID: *pnp0f13
| Service: i8042prt
| Driver: i8042prt.sys, 8/4/2004 04:05:44, 52736 bytes
| Driver: mouclass.sys, 8/4/2004 04:05:44, 23040 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 01:01:08, 40840 bytes
| Driver: mouclass.sys, 8/4/2004 04:05:44, 23040 bytes
----------------------------
DirectPlay Service Providers
----------------------------
DirectPlay8 Modem Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 Serial Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 IPX Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 TCP/IP Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
Internet TCP/IP Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
IPX Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
Modem Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)
Serial Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)
DirectPlay Voice Wizard Tests: Full Duplex: Not run, Half Duplex: Not run, Mic: Not run
DirectPlay Test Result: Not run
Registry: OK
-------------------
DirectPlay Adapters
-------------------
DirectPlay8 Modem Service Provider: HDAUDIO Soft Data Fax Modem with SmartCP
DirectPlay8 Serial Service Provider: COM3
DirectPlay8 TCP/IP Service Provider: Network Bridge - IPv4 - 
-----------------------
DirectPlay Voice Codecs
-----------------------
Voxware VR12 1.4kbit/s
Voxware SC06 6.4kbit/s
Voxware SC03 3.2kbit/s
MS-PCM 64 kbit/s
MS-ADPCM 32.8 kbit/s
Microsoft GSM 6.10 13 kbit/s
TrueSpeech(TM) 8.6 kbit/s
-------------------------
DirectPlay Lobbyable Apps
-------------------------
------------------------
Disk & DVD/CD-ROM Drives
------------------------
Drive: C:
Free Space: 33.1 GB
Total Space: 40.0 GB
File System: FAT32
Model: WDC WD1600BEVS-60RST0
Drive: D:
Free Space: 20.0 GB
Total Space: 20.0 GB
File System: FAT32
Model: WDC WD1600BEVS-60RST0
Drive: E:
Free Space: 22.3 GB
Total Space: 50.0 GB
File System: NTFS
Model: WDC WD1600BEVS-60RST0
Drive: F:
Free Space: 18.0 GB
Total Space: 42.6 GB
File System: NTFS
Model: WDC WD1600BEVS-60RST0
Drive: G:
Model: HL-DT-ST DVDRAM GSA-T10N
Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 49536 bytes
--------------
System Devices
--------------
Name: Broadcom 802.11b/g WLAN
Device ID: PCI\VEN_14E4&DEV_4311&SUBSYS_1363103C&REV_01\4&14C5F9B7&0&0018
Driver: n/a
Name: Ricoh xD-Picture Card Host Controller
Device ID: PCI\VEN_1180&DEV_0852&SUBSYS_30B7103C&REV_05\4&3A3249AB&0&2C80
Driver: C:\WINDOWS\system32\DRIVERS\rixdptsk.sys, 1.00.0002.0008 (Japanese), 11/1/2005 18:08:00, 308992 bytes
Driver: C:\WINDOWS\system32\rixdicon.dll, 5/6/2005 18:06:32, 16480 bytes
Name: Ricoh MMC Host Controller
Device ID: PCI\VEN_1180&DEV_0843&SUBSYS_30B7103C&REV_01\4&3A3249AB&0&2A80
Driver: C:\WINDOWS\system32\DRIVERS\rimmptsk.sys, 1.00.0000.0009 (Japanese), 11/16/2005 20:28:32, 28928 bytes
Name: OHCI Compliant IEEE 1394 Host Controller
Device ID: PCI\VEN_1180&DEV_0832&SUBSYS_30B7103C&REV_00\4&3A3249AB&0&2880
Driver: C:\WINDOWS\system32\DRIVERS\ohci1394.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 61056 bytes
Driver: C:\WINDOWS\system32\DRIVERS\1394bus.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 53248 bytes
Driver: C:\WINDOWS\system32\DRIVERS\nic1394.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 61824 bytes
Driver: C:\WINDOWS\system32\DRIVERS\arp1394.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 60800 bytes
Driver: C:\WINDOWS\system32\DRIVERS\enum1394.sys, 5.01.2600.0000 (English), 8/17/2001 13:46:40, 6400 bytes
Name: SDA Standard Compliant SD Host Controller
Device ID: PCI\VEN_1180&DEV_0822&SUBSYS_30B7103C&REV_19\4&3A3249AB&0&2980
Driver: C:\WINDOWS\system32\DRIVERS\sdbus.sys, 6.00.4069.0001 (English), 8/4/2004 04:05:44, 67584 bytes
Name: Ricoh Memory Stick Host Controller
Device ID: PCI\VEN_1180&DEV_0592&SUBSYS_30B7103C&REV_0A\4&3A3249AB&0&2B80
Driver: C:\WINDOWS\system32\snymsico.dll, 1.00.0000.9120 (English), 9/3/2004 12:00:00, 90112 bytes
Driver: C:\WINDOWS\system32\DRIVERS\rimsptsk.sys, 1.00.0002.0004 (Japanese), 11/1/2005 17:54:50, 51584 bytes
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_02FF&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&05
Driver: n/a
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_02FE&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&02
Driver: n/a
Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_02FD&SUBSYS_00000000&REV_A1\3&13C0B0C5&0&18
Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 68224 bytes
Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_02FC&SUBSYS_00000000&REV_A1\3&13C0B0C5&0&10
Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 68224 bytes
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_02FA&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&01
Driver: n/a
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_02F9&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&04
Driver: n/a
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_02F8&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&03
Driver: n/a
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_02F0&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&00
Driver: n/a
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_027F&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&06
Driver: n/a
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_027E&SUBSYS_00000000&REV_A2\3&13C0B0C5&0&07
Driver: n/a
Name: NVIDIA nForce System Management Controller
Device ID: PCI\VEN_10DE&DEV_0271&SUBSYS_30B7103C&REV_A3\3&13C0B0C5&0&53
Driver: C:\WINDOWS\system32\DRIVERS\nvsmu.sys, 5.00.0000.0000 (English), 3/5/2006 23:49:36, 11136 bytes
Name: PCI standard RAM Controller
Device ID: PCI\VEN_10DE&DEV_0270&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&48
Driver: n/a
Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_026F&SUBSYS_00000000&REV_A2\3&13C0B0C5&0&80
Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 68224 bytes
Name: Standard Enhanced PCI to USB Host Controller
Device ID: PCI\VEN_10DE&DEV_026E&SUBSYS_30B7103C&REV_A3\3&13C0B0C5&0&59
Driver: C:\WINDOWS\system32\drivers\usbehci.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 26624 bytes
Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 142976 bytes
Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/4/2004 00:56:48, 74240 bytes
Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 57600 bytes
Driver: C:\WINDOWS\system32\hccoin.dll, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 7168 bytes
Name: Standard OpenHCD USB Host Controller
Device ID: PCI\VEN_10DE&DEV_026D&SUBSYS_30B7103C&REV_A3\3&13C0B0C5&0&58
Driver: C:\WINDOWS\system32\drivers\usbohci.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 17024 bytes
Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 142976 bytes
Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/4/2004 00:56:48, 74240 bytes
Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 57600 bytes
Name: Microsoft UAA Bus Driver for High Definition Audio
Device ID: PCI\VEN_10DE&DEV_026C&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&81
Driver: C:\WINDOWS\system32\DRIVERS\hdaudbus.sys, 5.10.0001.5013 (English), 1/7/2005 17:07:18, 138752 bytes
Name: NVIDIA Network Bus Enumerator
Device ID: PCI\VEN_10DE&DEV_0269&SUBSYS_30B7103C&REV_A3\3&13C0B0C5&0&A0
Driver: C:\WINDOWS\system32\DRIVERS\nvnetbus.sys, 1.00.0000.5024 (English), 3/3/2006 00:31:04, 13056 bytes
Driver: C:\WINDOWS\system32\DRIVERS\nvnrm.sys, 1.00.0002.5024 (English), 3/3/2006 00:30:46, 305024 bytes
Driver: C:\WINDOWS\system32\DRIVERS\nvsnpu.sys, 1.00.0000.5024 (English), 3/3/2006 00:30:32, 222592 bytes
Driver: C:\WINDOWS\system32\bdco1.dll, 1.00.0000.0000 (English), 3/3/2006 00:29:26, 9728 bytes
Driver: C:\WINDOWS\system32\bdco1ins.dll, 1.00.0000.0000 (English), 3/3/2006 00:29:26, 9728 bytes
Driver: C:\WINDOWS\system32\nvconrm.dll, 1.00.0000.0035 (English), 2/22/2006 02:00:24, 35840 bytes
Name: NVIDIA nForce 430/410 Serial ATA Controller
Device ID: PCI\VEN_10DE&DEV_0266&SUBSYS_30B7103C&REV_F1\3&13C0B0C5&0&70
Driver: C:\WINDOWS\system32\DRIVERS\nvata.sys, 5.10.2600.0650 (English), 1/27/2006 00:04:16, 99584 bytes
Driver: C:\WINDOWS\system32\idecoi.dll, 1.00.0000.0001 (English), 1/27/2006 00:04:18, 290304 bytes
Driver: C:\WINDOWS\system32\idecoiins.dll, 1.00.0000.0001 (English), 1/27/2006 00:04:18, 290304 bytes
Driver: C:\WINDOWS\system32\NVCOI.DLL, 1.00.0000.0035 (English), 1/22/2006 21:48:58, 35840 bytes
Name: Standard Dual Channel PCI IDE Controller
Device ID: PCI\VEN_10DE&DEV_0265&SUBSYS_30B7103C&REV_F1\3&13C0B0C5&0&68
Driver: C:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 25088 bytes
Driver: C:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.2180 (English), 8/4/2004 04:05:44, 95360 bytes
Driver: C:\WINDOWS\system32\DRIVERS\pciide.sys, 5.01.2600.0000 (English), 8/23/2001 16:00:00, 3328 bytes
Name: NVIDIA nForce PCI System Management
Device ID: PCI\VEN_10DE&DEV_0264&SUBSYS_30B7103C&REV_A3\3&13C0B0C5&0&51
Driver: n/a
Name: PCI standard ISA bridge
Device ID: PCI\VEN_10DE&DEV_0260&SUBSYS_00000000&REV_A3\3&13C0B0C5&0&50
Driver: C:\WINDOWS\system32\DRIVERS\isapnp.sys, 5.01.2600.0000 (English), 8/23/2001 16:00:00, 35840 bytes
Name: NVIDIA GeForce Go 6150
Device ID: PCI\VEN_10DE&DEV_0244&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&0&28
Driver: C:\WINDOWS\system32\DRIVERS\nv4_mini.sys, 6.14.0010.8602 (English), 7/20/2006 20:58:00, 3685152 bytes
Driver: C:\WINDOWS\system32\nv4_disp.dll, 6.14.0010.8602 (English), 7/20/2006 20:58:00, 3989504 bytes
Driver: C:\WINDOWS\system32\nvsvc32.exe, 6.14.0010.8602 (English), 7/20/2006 20:58:00, 143426 bytes
Driver: C:\WINDOWS\system32\nvapi.dll, 6.14.0010.8602 (), 7/20/2006 20:58:00, 98304 bytes
Driver: C:\WINDOWS\system32\nvoglnt.dll, 6.14.0010.8602 (English), 7/20/2006 20:58:00, 5419008 bytes
Driver: C:\WINDOWS\system32\nvcpl.dll, 6.14.0010.8602 (English), 7/20/2006 20:58:00, 7581696 bytes
Driver: C:\WINDOWS\system32\nvmctray.dll, 6.14.0010.8602 (English), 7/20/2006 20:58:00, 86016 bytes
Driver: C:\WINDOWS\system32\nvwddi.dll, 6.14.0010.8602 (English), 7/20/2006 20:58:00, 81920 bytes
Driver: C:\WINDOWS\help\nvcpl.hlp, 7/20/2006 20:58:00, 171072 bytes
Driver: C:\WINDOWS\help\nvwcplen.hlp, 7/20/2006 20:58:00, 55444 bytes
Driver: C:\WINDOWS\system32\nvcod.dll, 1.00.0000.0035 (English), 7/20/2006 20:58:00, 35840 bytes
Driver: C:\WINDOWS\system32\nvcodins.dll, 1.00.0000.0035 (English), 7/20/2006 20:58:00, 35840 bytes
Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1103&SUBSYS_00000000&REV_00\3&13C0B0C5&0&C3
Driver: n/a
Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1102&SUBSYS_00000000&REV_00\3&13C0B0C5&0&C2
Driver: n/a
Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1101&SUBSYS_00000000&REV_00\3&13C0B0C5&0&C1
Driver: n/a
Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1100&SUBSYS_00000000&REV_00\3&13C0B0C5&0&C0
Driver: n/a
------------------
DirectX Components
------------------
ddraw.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 266240 bytes
ddrawex.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 27136 bytes
dxapi.sys: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 10496 bytes
d3d8.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:42 1179648 bytes
d3d8thk.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:42 8192 bytes
d3d9.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:42 1689088 bytes
d3dim.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 436224 bytes
d3dim700.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:42 825344 bytes
d3dramp.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 590336 bytes
d3drm.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 350208 bytes
d3dxof.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 47616 bytes
d3dpmesh.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 34816 bytes
dplay.dll: 5.00.2134.0001 English Final Retail 8/23/2001 16:00:00 33040 bytes
dplayx.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 229888 bytes
dpmodemx.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 23552 bytes
dpwsock.dll: 5.00.2134.0001 English Final Retail 8/23/2001 16:00:00 42768 bytes
dpwsockx.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 57344 bytes
dplaysvr.exe: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:50 30208 bytes
dpnsvr.exe: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:50 18432 bytes
dpnet.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 375296 bytes
dpnlobby.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:04 3584 bytes
dpnaddr.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:04 3584 bytes
dpvoice.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 212480 bytes
dpvsetup.exe: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:50 83456 bytes
dpvvox.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 116736 bytes
dpvacm.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 21504 bytes
dpnhpast.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 35328 bytes
dpnhupnp.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 60928 bytes
dpserial.dll: 5.00.2134.0001 English Final Retail 8/23/2001 16:00:00 53520 bytes
dinput.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 159232 bytes
dinput8.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 181760 bytes
dimap.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 44032 bytes
diactfrm.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 394240 bytes
joy.cpl: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:58 68608 bytes
gcdef.dll: 5.01.2600.0000 English Final Retail 8/23/2001 16:00:00 76800 bytes
pid.dll: 5.03.2600.2180 English Final Retail 8/4/2004 04:05:44 35328 bytes
dsound.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 367616 bytes
dsound3d.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 1294336 bytes
dswave.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 19456 bytes
dsdmo.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 181760 bytes
dsdmoprp.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 71680 bytes
dmusic.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 104448 bytes
dmband.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 28672 bytes
dmcompos.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 61440 bytes
dmime.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 181248 bytes
dmloader.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 35840 bytes
dmstyle.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 105984 bytes
dmsynth.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 103424 bytes
dmscript.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 82432 bytes
dx7vb.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 619008 bytes
dx8vb.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 1227264 bytes
dxdiagn.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 2113536 bytes
mfc40.dll: 4.01.0000.6140 English Final Retail 8/23/2001 16:00:00 924432 bytes
mfc42.dll: 6.02.4131.0000 English Final Retail 8/4/2004 03:56:44 1028096 bytes
wsock32.dll: 5.01.2600.2180 English Final Retail 8/4/2004 03:56:48 22528 bytes
amstream.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:42 70656 bytes
devenum.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:44 59904 bytes
dxmasf.dll: 6.04.0009.1125 English Final Retail 8/4/2004 03:56:44 498205 bytes
mciqtz32.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:44 35328 bytes
mpg2splt.ax: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:58 148992 bytes
msdmo.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:44 14336 bytes
encapi.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:44 20480 bytes
qasf.dll: 9.00.0000.3250 English Final Retail 8/4/2004 03:56:46 237568 bytes
qcap.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:46 192512 bytes
qdv.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:46 279040 bytes
qdvd.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:46 385024 bytes
qedit.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:46 562176 bytes
qedwipes.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:26 733696 bytes
quartz.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:46 1287680 bytes
strmdll.dll: 4.01.0000.3928 English Final Retail 8/4/2004 03:56:46 246302 bytes
iac25_32.ax: 2.00.0005.0053 English Final Retail 8/4/2004 03:56:58 199680 bytes
ir41_32.ax: 4.51.0016.0003 English Final Retail 8/4/2004 03:56:58 848384 bytes
ir41_qc.dll: 4.30.0062.0002 English Final Retail 8/4/2004 03:56:44 120320 bytes
ir41_qcx.dll: 4.30.0064.0001 English Final Retail 8/4/2004 03:56:44 338432 bytes
ir50_32.dll: 5.2562.0015.0055 English Final Retail 8/4/2004 03:56:44 755200 bytes
ir50_qc.dll: 5.00.0063.0048 English Final Retail 8/4/2004 03:56:44 200192 bytes
ir50_qcx.dll: 5.00.0064.0048 English Final Retail 8/4/2004 03:56:44 183808 bytes
ivfsrc.ax: 5.10.0002.0051 English Final Retail 8/4/2004 03:56:58 154624 bytes
mswebdvd.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:46 204288 bytes
ks.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:15:22 140928 bytes
ksproxy.ax: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:58 130048 bytes
ksuser.dll: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:44 4096 bytes
stream.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:08:04 48640 bytes
mspclock.sys: 5.03.2600.2180 English Final Retail 8/3/2004 22:58:40 5376 bytes
mspqm.sys: 5.01.2600.2180 English Final Retail 8/3/2004 22:58:42 4992 bytes
mskssrv.sys: 5.03.2600.2180 English Final Retail 8/3/2004 22:58:42 7552 bytes
swenum.sys: 5.03.2600.2180 English Final Retail 8/4/2004 04:05:44 4352 bytes
mstee.sys: 5.03.2600.2180 English Final Retail 8/3/2004 22:58:40 5504 bytes
ipsink.ax: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:58 16384 bytes
mpeg2data.ax: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:58 118272 bytes
ndisip.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:10:14 10880 bytes
streamip.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:10:14 15360 bytes
msvidctl.dll: 6.05.2600.2180 English Final Retail 8/4/2004 03:56:44 1428480 bytes
slip.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:10:18 11136 bytes
nabtsfec.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:10:30 85376 bytes
ccdecode.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:10:18 17024 bytes
vbisurf.ax: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:58 30720 bytes
msyuv.dll: 5.03.2600.2180 English Final Retail 8/4/2004 04:05:44 17408 bytes
kstvtune.ax: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:58 61952 bytes
ksxbar.ax: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:58 43008 bytes
kswdmcap.ax: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:58 90624 bytes
vfwwdm32.dll: 5.01.2600.2180 English Final Retail 8/4/2004 00:56:48 53760 bytes
wstcodec.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:10:22 19328 bytes
wstdecod.dll: 5.03.2600.2180 English Final Retail 8/4/2004 03:56:48 50688 bytes
------------------
DirectShow Filters
------------------
WDM Streaming VBI Codecs:
NABTS/FEC VBI Codec,0x00200000,2,1,,5.03.2600.2180
CC Decoder,0x00200000,2,1,,5.03.2600.2180
WST Codec,0x00200000,1,1,,5.03.2600.2180
DirectShow Filters:
WMAudio Decoder DMO,0x00800800,1,1,,
WMSpeech Decoder DMO,0x00600800,1,1,,
Mpeg4s Decoder DMO,0x00800001,1,1,,
WMV Screen decoder DMO,0x00800001,1,1,,
WMVideo Decoder DMO,0x00800001,1,1,,
Mpeg43 Decoder DMO,0x00800001,1,1,,
Mpeg4 Decoder DMO,0x00800001,1,1,,
WMT MuxDeMux Filter,0x00200000,0,0,wmm2filt.dll,2.01.4026.0000
Full Screen Renderer,0x00200000,1,0,quartz.dll,6.05.2600.2180
Gretech ASF Source Filter,0x00200000,0,1,GSFU.ax,
Gretech MPEG Source Filter,0x00200000,0,1,GSFU.ax,
DV Muxer,0x00400000,0,0,qdv.dll,6.05.2600.2180
Color Space Converter,0x00400001,1,1,quartz.dll,6.05.2600.2180
WM ASF Reader,0x00400000,0,0,qasf.dll,9.00.0000.3250
AVI Splitter,0x00600000,1,1,quartz.dll,6.05.2600.2180
WMT AudioAnalyzer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VGA 16 Color Ditherer,0x00400000,1,1,quartz.dll,6.05.2600.2180
Indeo® video 5.10 Compression Filter,0x00200000,1,1,ir50_32.dll,5.2562.0015.0055
CyberLink AudioCD Filter (PDVD7),0x00600000,0,1,CLAudioCD.ax,5.00.0000.4417
Windows Media Audio Decoder,0x00800001,1,1,msadds32.ax,8.00.0000.4487
RealVideo Decoder,0x00600000,1,1,RealMediaSplitter.ax,1.00.0001.0002
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
CyberLink Audio Decoder,0x00601000,1,1,Claud.ax,6.01.0000.4420
WMT Format Conversion,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
StreamBufferSink,0x00200000,0,0,sbe.dll,6.05.2600.2180
WMT Black Frame Generator,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MJPEG Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2180
CyberLink Audio Effect (PDVD7),0x00200000,1,1,CLAudFx.ax,6.00.0000.4111
Indeo® video 5.10 Decompression Filter,0x00640000,1,1,ir50_32.dll,5.2562.0015.0055
WMT Screen Capture filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
Microsoft Screen Video Decompressor,0x00800000,1,1,msscds32.ax,8.00.0000.4487
MPEG-I Stream Splitter,0x00600000,1,2,quartz.dll,6.05.2600.2180
SAMI (CC) Parser,0x00400000,1,1,quartz.dll,6.05.2600.2180
MPEG Layer-3 Decoder,0x00810000,1,1,l3codecx.ax,1.05.0000.0050
CyberLink Audio Digital Transcoder,0x00200000,1,1,CLADT.ax,1.00.0000.0717
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,6.05.2600.2180
ACELP.net Sipro Lab Audio Decoder,0x00800001,1,1,acelpdec.ax,1.04.0000.0000
Gretech Video Filter,0x00200000,1,1,GVF.ax,
CyberLink SAC Video Decoder(PDVD7 HomeNetwork),0x00200000,2,3,CLVSD.ax,6.00.0000.2122
Internal Script Command Renderer,0x00800001,1,0,quartz.dll,6.05.2600.2180
MPEG Audio Decoder,0x03680001,1,1,quartz.dll,6.05.2600.2180
File Source (Netshow URL),0x00400000,0,1,wmpasf.dll,9.00.0000.3250
Gretech Theora Source Filter,0x00200000,0,1,GSFU.ax,
Gretech FLV Source Filter,0x00200000,0,1,GSFU.ax,
WMT Import Filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
DV Splitter,0x00600000,1,2,qdv.dll,6.05.2600.2180
Bitmap Generate,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Video Decoder,0x00800000,1,1,wmvds32.ax,8.00.0000.4487
Video Mixing Renderer 9,0x00200000,1,0,quartz.dll,6.05.2600.2180
Windows Media Video Decoder,0x00800000,1,1,wmv8ds32.ax,8.00.0000.4000
CyberLink Demux (PDVD7),0x00602000,1,0,CLDemuxer.ax,1.00.0000.4528
CyberLink MPEG Splitter(Scramble),0x00200000,1,2,CLSplter.ax,3.01.0000.1424
WMT VIH2 Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Gretech AsfEx Source Filter,0x00200000,0,1,GSFU.ax,
CyberLink BDROM Navigator,0x00600000,0,3,CLBDROMNav.ax,1.03.0000.3506
Record Queue,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
CyberLink Line21 Decoder (PDVD7.x),0x00200000,0,2,CLLine21.ax,4.00.0000.7602
Windows Media Multiplexer,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASX file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASX v.2 file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.3250
NSC file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ACM Wrapper,0x00600000,1,1,quartz.dll,6.05.2600.2180
Windows Media source filter,0x00600000,0,2,wmpasf.dll,9.00.0000.3250
Gretech AVI Source Filter,0x00200000,0,1,GSFU.ax,
Video Renderer,0x00800001,1,0,quartz.dll,6.05.2600.2180
Gretech Network(OGG) Filter,0x00200000,0,1,GNF.ax,
Frame Eater,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,6.05.2600.2180
Line 21 Decoder,0x00600000,1,1,qdvd.dll,6.05.2600.2180
Video Port Manager,0x00600000,2,1,quartz.dll,6.05.2600.2180
CyberLink Push-Mode CLStream (PDVD7),0x00200000,0,1,CLStream(PushMode).ax,1.00.0000.1524
CyberLink Audio Decoder (PDVD7 UPnP),0x00200000,1,1,CLAud.ax,6.00.0000.1803
WST Decoder,0x00600000,1,1,wstdecod.dll,5.03.2600.2180
Video Renderer,0x00400000,1,0,quartz.dll,6.05.2600.2180
RealMedia Source,0x00600000,0,0,RealMediaSplitter.ax,1.00.0001.0002
CyberLink Audio Spectrum Analyzer (PDVD7),0x00200000,1,1,CLAudSpa.ax,1.00.0000.0924
DivX Decoder Filter,0xff800000,1,1,DXdec.ax,6.00.0000.1571
WM ASF Writer,0x00400000,0,0,qasf.dll,9.00.0000.3250
Gretech Audio Filter,0x00200000,1,1,GAF.ax,
WMT Sample Information Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,5.03.2600.2180
Microsoft MPEG-4 Video Decompressor,0x00800000,1,1,mpg4ds32.ax,8.00.0000.4487
File writer,0x00200000,1,0,qcap.dll,6.05.2600.2180
Gretech Network(FLV) Filter,0x00200000,0,1,GNF.ax,
CyberLink Video/SP Decoder (PDVD7),0x00602000,2,3,CLVsd.ax,8.00.0000.2103
Gretech OGG Source Filter,0x00200000,0,1,GSFU.ax,
Gretech Network(AVI) Filter,0x00200000,0,1,GNF.ax,
CyberLink BDRE Navigator,0x00600000,0,3,CLBDRENav.ax,1.00.0000.3506
WMT Log Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Virtual Renderer,0x00200000,1,0,wmm2filt.dll,2.01.4026.0000
RealAudio Decoder,0x00600000,1,1,RealMediaSplitter.ax,1.00.0001.0002
Gretech MKV Source Filter,0x00200000,0,1,GSFU.ax,
DVD Navigator,0x00200000,0,2,qdvd.dll,6.05.2600.2180
CyberLink DVD Navigator (PDVD7),0x00600000,0,3,CLNavX.ax,7.00.0000.3306
CyberLink TimeStretch Filter (PDVD7),0x00200000,1,1,clauts.ax,1.00.0000.5423
Overlay Mixer2,0x00400000,1,1,qdvd.dll,6.05.2600.2180
Cyberlink SubTitle Importor,0x00200000,1,1,CLSubTitle.ax,1.00.0000.1604
AVI Draw,0x00600064,9,1,quartz.dll,6.05.2600.2180
.RAM file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.3250
CyberLink HDDVD Navigator,0x00600000,0,6,HDDVDNav.ax,1.01.0000.1031
WMT DirectX Transform Wrapper,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
G.711 Codec,0x00200000,1,1,g711codc.ax,5.01.2600.0000
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
DV Video Decoder,0x00800000,1,1,qdv.dll,6.05.2600.2180
Indeo® audio software,0x00500000,1,1,iac25_32.ax,2.00.0005.0053
Windows Media Update Filter,0x00400000,1,0,wmpasf.dll,9.00.0000.3250
CyberLink MPEG-4 Splitter (PDVD7),0x00600000,1,2,clm4splt.ax,1.00.0000.4409
CyberLink HD/BD Mixer (PDVD7.x),0x00200000,1,2,CLHBMixer.ax,1.00.0000.2017
Gretech Network(SHOUTcast) Filter,0x00200000,0,1,GNF.ax,
ASF DIB Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF ACM Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF ICM Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF URL Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF JPEG Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF DJPEG Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF embedded stuff Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
9x8Resize,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WIA Stream Snapshot Filter,0x00200000,1,1,wiasf.ax,1.00.0000.0000
Gretech Network(GOM) Filter,0x00200000,0,1,GNF.ax,
Allocator Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
CyberLink VC-1 Decoder (PDVD7.x),0x00600400,1,3,CLVc1Dec.ax,2.01.0000.5824
SampleGrabber,0x00200000,1,1,qedit.dll,6.05.2600.2180
Null Renderer,0x00200000,1,0,qedit.dll,6.05.2600.2180
WMT Virtual Source,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
Gretech Network(OGG P2P) Filter,0x00200000,0,1,GNF.ax,
WMT Interlacer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
StreamBufferSource,0x00200000,0,0,sbe.dll,6.05.2600.2180
Smart Tee,0x00200000,1,2,qcap.dll,6.05.2600.2180
Overlay Mixer,0x00200000,0,0,qdvd.dll,6.05.2600.2180
AVI Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2180
Uncompressed Domain Shot Detection Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Gretech MP4 Source Filter,0x00200000,0,1,GSFU.ax,
AVI/WAV File Source,0x00400000,0,2,quartz.dll,6.05.2600.2180
QuickTime Movie Parser,0x00600000,1,1,quartz.dll,6.05.2600.2180
Wave Parser,0x00400000,1,1,quartz.dll,6.05.2600.2180
MIDI Parser,0x00400000,1,1,quartz.dll,6.05.2600.2180
Multi-file Parser,0x00400000,1,1,quartz.dll,6.05.2600.2180
File stream renderer,0x00400000,1,1,quartz.dll,6.05.2600.2180
XML Playlist,0x00400000,1,0,wmpasf.dll,9.00.0000.3250
CyberLink Audio Decode (PDVD7.x),0x00200000,1,1,claud_HBD.ax,8.01.0003.8230
RealMedia Splitter,0x00600000,1,1,RealMediaSplitter.ax,1.00.0001.0002
AVI Mux,0x00200000,1,0,qcap.dll,6.05.2600.2180
Line 21 Decoder 2,0x00600002,1,1,quartz.dll,6.05.2600.2180
File Source (Async.),0x00400000,0,1,quartz.dll,6.05.2600.2180
File Source (URL),0x00400000,0,1,quartz.dll,6.05.2600.2180
WMT DV Extract,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
CyberLink Video/SP BD-HD Decoder (PDVD7.x),0x00600000,2,3,CLVSD_HBD.ax,8.01.0000.7104
CyberLink Demux (PDVD7 UPnP),0x00200000,1,0,CLDemuxer.ax,1.00.0000.3421
WMT Switch Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Volume,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
CyberLink H.264/AVC Decoder (PDVD7.x),0x00600400,1,2,CL264dec.ax,2.01.0000.0828
Stretch Video,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Infinite Pin Tee Filter,0x00200000,1,1,qcap.dll,6.05.2600.2180
CyberLink Streamming Filter (PDVD7),0x00200000,0,1,CLStream.ax,1.01.0000.1524
QT Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2180
MPEG Video Decoder,0x40000001,1,1,quartz.dll,6.05.2600.2180
Indeo® video 4.4 Decompression Filter,0x00640000,1,1,ir41_32.ax,4.51.0016.0003
Indeo® video 4.4 Compression Filter,0x00200000,1,1,ir41_32.ax,4.51.0016.0003
WDM Streaming Tee/Splitter Devices:
Tee/Sink-to-Sink Converter,0x00200000,1,1,,5.03.2600.2180
WDM Streaming Data Transforms:
Microsoft Kernel Acoustic Echo Canceller,0x00000000,0,0,,
Microsoft Kernel GS Wavetable Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DLS Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DRM Audio Descrambler,0x00200000,1,1,,5.03.2600.2180
Video Compressors:
MSScreen encoder DMO,0x00600800,1,1,,
WMVideo9 Encoder DMO,0x00600800,1,1,,
MSScreen 9 encoder DMO,0x00600800,1,1,,
DV Video Encoder,0x00200000,0,0,qdv.dll,6.05.2600.2180
Indeo® video 5.10 Compression Filter,0x00100000,1,1,ir50_32.dll,5.2562.0015.0055
MJPEG Compressor,0x00200000,0,0,quartz.dll,6.05.2600.2180
Cinepak Codec by Radius,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel 4:2:0 Video V2.50,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo(R) Video R3.2,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo® Video 4.5,0x00200000,1,1,qcap.dll,6.05.2600.2180
Indeo® video 5.10,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel IYUV codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.261 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.263 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft RLE,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft Video 1,0x00200000,1,1,qcap.dll,6.05.2600.2180
Audio Compressors:
WM Speech Encoder DMO,0x00600800,1,1,,
WMAudio Encoder DMO,0x00600800,1,1,,
IAC2,0x00200000,1,1,quartz.dll,6.05.2600.2180
IMA ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.2180
PCM,0x00200000,1,1,quartz.dll,6.05.2600.2180
Microsoft ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.2180
ACELP.net,0x00200000,1,1,quartz.dll,6.05.2600.2180
DSP Group TrueSpeech(TM),0x00200000,1,1,quartz.dll,6.05.2600.2180
Windows Media Audio V1,0x00200000,1,1,quartz.dll,6.05.2600.2180
Windows Media Audio V2,0x00200000,1,1,quartz.dll,6.05.2600.2180
GSM 6.10,0x00200000,1,1,quartz.dll,6.05.2600.2180
Microsoft G.723.1,0x00200000,1,1,quartz.dll,6.05.2600.2180
CCITT A-Law,0x00200000,1,1,quartz.dll,6.05.2600.2180
CCITT u-Law,0x00200000,1,1,quartz.dll,6.05.2600.2180
MPEG Layer-3,0x00200000,1,1,quartz.dll,6.05.2600.2180
Audio Capture Sources:
Conexant HD Audio input,0x00200000,0,0,qcap.dll,6.05.2600.2180
Midi Renderers:
Default MidiOut Device,0x00800000,1,0,quartz.dll,6.05.2600.2180
Microsoft GS Wavetable SW Synth,0x00200000,1,0,quartz.dll,6.05.2600.2180
WDM Streaming Capture Devices:
Conexant HD Audio input,0x00200000,1,1,,5.03.2600.2180
,0x00000000,0,0,,
USB Video Device,0x00200000,1,1,,5.03.2600.2180
WDM Streaming Rendering Devices:
,0x00000000,0,0,,
Conexant HD Audio output,0x00200000,2,1,,5.03.2600.2180
BDA Rendering Filters:
BDA IP Sink,0x00200000,1,1,,5.03.2600.2180
Video Capture Sources:
USB Video Device,0x00200000,1,1,,5.03.2600.2180
WDM Streaming Mixer Devices:
Microsoft Kernel Wave Audio Mixer,0x00000000,0,0,,
BDA CP/CA Filters:
Decrypt/Tag,0x00600000,1,0,encdec.dll,6.05.2600.2180
Encrypt/Tag,0x00200000,0,0,encdec.dll,6.05.2600.2180
XDS Codec,0x00200000,0,0,encdec.dll,6.05.2600.2180
WDM Streaming Communication Transforms:
Tee/Sink-to-Sink Converter,0x00200000,1,1,,5.03.2600.2180
Audio Renderers:
Conexant HD Audio output,0x00200000,1,0,quartz.dll,6.05.2600.2180
CyberLink Audio Renderer (PDVD7.x),0x00200000,1,0,cladr.ax,6.00.0000.4309
Default DirectSound Device,0x00800000,1,0,quartz.dll,6.05.2600.2180
Default WaveOut Device,0x00200000,1,0,quartz.dll,6.05.2600.2180
DirectSound: Conexant HD Audio output,0x00200000,1,0,quartz.dll,6.05.2600.2180
WDM Streaming System Devices:
Conexant HD Audio input,0x00200000,3,1,,5.03.2600.2180
Conexant HD Audio output,0x00200000,5,1,,5.03.2600.2180
BDA Receiver Components:
BDA Slip De-Framer,0x00600000,1,1,,5.03.2600.2180
```
 
 
what can i do now
 
if it install when at last its say to reset sytem then its hang if i force to shutdown the its not begun properly and hang in middle of the start point in checkinh

---

### Post by martrn on 2009-10-21
You can find a partition editor called gparted and install a proper distribution of gnu/ubuntu/linux,  the partition editor software will resise/move/edit/delete partitions for you.  See [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/").


Your kernel is toast.  You could also change the [PREFIX] to [WUBI] in your initial thread, and maybe more wubi people might answer your post.

You could if you don't have much disk space install ubuntu to a usb pen drive and read and write your files to a pen drive, 2gb pen drives can be found and very little cost.  Then from the ubuntu install cd you can install ubuntu to your pen drive, just mark your pen drive to be formatted as reiserfs (better for pendrives).  This way you will have a full install of ubuntu, that you can carry around in your pocket.

Don't forget to spend some time defragging your windows drive, and ensuring you have a plan about what new partitions you want before you attempt to resize or move your partitions IF you decide to install a full ubuntu distribution.

---

