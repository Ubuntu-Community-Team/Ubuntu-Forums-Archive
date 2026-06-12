---
title: "Installation issues"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by Dreamsclick on 2010-03-03
I'm unable to even install Ubuntu 9.10. Below is the error i get. Pls help me start a new thread, so that i can get help from the proper source. I don't know how to start a new thread in this forum.
```

03-01 19:11 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 19:11 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-01 19:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-01 19:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\data
03-01 19:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\bin\7z.exe
03-01 19:11 DEBUG  CommonBackend: Fetching basic info...
03-01 19:11 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-01 19:11 DEBUG  CommonBackend: platform=win32
03-01 19:11 DEBUG  CommonBackend: osname=nt
03-01 19:11 DEBUG  CommonBackend: language=en_US
03-01 19:11 DEBUG  CommonBackend: encoding=cp1252
03-01 19:11 DEBUG  WindowsBackend: arch=amd64
03-01 19:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\data\isolist.ini
03-01 19:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 19:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 19:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 19:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 19:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 19:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 19:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 19:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 19:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 19:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 19:11 DEBUG  WindowsBackend: Fetching host info...
03-01 19:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 19:11 DEBUG  WindowsBackend: windows version=xp
03-01 19:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 19:11 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-01 19:11 DEBUG  WindowsBackend: windows_build=2600
03-01 19:11 DEBUG  WindowsBackend: gmt=5
03-01 19:11 DEBUG  WindowsBackend: country=US
03-01 19:11 DEBUG  WindowsBackend: timezone=America/New_York
03-01 19:11 DEBUG  WindowsBackend: windows_username=Thirumalar
03-01 19:11 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-01 19:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-01 19:11 DEBUG  WindowsBackend: windows_language_code=1033
03-01 19:11 DEBUG  WindowsBackend: windows_language=English
03-01 19:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-01 19:11 DEBUG  WindowsBackend: bootloader=xp
03-01 19:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 12216.9414063 mb free ntfs)
03-01 19:11 DEBUG  WindowsBackend: drive=Drive(C: hd 12216.9414063 mb free ntfs)
03-01 19:11 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
03-01 19:11 DEBUG  WindowsBackend: drive=Drive(E: hd 112538.355469 mb free ntfs)
03-01 19:11 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3476563 mb free ntfs)
03-01 19:11 DEBUG  WindowsBackend: drive=Drive(G: hd 86681.8320313 mb free ntfs)
03-01 19:11 DEBUG  WindowsBackend: uninstaller_path=None
03-01 19:11 DEBUG  WindowsBackend: previous_target_dir=None
03-01 19:11 DEBUG  WindowsBackend: previous_distro_name=None
03-01 19:11 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 19:11 DEBUG  WindowsBackend: keyboard_layout=us
03-01 19:11 DEBUG  WindowsBackend: keyboard_variant=
03-01 19:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 19:11 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 19:11 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 19:11 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 19:11 DEBUG  CommonBackend: Searching for local CDs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Ubuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Ubuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Ubuntu Netbook Remix CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Kubuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Kubuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Kubuntu Netbook CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Xubuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Xubuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Mythbuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp is a valid Mythbuntu CD
03-01 19:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\casper\filesystem.squashfs
03-01 19:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 19:11 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-01 19:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-01 19:11 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-01 19:11 INFO   root: Running the CD menu...
03-01 19:11 DEBUG  WindowsFrontend: __init__...
03-01 19:11 DEBUG  WindowsFrontend: on_init...
03-01 19:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\translations, languages=['en_US', 'en']
03-01 19:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\translations, languages=['en_US', 'en']
03-01 19:11 INFO   root: CD menu finished
03-01 19:11 INFO   root: Running the CD boot helper...
03-01 19:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\translations, languages=['en_US', 'en']
03-01 19:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\translations, languages=['en_US', 'en']
03-01 19:13 INFO   root: CD boot helper confirmed
03-01 19:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\translations, languages=['en_US', 'en']
03-01 19:13 DEBUG  TaskList: # Running tasklist...
03-01 19:13 DEBUG  TaskList: ## Running select_target_dir...
03-01 19:13 INFO   WindowsBackend: Installing into C:\ubuntu
03-01 19:13 DEBUG  TaskList: ## Finished select_target_dir
03-01 19:13 DEBUG  TaskList: ## Running create_dir_structure...
03-01 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-01 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-01 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-01 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-01 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-01 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-01 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-01 19:13 DEBUG  TaskList: ## Finished create_dir_structure
03-01 19:13 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 19:13 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 19:13 DEBUG  TaskList: ## Running create_uninstaller...
03-01 19:13 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-01 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-01 19:13 DEBUG  TaskList: ## Finished create_uninstaller
03-01 19:13 DEBUG  TaskList: ## Running copy_installation_files...
03-01 19:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-01 19:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\winboot -> C:\ubuntu\winboot
03-01 19:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl11.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-01 19:13 DEBUG  TaskList: ## Finished copy_installation_files
03-01 19:13 DEBUG  TaskList: ## Running use_cd...
03-01 19:13 DEBUG  TaskList: New task copy_file
03-01 19:13 DEBUG  TaskList: ### Running copy_file...
03-01 19:14 DEBUG  TaskList: ### Finished copy_file
03-01 19:14 DEBUG  TaskList: New task check_iso
03-01 19:14 DEBUG  TaskList: ### Running check_iso...
03-01 19:14 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-01 19:14 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-01 19:14 DEBUG  Distro:     does not contain casper\filesystem.squashfs
03-01 19:14 DEBUG  TaskList: ### Finished check_iso
03-01 19:14 DEBUG  TaskList: ## Finished use_cd
03-01 19:14 DEBUG  TaskList: ## Running extract_kernel...
03-01 19:14 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-01 19:14 DEBUG  TaskList: # Cancelling tasklist
03-01 19:14 DEBUG  TaskList: # Finished tasklist
03-01 19:14 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-01 19:14 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 19:14 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-01 19:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-01 19:14 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\data
03-01 19:14 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\bin\7z.exe
03-01 19:14 DEBUG  CommonBackend: Fetching basic info...
03-01 19:14 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-01 19:14 DEBUG  CommonBackend: platform=win32
03-01 19:14 DEBUG  CommonBackend: osname=nt
03-01 19:14 DEBUG  CommonBackend: language=en_US
03-01 19:14 DEBUG  CommonBackend: encoding=cp1252
03-01 19:14 DEBUG  WindowsBackend: arch=amd64
03-01 19:14 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\data\isolist.ini
03-01 19:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 19:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 19:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 19:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 19:14 DEBUG  WindowsBackend: Fetching host info...
03-01 19:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 19:14 DEBUG  WindowsBackend: windows version=xp
03-01 19:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 19:14 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-01 19:14 DEBUG  WindowsBackend: windows_build=2600
03-01 19:14 DEBUG  WindowsBackend: gmt=5
03-01 19:14 DEBUG  WindowsBackend: country=US
03-01 19:14 DEBUG  WindowsBackend: timezone=America/New_York
03-01 19:14 DEBUG  WindowsBackend: windows_username=Thirumalar
03-01 19:14 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-01 19:14 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-01 19:14 DEBUG  WindowsBackend: windows_language_code=1033
03-01 19:14 DEBUG  WindowsBackend: windows_language=English
03-01 19:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-01 19:14 DEBUG  WindowsBackend: bootloader=xp
03-01 19:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11514.4804688 mb free ntfs)
03-01 19:14 DEBUG  WindowsBackend: drive=Drive(C: hd 11514.4804688 mb free ntfs)
03-01 19:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
03-01 19:14 DEBUG  WindowsBackend: drive=Drive(E: hd 112538.355469 mb free ntfs)
03-01 19:14 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3476563 mb free ntfs)
03-01 19:14 DEBUG  WindowsBackend: drive=Drive(G: hd 86681.8320313 mb free ntfs)
03-01 19:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-01 19:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-01 19:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 19:14 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 19:14 DEBUG  WindowsBackend: keyboard_layout=us
03-01 19:14 DEBUG  WindowsBackend: keyboard_variant=
03-01 19:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 19:14 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 19:14 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 19:14 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 19:14 DEBUG  CommonBackend: Searching for local CDs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu Netbook Remix CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu Netbook CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
03-01 19:14 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 19:14 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-01 19:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-01 19:14 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-01 19:14 INFO   root: Running the CD menu...
03-01 19:14 DEBUG  WindowsFrontend: __init__...
03-01 19:14 DEBUG  WindowsFrontend: on_init...
03-01 19:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-01 19:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-01 19:15 INFO   root: CD menu finished
03-01 19:15 INFO   root: Already installed, running the uninstaller...
03-01 19:15 INFO   root: Running the uninstaller...
03-01 19:15 INFO   CommonBackend: This is the uninstaller running
03-01 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-01 19:15 INFO   root: Received settings
03-01 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-01 19:15 DEBUG  TaskList: # Running tasklist...
03-01 19:15 DEBUG  TaskList: ## Running Backup ISO...
03-01 19:15 DEBUG  TaskList: ## Finished Backup ISO
03-01 19:15 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 19:15 ERROR  WindowsBackend: Cannot find bcdedit
03-01 19:15 DEBUG  WindowsBackend: undo_bootini C:
03-01 19:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 11514.4804688 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: undo_bootini E:
03-01 19:15 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 112538.355469 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: undo_bootini F:
03-01 19:15 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 16310.3476563 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: undo_bootini G:
03-01 19:15 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 86681.8320313 mb free ntfs)
03-01 19:15 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 19:15 DEBUG  TaskList: ## Running Remove target dir...
03-01 19:15 DEBUG  CommonBackend: Deleting C:\ubuntu
03-01 19:15 DEBUG  TaskList: ## Finished Remove target dir
03-01 19:15 DEBUG  TaskList: ## Running Remove registry key...
03-01 19:15 DEBUG  TaskList: ## Finished Remove registry key
03-01 19:15 DEBUG  TaskList: # Finished tasklist
03-01 19:15 INFO   root: Almost finished uninstalling
03-01 19:15 INFO   root: Finished uninstallation
03-01 19:15 DEBUG  CommonBackend: Fetching basic info...
03-01 19:15 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-01 19:15 DEBUG  CommonBackend: platform=win32
03-01 19:15 DEBUG  CommonBackend: osname=nt
03-01 19:15 DEBUG  WindowsBackend: arch=amd64
03-01 19:15 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\data\isolist.ini
03-01 19:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 19:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 19:15 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 19:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 19:15 DEBUG  WindowsBackend: Fetching host info...
03-01 19:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 19:15 DEBUG  WindowsBackend: windows version=xp
03-01 19:15 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 19:15 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-01 19:15 DEBUG  WindowsBackend: windows_build=2600
03-01 19:15 DEBUG  WindowsBackend: gmt=5
03-01 19:15 DEBUG  WindowsBackend: country=US
03-01 19:15 DEBUG  WindowsBackend: timezone=America/New_York
03-01 19:15 DEBUG  WindowsBackend: windows_username=Thirumalar
03-01 19:15 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-01 19:15 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-01 19:15 DEBUG  WindowsBackend: windows_language_code=1033
03-01 19:15 DEBUG  WindowsBackend: windows_language=English
03-01 19:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-01 19:15 DEBUG  WindowsBackend: bootloader=xp
03-01 19:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 12170.7109375 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: drive=Drive(C: hd 12170.7109375 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
03-01 19:15 DEBUG  WindowsBackend: drive=Drive(E: hd 112538.355469 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3476563 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: drive=Drive(G: hd 86681.8320313 mb free ntfs)
03-01 19:15 DEBUG  WindowsBackend: uninstaller_path=None
03-01 19:15 DEBUG  WindowsBackend: previous_target_dir=None
03-01 19:15 DEBUG  WindowsBackend: previous_distro_name=None
03-01 19:15 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 19:15 DEBUG  WindowsBackend: keyboard_layout=us
03-01 19:15 DEBUG  WindowsBackend: keyboard_variant=
03-01 19:15 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-01 19:15 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 19:15 DEBUG  CommonBackend: Searching for local CDs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu Netbook Remix CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu Netbook CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
03-01 19:15 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
03-01 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 19:15 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-01 19:15 INFO   root: Running the CD boot helper...
03-01 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-01 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-01 19:15 INFO   root: CD boot helper confirmed
03-01 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
03-01 19:15 DEBUG  TaskList: # Running tasklist...
03-01 19:15 DEBUG  TaskList: ## Running select_target_dir...
03-01 19:15 INFO   WindowsBackend: Installing into C:\ubuntu
03-01 19:15 DEBUG  TaskList: ## Finished select_target_dir
03-01 19:15 DEBUG  TaskList: ## Running create_dir_structure...
03-01 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-01 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-01 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-01 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-01 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-01 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-01 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-01 19:15 DEBUG  TaskList: ## Finished create_dir_structure
03-01 19:15 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 19:15 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 19:15 DEBUG  TaskList: ## Running create_uninstaller...
03-01 19:15 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-01 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-01 19:15 DEBUG  TaskList: ## Finished create_uninstaller
03-01 19:15 DEBUG  TaskList: ## Running copy_installation_files...
03-01 19:15 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-01 19:15 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\winboot -> C:\ubuntu\winboot
03-01 19:15 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl12.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-01 19:15 DEBUG  TaskList: ## Finished copy_installation_files
03-01 19:15 DEBUG  TaskList: ## Running use_cd...
03-01 19:15 DEBUG  TaskList: New task copy_file
03-01 19:15 DEBUG  TaskList: ### Running copy_file...
03-01 19:18 DEBUG  TaskList: ### Finished copy_file
03-01 19:18 DEBUG  TaskList: New task check_iso
03-01 19:18 DEBUG  TaskList: ### Running check_iso...
03-01 19:18 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-01 19:18 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-01 19:18 DEBUG  Distro:     does not contain casper\filesystem.squashfs
03-01 19:18 DEBUG  TaskList: ### Finished check_iso
03-01 19:18 DEBUG  TaskList: ## Finished use_cd
03-01 19:18 DEBUG  TaskList: ## Running extract_kernel...
03-01 19:18 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-01 19:18 DEBUG  TaskList: # Cancelling tasklist
03-01 19:18 DEBUG  TaskList: # Finished tasklist
03-01 19:18 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-03 21:07 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 21:07 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 21:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-03 21:07 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\data
03-03 21:07 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\bin\7z.exe
03-03 21:07 DEBUG  CommonBackend: Fetching basic info...
03-03 21:07 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 21:07 DEBUG  CommonBackend: platform=win32
03-03 21:07 DEBUG  CommonBackend: osname=nt
03-03 21:07 DEBUG  CommonBackend: language=en_US
03-03 21:07 DEBUG  CommonBackend: encoding=cp1252
03-03 21:07 DEBUG  WindowsBackend: arch=amd64
03-03 21:07 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
03-03 21:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 21:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 21:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 21:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 21:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 21:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 21:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 21:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 21:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 21:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 21:07 DEBUG  WindowsBackend: Fetching host info...
03-03 21:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 21:07 DEBUG  WindowsBackend: windows version=xp
03-03 21:07 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 21:07 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 21:07 DEBUG  WindowsBackend: windows_build=2600
03-03 21:07 DEBUG  WindowsBackend: gmt=5
03-03 21:07 DEBUG  WindowsBackend: country=US
03-03 21:07 DEBUG  WindowsBackend: timezone=America/New_York
03-03 21:07 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 21:07 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 21:07 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 21:07 DEBUG  WindowsBackend: windows_language_code=1033
03-03 21:07 DEBUG  WindowsBackend: windows_language=English
03-03 21:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 21:07 DEBUG  WindowsBackend: bootloader=xp
03-03 21:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11400.265625 mb free ntfs)
03-03 21:07 DEBUG  WindowsBackend: drive=Drive(C: hd 11400.265625 mb free ntfs)
03-03 21:07 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 21:07 DEBUG  WindowsBackend: drive=Drive(E: hd 112538.355469 mb free ntfs)
03-03 21:07 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3476563 mb free ntfs)
03-03 21:07 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6914063 mb free ntfs)
03-03 21:07 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-03 21:07 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-03 21:07 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-03 21:07 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 21:07 DEBUG  WindowsBackend: keyboard_layout=us
03-03 21:07 DEBUG  WindowsBackend: keyboard_variant=
03-03 21:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 21:07 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 21:07 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 21:07 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 21:07 DEBUG  CommonBackend: Searching for local CDs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook Remix CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-03 21:07 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 21:07 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 21:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 21:07 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 21:07 INFO   root: Running the CD menu...
03-03 21:07 DEBUG  WindowsFrontend: __init__...
03-03 21:07 DEBUG  WindowsFrontend: on_init...
03-03 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-03 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-03 21:07 INFO   root: CD menu finished
03-03 21:07 INFO   root: Already installed, running the uninstaller...
03-03 21:07 INFO   root: Running the uninstaller...
03-03 21:07 INFO   CommonBackend: This is the uninstaller running
03-03 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-03 21:08 INFO   root: Received settings
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-03 21:08 DEBUG  TaskList: # Running tasklist...
03-03 21:08 DEBUG  TaskList: ## Running Backup ISO...
03-03 21:08 DEBUG  TaskList: ## Finished Backup ISO
03-03 21:08 DEBUG  TaskList: ## Running Remove bootloader entry...
03-03 21:08 ERROR  WindowsBackend: Cannot find bcdedit
03-03 21:08 DEBUG  WindowsBackend: undo_bootini C:
03-03 21:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 11400.265625 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: undo_bootini E:
03-03 21:08 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 112538.355469 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: undo_bootini F:
03-03 21:08 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 16310.3476563 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: undo_bootini G:
03-03 21:08 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 86624.6914063 mb free ntfs)
03-03 21:08 DEBUG  TaskList: ## Finished Remove bootloader entry
03-03 21:08 DEBUG  TaskList: ## Running Remove target dir...
03-03 21:08 DEBUG  CommonBackend: Deleting C:\ubuntu
03-03 21:08 DEBUG  TaskList: ## Finished Remove target dir
03-03 21:08 DEBUG  TaskList: ## Running Remove registry key...
03-03 21:08 DEBUG  TaskList: ## Finished Remove registry key
03-03 21:08 DEBUG  TaskList: # Finished tasklist
03-03 21:08 INFO   root: Almost finished uninstalling
03-03 21:08 INFO   root: Finished uninstallation
03-03 21:08 DEBUG  CommonBackend: Fetching basic info...
03-03 21:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 21:08 DEBUG  CommonBackend: platform=win32
03-03 21:08 DEBUG  CommonBackend: osname=nt
03-03 21:08 DEBUG  WindowsBackend: arch=amd64
03-03 21:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
03-03 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 21:08 DEBUG  WindowsBackend: Fetching host info...
03-03 21:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 21:08 DEBUG  WindowsBackend: windows version=xp
03-03 21:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 21:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 21:08 DEBUG  WindowsBackend: windows_build=2600
03-03 21:08 DEBUG  WindowsBackend: gmt=5
03-03 21:08 DEBUG  WindowsBackend: country=US
03-03 21:08 DEBUG  WindowsBackend: timezone=America/New_York
03-03 21:08 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 21:08 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 21:08 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 21:08 DEBUG  WindowsBackend: windows_language_code=1033
03-03 21:08 DEBUG  WindowsBackend: windows_language=English
03-03 21:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 21:08 DEBUG  WindowsBackend: bootloader=xp
03-03 21:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 12090.6210938 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(C: hd 12090.6210938 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(E: hd 112538.355469 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3476563 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6914063 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: uninstaller_path=None
03-03 21:08 DEBUG  WindowsBackend: previous_target_dir=None
03-03 21:08 DEBUG  WindowsBackend: previous_distro_name=None
03-03 21:08 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 21:08 DEBUG  WindowsBackend: keyboard_layout=us
03-03 21:08 DEBUG  WindowsBackend: keyboard_variant=
03-03 21:08 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 21:08 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 21:08 DEBUG  CommonBackend: Searching for local CDs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook Remix CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 21:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 21:08 INFO   root: Running the CD boot helper...
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-03 21:08 INFO   WindowsFrontend: Operation cancelled
03-03 21:08 DEBUG  WindowsFrontend: frontend.quit
03-03 21:08 DEBUG  WindowsFrontend: frontend.on_quit
03-03 21:08 DEBUG  root: application.on_quit
03-03 21:08 INFO   root: sys.exit
03-03 21:08 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 21:08 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 21:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-03 21:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\data
03-03 21:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\bin\7z.exe
03-03 21:08 DEBUG  CommonBackend: Fetching basic info...
03-03 21:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 21:08 DEBUG  CommonBackend: platform=win32
03-03 21:08 DEBUG  CommonBackend: osname=nt
03-03 21:08 DEBUG  CommonBackend: language=en_US
03-03 21:08 DEBUG  CommonBackend: encoding=cp1252
03-03 21:08 DEBUG  WindowsBackend: arch=amd64
03-03 21:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\data\isolist.ini
03-03 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 21:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 21:08 DEBUG  WindowsBackend: Fetching host info...
03-03 21:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 21:08 DEBUG  WindowsBackend: windows version=xp
03-03 21:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 21:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 21:08 DEBUG  WindowsBackend: windows_build=2600
03-03 21:08 DEBUG  WindowsBackend: gmt=5
03-03 21:08 DEBUG  WindowsBackend: country=US
03-03 21:08 DEBUG  WindowsBackend: timezone=America/New_York
03-03 21:08 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 21:08 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 21:08 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 21:08 DEBUG  WindowsBackend: windows_language_code=1033
03-03 21:08 DEBUG  WindowsBackend: windows_language=English
03-03 21:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 21:08 DEBUG  WindowsBackend: bootloader=xp
03-03 21:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 12062.2109375 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(C: hd 12062.2109375 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(E: hd 112537.839844 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3320313 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6757813 mb free ntfs)
03-03 21:08 DEBUG  WindowsBackend: uninstaller_path=None
03-03 21:08 DEBUG  WindowsBackend: previous_target_dir=None
03-03 21:08 DEBUG  WindowsBackend: previous_distro_name=None
03-03 21:08 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 21:08 DEBUG  WindowsBackend: keyboard_layout=us
03-03 21:08 DEBUG  WindowsBackend: keyboard_variant=
03-03 21:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 21:08 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 21:08 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 21:08 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 21:08 DEBUG  CommonBackend: Searching for local CDs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Ubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Ubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Ubuntu Netbook Remix CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Kubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Kubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Kubuntu Netbook CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Xubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Xubuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Mythbuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp is a valid Mythbuntu CD
03-03 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\casper\filesystem.squashfs
03-03 21:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 21:08 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 21:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 21:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 21:08 INFO   root: Running the CD menu...
03-03 21:08 DEBUG  WindowsFrontend: __init__...
03-03 21:08 DEBUG  WindowsFrontend: on_init...
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\translations, languages=['en_US', 'en']
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\translations, languages=['en_US', 'en']
03-03 21:08 INFO   root: CD menu finished
03-03 21:08 INFO   root: Running the CD boot helper...
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\translations, languages=['en_US', 'en']
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\translations, languages=['en_US', 'en']
03-03 21:08 INFO   root: CD boot helper confirmed
03-03 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\translations, languages=['en_US', 'en']
03-03 21:08 DEBUG  TaskList: # Running tasklist...
03-03 21:08 DEBUG  TaskList: ## Running select_target_dir...
03-03 21:08 INFO   WindowsBackend: Installing into C:\ubuntu
03-03 21:08 DEBUG  TaskList: ## Finished select_target_dir
03-03 21:08 DEBUG  TaskList: ## Running create_dir_structure...
03-03 21:08 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-03 21:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-03 21:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-03 21:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-03 21:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-03 21:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-03 21:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-03 21:08 DEBUG  TaskList: ## Finished create_dir_structure
03-03 21:08 DEBUG  TaskList: ## Running uncompress_target_dir...
03-03 21:08 DEBUG  TaskList: ## Finished uncompress_target_dir
03-03 21:08 DEBUG  TaskList: ## Running create_uninstaller...
03-03 21:08 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-03 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-03 21:08 DEBUG  TaskList: ## Finished create_uninstaller
03-03 21:08 DEBUG  TaskList: ## Running copy_installation_files...
03-03 21:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-03 21:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\winboot -> C:\ubuntu\winboot
03-03 21:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-03 21:08 DEBUG  TaskList: ## Finished copy_installation_files
03-03 21:08 DEBUG  TaskList: ## Running use_cd...
03-03 21:08 DEBUG  TaskList: New task copy_file
03-03 21:08 DEBUG  TaskList: ### Running copy_file...
03-03 21:11 DEBUG  TaskList: ### Finished copy_file
03-03 21:11 DEBUG  TaskList: New task check_iso
03-03 21:11 DEBUG  TaskList: ### Running check_iso...
03-03 21:11 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-03 21:11 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-03 21:11 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-03 21:11 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 21:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 21:11 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-03 21:11 DEBUG  TaskList: New task get_metalink
03-03 21:11 DEBUG  TaskList: #### Running get_metalink...
03-03 21:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > C:\ubuntu\install
03-03 21:11 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
03-03 21:11 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-amd64.metalink) > C:\ubuntu\install
03-03 21:11 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-amd64.metalink) err=[Errno 14] HTTP Error 404: Not Found
03-03 21:11 DEBUG  TaskList: #### Finished get_metalink
03-03 21:11 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\ubuntu\install\installation.iso, ignoring
03-03 21:11 DEBUG  TaskList: ### Finished check_iso
03-03 21:11 DEBUG  TaskList: ## Finished use_cd
03-03 21:11 DEBUG  TaskList: ## Running extract_kernel...
03-03 21:11 DEBUG  CommonBackend: Copying files from CD D:\
03-03 21:11 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-03 21:11 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
03-03 21:11 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = f2bec09da1b46a21c0e6cc3192ca2e4f == f2bec09da1b46a21c0e6cc3192ca2e4f
03-03 21:11 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
03-03 21:11 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = e09f7d0e9500f67156730ad6093ce225 == e09f7d0e9500f67156730ad6093ce225
03-03 21:11 DEBUG  TaskList: ## Finished extract_kernel
03-03 21:11 DEBUG  TaskList: ## Running create_preseed_cdboot...
03-03 21:11 DEBUG  TaskList: ## Finished create_preseed_cdboot
03-03 21:11 DEBUG  TaskList: ## Running modify_bootloader...
03-03 21:11 DEBUG  TaskList: New task modify_bootini
03-03 21:11 DEBUG  TaskList: ### Running modify_bootini...
03-03 21:11 DEBUG  WindowsBackend: modify_bootini C:
03-03 21:11 DEBUG  TaskList: ### Finished modify_bootini
03-03 21:11 DEBUG  TaskList: New task modify_bootini
03-03 21:11 DEBUG  TaskList: ### Running modify_bootini...
03-03 21:11 DEBUG  WindowsBackend: modify_bootini E:
03-03 21:11 DEBUG  WindowsBackend: Could not find boot.ini E:\boot.ini
03-03 21:11 DEBUG  TaskList: ### Finished modify_bootini
03-03 21:11 DEBUG  TaskList: New task modify_bootini
03-03 21:11 DEBUG  TaskList: ### Running modify_bootini...
03-03 21:11 DEBUG  WindowsBackend: modify_bootini F:
03-03 21:11 DEBUG  WindowsBackend: Could not find boot.ini F:\boot.ini
03-03 21:11 DEBUG  TaskList: ### Finished modify_bootini
03-03 21:11 DEBUG  TaskList: New task modify_bootini
03-03 21:11 DEBUG  TaskList: ### Running modify_bootini...
03-03 21:11 DEBUG  WindowsBackend: modify_bootini G:
03-03 21:11 DEBUG  WindowsBackend: Could not find boot.ini G:\boot.ini
03-03 21:11 DEBUG  TaskList: ### Finished modify_bootini
03-03 21:11 DEBUG  TaskList: ## Finished modify_bootloader
03-03 21:11 DEBUG  TaskList: ## Running modify_grub_configuration...
03-03 21:11 DEBUG  TaskList: ## Finished modify_grub_configuration
03-03 21:11 DEBUG  TaskList: ## Running uncompress_files...
03-03 21:11 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
03-03 21:11 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
03-03 21:11 DEBUG  TaskList: ## Finished uncompress_files
03-03 21:11 DEBUG  TaskList: ## Running eject_cd...
03-03 21:11 DEBUG  TaskList: ## Finished eject_cd
03-03 21:11 DEBUG  TaskList: # Finished tasklist
03-03 21:11 INFO   root: Almost finished installing
03-03 21:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl56.tmp\translations, languages=['en_US', 'en']
03-03 21:12 INFO   root: Finished installation
03-03 21:12 INFO   root: Rebooting
03-03 21:12 DEBUG  TaskList: # Running tasklist...
03-03 21:12 DEBUG  TaskList: ## Running reboot...
03-03 21:12 DEBUG  TaskList: ## Finished reboot
03-03 21:12 DEBUG  TaskList: # Finished tasklist
03-03 21:12 DEBUG  root: application.quit
03-03 21:12 DEBUG  WindowsFrontend: frontend.quit
03-03 21:12 DEBUG  WindowsFrontend: frontend.on_quit
03-03 21:12 DEBUG  root: application.on_quit
03-03 21:12 INFO   root: sys.exit
03-03 22:10 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 22:10 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 22:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-03 22:10 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\data
03-03 22:10 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\bin\7z.exe
03-03 22:10 DEBUG  CommonBackend: Fetching basic info...
03-03 22:10 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:10 DEBUG  CommonBackend: platform=win32
03-03 22:10 DEBUG  CommonBackend: osname=nt
03-03 22:10 DEBUG  CommonBackend: language=en_US
03-03 22:10 DEBUG  CommonBackend: encoding=cp1252
03-03 22:10 DEBUG  WindowsBackend: arch=amd64
03-03 22:10 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\data\isolist.ini
03-03 22:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:10 DEBUG  WindowsBackend: Fetching host info...
03-03 22:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:10 DEBUG  WindowsBackend: windows version=xp
03-03 22:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:10 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:10 DEBUG  WindowsBackend: windows_build=2600
03-03 22:10 DEBUG  WindowsBackend: gmt=5
03-03 22:10 DEBUG  WindowsBackend: country=US
03-03 22:10 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:10 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:10 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:10 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:10 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:10 DEBUG  WindowsBackend: windows_language=English
03-03 22:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:10 DEBUG  WindowsBackend: bootloader=xp
03-03 22:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10632.484375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(C: hd 10632.484375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-03 22:10 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-03 22:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-03 22:10 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:10 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:10 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 22:10 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 22:10 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:10 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:10 DEBUG  CommonBackend: Searching for local CDs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Kubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Kubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Kubuntu Netbook CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Xubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Xubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Mythbuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp is a valid Mythbuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:10 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:10 INFO   root: Running the CD menu...
03-03 22:10 DEBUG  WindowsFrontend: __init__...
03-03 22:10 DEBUG  WindowsFrontend: on_init...
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\translations, languages=['en_US', 'en']
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl3F.tmp\translations, languages=['en_US', 'en']
03-03 22:10 INFO   root: CD menu finished
03-03 22:10 DEBUG  CommonBackend: Showing info
03-03 22:10 DEBUG  root: application.quit
03-03 22:10 DEBUG  WindowsFrontend: frontend.quit
03-03 22:10 DEBUG  WindowsFrontend: frontend.on_quit
03-03 22:10 DEBUG  root: application.on_quit
03-03 22:10 INFO   root: sys.exit
03-03 22:10 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 22:10 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 22:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-03 22:10 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\data
03-03 22:10 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\bin\7z.exe
03-03 22:10 DEBUG  CommonBackend: Fetching basic info...
03-03 22:10 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:10 DEBUG  CommonBackend: platform=win32
03-03 22:10 DEBUG  CommonBackend: osname=nt
03-03 22:10 DEBUG  CommonBackend: language=en_US
03-03 22:10 DEBUG  CommonBackend: encoding=cp1252
03-03 22:10 DEBUG  WindowsBackend: arch=amd64
03-03 22:10 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\data\isolist.ini
03-03 22:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:10 DEBUG  WindowsBackend: Fetching host info...
03-03 22:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:10 DEBUG  WindowsBackend: windows version=xp
03-03 22:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:10 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:10 DEBUG  WindowsBackend: windows_build=2600
03-03 22:10 DEBUG  WindowsBackend: gmt=5
03-03 22:10 DEBUG  WindowsBackend: country=US
03-03 22:10 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:10 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:10 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:10 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:10 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:10 DEBUG  WindowsBackend: windows_language=English
03-03 22:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:10 DEBUG  WindowsBackend: bootloader=xp
03-03 22:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10632.4609375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(C: hd 10632.4609375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-03 22:10 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-03 22:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-03 22:10 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:10 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:10 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 22:10 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 22:10 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:10 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:10 DEBUG  CommonBackend: Searching for local CDs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu Netbook CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:10 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:10 INFO   root: Running the CD menu...
03-03 22:10 DEBUG  WindowsFrontend: __init__...
03-03 22:10 DEBUG  WindowsFrontend: on_init...
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
03-03 22:10 INFO   root: CD menu finished
03-03 22:10 INFO   root: Already installed, running the uninstaller...
03-03 22:10 INFO   root: Running the uninstaller...
03-03 22:10 INFO   CommonBackend: This is the uninstaller running
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
03-03 22:10 INFO   root: Received settings
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
03-03 22:10 DEBUG  TaskList: # Running tasklist...
03-03 22:10 DEBUG  TaskList: ## Running Backup ISO...
03-03 22:10 DEBUG  TaskList: ## Finished Backup ISO
03-03 22:10 DEBUG  TaskList: ## Running Remove bootloader entry...
03-03 22:10 ERROR  WindowsBackend: Cannot find bcdedit
03-03 22:10 DEBUG  WindowsBackend: undo_bootini C:
03-03 22:10 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 10632.4609375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: undo_bootini E:
03-03 22:10 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: undo_bootini F:
03-03 22:10 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: undo_bootini G:
03-03 22:10 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:10 DEBUG  TaskList: ## Finished Remove bootloader entry
03-03 22:10 DEBUG  TaskList: ## Running Remove target dir...
03-03 22:10 DEBUG  CommonBackend: Deleting C:\ubuntu
03-03 22:10 DEBUG  TaskList: ## Finished Remove target dir
03-03 22:10 DEBUG  TaskList: ## Running Remove registry key...
03-03 22:10 DEBUG  TaskList: ## Finished Remove registry key
03-03 22:10 DEBUG  TaskList: # Finished tasklist
03-03 22:10 INFO   root: Almost finished uninstalling
03-03 22:10 INFO   root: Finished uninstallation
03-03 22:10 DEBUG  CommonBackend: Fetching basic info...
03-03 22:10 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:10 DEBUG  CommonBackend: platform=win32
03-03 22:10 DEBUG  CommonBackend: osname=nt
03-03 22:10 DEBUG  WindowsBackend: arch=amd64
03-03 22:10 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\data\isolist.ini
03-03 22:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:10 DEBUG  WindowsBackend: Fetching host info...
03-03 22:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:10 DEBUG  WindowsBackend: windows version=xp
03-03 22:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:10 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:10 DEBUG  WindowsBackend: windows_build=2600
03-03 22:10 DEBUG  WindowsBackend: gmt=5
03-03 22:10 DEBUG  WindowsBackend: country=US
03-03 22:10 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:10 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:10 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:10 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:10 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:10 DEBUG  WindowsBackend: windows_language=English
03-03 22:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:10 DEBUG  WindowsBackend: bootloader=xp
03-03 22:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11332.75 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(C: hd 11332.75 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:10 DEBUG  WindowsBackend: uninstaller_path=None
03-03 22:10 DEBUG  WindowsBackend: previous_target_dir=None
03-03 22:10 DEBUG  WindowsBackend: previous_distro_name=None
03-03 22:10 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:10 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:10 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:10 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:10 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:10 DEBUG  CommonBackend: Searching for local CDs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu Netbook CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
03-03 22:10 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
03-03 22:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:10 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:10 INFO   root: Running the installer...
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
03-03 22:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
03-03 22:11 INFO   WindowsFrontend: Operation cancelled
03-03 22:11 DEBUG  WindowsFrontend: frontend.quit
03-03 22:11 DEBUG  WindowsFrontend: frontend.on_quit
03-03 22:11 DEBUG  root: application.on_quit
03-03 22:11 INFO   root: sys.exit
03-03 22:11 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 22:11 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 22:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-03 22:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\data
03-03 22:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\bin\7z.exe
03-03 22:11 DEBUG  CommonBackend: Fetching basic info...
03-03 22:11 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:11 DEBUG  CommonBackend: platform=win32
03-03 22:11 DEBUG  CommonBackend: osname=nt
03-03 22:11 DEBUG  CommonBackend: language=en_US
03-03 22:11 DEBUG  CommonBackend: encoding=cp1252
03-03 22:11 DEBUG  WindowsBackend: arch=amd64
03-03 22:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\data\isolist.ini
03-03 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:11 DEBUG  WindowsBackend: Fetching host info...
03-03 22:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:11 DEBUG  WindowsBackend: windows version=xp
03-03 22:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:11 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:11 DEBUG  WindowsBackend: windows_build=2600
03-03 22:11 DEBUG  WindowsBackend: gmt=5
03-03 22:11 DEBUG  WindowsBackend: country=US
03-03 22:11 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:11 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:11 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:11 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:11 DEBUG  WindowsBackend: windows_language=English
03-03 22:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:11 DEBUG  WindowsBackend: bootloader=xp
03-03 22:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11332.21875 mb free ntfs)
03-03 22:11 DEBUG  WindowsBackend: drive=Drive(C: hd 11332.21875 mb free ntfs)
03-03 22:11 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:11 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:11 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:11 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:11 DEBUG  WindowsBackend: uninstaller_path=None
03-03 22:11 DEBUG  WindowsBackend: previous_target_dir=None
03-03 22:11 DEBUG  WindowsBackend: previous_distro_name=None
03-03 22:11 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:11 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:11 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 22:11 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 22:11 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:11 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:11 DEBUG  CommonBackend: Searching for local CDs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Ubuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Ubuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Kubuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Kubuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Kubuntu Netbook CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Xubuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Xubuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Mythbuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp is a valid Mythbuntu CD
03-03 22:11 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\casper\filesystem.squashfs
03-03 22:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:11 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:11 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:11 INFO   root: Running the CD menu...
03-03 22:11 DEBUG  WindowsFrontend: __init__...
03-03 22:11 DEBUG  WindowsFrontend: on_init...
03-03 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\translations, languages=['en_US', 'en']
03-03 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl41.tmp\translations, languages=['en_US', 'en']
03-03 22:11 DEBUG  root: application.quit
03-03 22:11 DEBUG  WindowsFrontend: frontend.quit
03-03 22:11 DEBUG  WindowsFrontend: frontend.on_quit
03-03 22:11 DEBUG  root: application.on_quit
03-03 22:11 INFO   root: sys.exit
03-03 22:12 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 22:12 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 22:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-03 22:12 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\data
03-03 22:12 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\bin\7z.exe
03-03 22:12 DEBUG  CommonBackend: Fetching basic info...
03-03 22:12 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:12 DEBUG  CommonBackend: platform=win32
03-03 22:12 DEBUG  CommonBackend: osname=nt
03-03 22:12 DEBUG  CommonBackend: language=en_US
03-03 22:12 DEBUG  CommonBackend: encoding=cp1252
03-03 22:12 DEBUG  WindowsBackend: arch=amd64
03-03 22:12 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\data\isolist.ini
03-03 22:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:12 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:12 DEBUG  WindowsBackend: Fetching host info...
03-03 22:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:12 DEBUG  WindowsBackend: windows version=xp
03-03 22:12 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:12 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:12 DEBUG  WindowsBackend: windows_build=2600
03-03 22:12 DEBUG  WindowsBackend: gmt=5
03-03 22:12 DEBUG  WindowsBackend: country=US
03-03 22:12 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:12 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:12 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:12 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:12 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:12 DEBUG  WindowsBackend: windows_language=English
03-03 22:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:12 DEBUG  WindowsBackend: bootloader=xp
03-03 22:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11274.75 mb free ntfs)
03-03 22:12 DEBUG  WindowsBackend: drive=Drive(C: hd 11274.75 mb free ntfs)
03-03 22:12 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:12 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:12 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:12 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:12 DEBUG  WindowsBackend: uninstaller_path=None
03-03 22:12 DEBUG  WindowsBackend: previous_target_dir=None
03-03 22:12 DEBUG  WindowsBackend: previous_distro_name=None
03-03 22:12 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:12 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:12 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 22:12 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 22:12 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:12 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:12 DEBUG  CommonBackend: Searching for local CDs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Ubuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Ubuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Kubuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Kubuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Kubuntu Netbook CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Xubuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Xubuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Mythbuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp is a valid Mythbuntu CD
03-03 22:12 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
03-03 22:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:12 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:12 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:12 INFO   root: Running the CD menu...
03-03 22:12 DEBUG  WindowsFrontend: __init__...
03-03 22:12 DEBUG  WindowsFrontend: on_init...
03-03 22:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\translations, languages=['en_US', 'en']
03-03 22:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl42.tmp\translations, languages=['en_US', 'en']
03-03 22:12 INFO   WindowsFrontend: Operation cancelled
03-03 22:12 DEBUG  WindowsFrontend: frontend.quit
03-03 22:12 DEBUG  WindowsFrontend: frontend.on_quit
03-03 22:12 DEBUG  root: application.on_quit
03-03 22:12 INFO   root: sys.exit
03-03 22:22 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 22:22 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 22:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-03 22:22 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\data
03-03 22:22 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\bin\7z.exe
03-03 22:22 DEBUG  CommonBackend: Fetching basic info...
03-03 22:22 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:22 DEBUG  CommonBackend: platform=win32
03-03 22:22 DEBUG  CommonBackend: osname=nt
03-03 22:22 DEBUG  CommonBackend: language=en_US
03-03 22:22 DEBUG  CommonBackend: encoding=cp1252
03-03 22:22 DEBUG  WindowsBackend: arch=amd64
03-03 22:22 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\data\isolist.ini
03-03 22:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:22 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:22 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:22 DEBUG  WindowsBackend: Fetching host info...
03-03 22:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:22 DEBUG  WindowsBackend: windows version=xp
03-03 22:22 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:22 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:22 DEBUG  WindowsBackend: windows_build=2600
03-03 22:22 DEBUG  WindowsBackend: gmt=5
03-03 22:22 DEBUG  WindowsBackend: country=US
03-03 22:22 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:22 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:22 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:22 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:22 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:22 DEBUG  WindowsBackend: windows_language=English
03-03 22:22 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:22 DEBUG  WindowsBackend: bootloader=xp
03-03 22:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11278.65625 mb free ntfs)
03-03 22:22 DEBUG  WindowsBackend: drive=Drive(C: hd 11278.65625 mb free ntfs)
03-03 22:22 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:22 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:22 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:22 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:22 DEBUG  WindowsBackend: uninstaller_path=None
03-03 22:22 DEBUG  WindowsBackend: previous_target_dir=None
03-03 22:22 DEBUG  WindowsBackend: previous_distro_name=None
03-03 22:22 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:22 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:22 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:22 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 22:22 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 22:22 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:22 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:22 DEBUG  CommonBackend: Searching for local CDs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Kubuntu Netbook CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Xubuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Xubuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Mythbuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp is a valid Mythbuntu CD
03-03 22:22 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\casper\filesystem.squashfs
03-03 22:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:22 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:22 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:22 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:22 INFO   root: Running the CD menu...
03-03 22:22 DEBUG  WindowsFrontend: __init__...
03-03 22:22 DEBUG  WindowsFrontend: on_init...
03-03 22:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
03-03 22:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
03-03 22:22 INFO   root: CD menu finished
03-03 22:22 INFO   root: Running the CD boot helper...
03-03 22:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
03-03 22:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
03-03 22:22 INFO   root: CD boot helper confirmed
03-03 22:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\translations, languages=['en_US', 'en']
03-03 22:22 DEBUG  TaskList: # Running tasklist...
03-03 22:22 DEBUG  TaskList: ## Running select_target_dir...
03-03 22:22 INFO   WindowsBackend: Installing into C:\ubuntu
03-03 22:22 DEBUG  TaskList: ## Finished select_target_dir
03-03 22:22 DEBUG  TaskList: ## Running create_dir_structure...
03-03 22:22 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-03 22:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-03 22:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-03 22:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-03 22:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-03 22:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-03 22:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-03 22:22 DEBUG  TaskList: ## Finished create_dir_structure
03-03 22:22 DEBUG  TaskList: ## Running uncompress_target_dir...
03-03 22:22 DEBUG  TaskList: ## Finished uncompress_target_dir
03-03 22:22 DEBUG  TaskList: ## Running create_uninstaller...
03-03 22:22 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-03 22:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-03 22:22 DEBUG  TaskList: ## Finished create_uninstaller
03-03 22:22 DEBUG  TaskList: ## Running copy_installation_files...
03-03 22:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-03 22:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\winboot -> C:\ubuntu\winboot
03-03 22:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl13.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-03 22:22 DEBUG  TaskList: ## Finished copy_installation_files
03-03 22:22 DEBUG  TaskList: ## Running use_cd...
03-03 22:22 DEBUG  TaskList: New task copy_file
03-03 22:22 DEBUG  TaskList: ### Running copy_file...
03-03 22:25 DEBUG  TaskList: ### Finished copy_file
03-03 22:25 DEBUG  TaskList: New task check_iso
03-03 22:25 DEBUG  TaskList: ### Running check_iso...
03-03 22:25 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-03 22:25 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-03 22:25 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-03 22:25 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:25 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-03 22:25 DEBUG  TaskList: New task get_metalink
03-03 22:25 DEBUG  TaskList: #### Running get_metalink...
03-03 22:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > C:\ubuntu\install
03-03 22:25 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
03-03 22:25 DEBUG  downloader: download finished (read 26651 bytes)
03-03 22:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
03-03 22:25 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-03 22:25 DEBUG  downloader: download finished (read 562 bytes)
03-03 22:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-03 22:25 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-03 22:25 DEBUG  downloader: download finished (read 189 bytes)
03-03 22:25 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-03 22:25 INFO   saplog: Checking block bindings..
03-03 22:25 INFO   saplog: Key verified successfully.
03-03 22:25 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-03 22:25 DEBUG  TaskList: #### Finished get_metalink
03-03 22:25 DEBUG  TaskList: New task get_file_md5
03-03 22:25 DEBUG  TaskList: #### Running get_file_md5...
03-03 22:25 DEBUG  TaskList: #### Finished get_file_md5
03-03 22:25 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dc51c1d7e3e173dcab4e0b9ad2be2bbf != 4b4e42cd2e7be5b74bad7ec00f4ad529)
None
03-03 22:25 DEBUG  TaskList: ### Finished check_iso
03-03 22:25 DEBUG  TaskList: ## Finished use_cd
03-03 22:25 DEBUG  TaskList: ## Running extract_kernel...
03-03 22:25 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-03 22:25 DEBUG  TaskList: # Cancelling tasklist
03-03 22:25 DEBUG  TaskList: # Finished tasklist
03-03 22:25 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-03 22:28 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 22:28 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 22:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Thirumalar\\My Documents\\Downloads\\wubi.exe"']
03-03 22:28 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\data
03-03 22:28 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\bin\7z.exe
03-03 22:28 DEBUG  CommonBackend: Fetching basic info...
03-03 22:28 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Thirumalar\My Documents\Downloads\wubi.exe
03-03 22:28 DEBUG  CommonBackend: platform=win32
03-03 22:28 DEBUG  CommonBackend: osname=nt
03-03 22:28 DEBUG  CommonBackend: language=en_US
03-03 22:28 DEBUG  CommonBackend: encoding=cp1252
03-03 22:28 DEBUG  WindowsBackend: arch=amd64
03-03 22:28 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\data\isolist.ini
03-03 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:28 DEBUG  WindowsBackend: Fetching host info...
03-03 22:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:28 DEBUG  WindowsBackend: windows version=xp
03-03 22:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:28 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:28 DEBUG  WindowsBackend: windows_build=2600
03-03 22:28 DEBUG  WindowsBackend: gmt=5
03-03 22:28 DEBUG  WindowsBackend: country=US
03-03 22:28 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:28 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:28 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:28 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:28 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:28 DEBUG  WindowsBackend: windows_language=English
03-03 22:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:28 DEBUG  WindowsBackend: bootloader=xp
03-03 22:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10582.1132813 mb free ntfs)
03-03 22:28 DEBUG  WindowsBackend: drive=Drive(C: hd 10582.1132813 mb free ntfs)
03-03 22:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:28 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:28 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:28 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-03 22:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-03 22:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-03 22:28 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:28 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:28 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 22:28 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 22:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:28 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:28 DEBUG  CommonBackend: Searching for local CDs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Kubuntu Netbook CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Xubuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Xubuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Mythbuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp is a valid Mythbuntu CD
03-03 22:28 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\casper\filesystem.squashfs
03-03 22:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:28 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:28 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:28 INFO   root: Running the CD menu...
03-03 22:28 DEBUG  WindowsFrontend: __init__...
03-03 22:28 DEBUG  WindowsFrontend: on_init...
03-03 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
03-03 22:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl17.tmp\translations, languages=['en_US', 'en']
03-03 22:28 INFO   WindowsFrontend: Operation cancelled
03-03 22:28 DEBUG  WindowsFrontend: frontend.quit
03-03 22:28 DEBUG  WindowsFrontend: frontend.on_quit
03-03 22:28 DEBUG  root: application.on_quit
03-03 22:28 INFO   root: sys.exit
03-03 22:29 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-03 22:29 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-03 22:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
03-03 22:29 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\data
03-03 22:29 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\bin\7z.exe
03-03 22:29 DEBUG  CommonBackend: Fetching basic info...
03-03 22:29 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:29 DEBUG  CommonBackend: platform=win32
03-03 22:29 DEBUG  CommonBackend: osname=nt
03-03 22:29 DEBUG  CommonBackend: language=en_US
03-03 22:29 DEBUG  CommonBackend: encoding=cp1252
03-03 22:29 DEBUG  WindowsBackend: arch=amd64
03-03 22:29 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
03-03 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:29 DEBUG  WindowsBackend: Fetching host info...
03-03 22:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:29 DEBUG  WindowsBackend: windows version=xp
03-03 22:29 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:29 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:29 DEBUG  WindowsBackend: windows_build=2600
03-03 22:29 DEBUG  WindowsBackend: gmt=5
03-03 22:29 DEBUG  WindowsBackend: country=US
03-03 22:29 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:29 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:29 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:29 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:29 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:29 DEBUG  WindowsBackend: windows_language=English
03-03 22:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:29 DEBUG  WindowsBackend: bootloader=xp
03-03 22:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10581.7617188 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(C: hd 10581.7617188 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-03 22:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-03 22:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-03 22:29 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:29 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:29 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-03 22:29 DEBUG  CommonBackend: locale=en_US.UTF-8
03-03 22:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:29 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:29 DEBUG  CommonBackend: Searching for local CDs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:29 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:29 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:29 INFO   root: Running the CD menu...
03-03 22:29 DEBUG  WindowsFrontend: __init__...
03-03 22:29 DEBUG  WindowsFrontend: on_init...
03-03 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
03-03 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
03-03 22:29 INFO   root: CD menu finished
03-03 22:29 INFO   root: Already installed, running the uninstaller...
03-03 22:29 INFO   root: Running the uninstaller...
03-03 22:29 INFO   CommonBackend: This is the uninstaller running
03-03 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
03-03 22:29 INFO   root: Received settings
03-03 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
03-03 22:29 DEBUG  TaskList: # Running tasklist...
03-03 22:29 DEBUG  TaskList: ## Running Backup ISO...
03-03 22:29 DEBUG  TaskList: ## Finished Backup ISO
03-03 22:29 DEBUG  TaskList: ## Running Remove bootloader entry...
03-03 22:29 ERROR  WindowsBackend: Cannot find bcdedit
03-03 22:29 DEBUG  WindowsBackend: undo_bootini C:
03-03 22:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 10581.7617188 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: undo_bootini E:
03-03 22:29 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: undo_bootini F:
03-03 22:29 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: undo_bootini G:
03-03 22:29 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:29 DEBUG  TaskList: ## Finished Remove bootloader entry
03-03 22:29 DEBUG  TaskList: ## Running Remove target dir...
03-03 22:29 DEBUG  CommonBackend: Deleting C:\ubuntu
03-03 22:29 DEBUG  TaskList: ## Finished Remove target dir
03-03 22:29 DEBUG  TaskList: ## Running Remove registry key...
03-03 22:29 DEBUG  TaskList: ## Finished Remove registry key
03-03 22:29 DEBUG  TaskList: # Finished tasklist
03-03 22:29 INFO   root: Almost finished uninstalling
03-03 22:29 INFO   root: Finished uninstallation
03-03 22:29 DEBUG  CommonBackend: Fetching basic info...
03-03 22:29 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-03 22:29 DEBUG  CommonBackend: platform=win32
03-03 22:29 DEBUG  CommonBackend: osname=nt
03-03 22:29 DEBUG  WindowsBackend: arch=amd64
03-03 22:29 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
03-03 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-03 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-03 22:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-03 22:29 DEBUG  WindowsBackend: Fetching host info...
03-03 22:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-03 22:29 DEBUG  WindowsBackend: windows version=xp
03-03 22:29 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-03 22:29 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-03 22:29 DEBUG  WindowsBackend: windows_build=2600
03-03 22:29 DEBUG  WindowsBackend: gmt=5
03-03 22:29 DEBUG  WindowsBackend: country=US
03-03 22:29 DEBUG  WindowsBackend: timezone=America/New_York
03-03 22:29 DEBUG  WindowsBackend: windows_username=Thirumalar
03-03 22:29 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-03 22:29 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-03 22:29 DEBUG  WindowsBackend: windows_language_code=1033
03-03 22:29 DEBUG  WindowsBackend: windows_language=English
03-03 22:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-03 22:29 DEBUG  WindowsBackend: bootloader=xp
03-03 22:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11274.109375 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(C: hd 11274.109375 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.34375 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6875 mb free ntfs)
03-03 22:29 DEBUG  WindowsBackend: uninstaller_path=None
03-03 22:29 DEBUG  WindowsBackend: previous_target_dir=None
03-03 22:29 DEBUG  WindowsBackend: previous_distro_name=None
03-03 22:29 DEBUG  WindowsBackend: keyboard_id=67699721
03-03 22:29 DEBUG  WindowsBackend: keyboard_layout=us
03-03 22:29 DEBUG  WindowsBackend: keyboard_variant=
03-03 22:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-03 22:29 DEBUG  CommonBackend: Searching ISOs on USB devices
03-03 22:29 DEBUG  CommonBackend: Searching for local CDs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook Remix CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
03-03 22:29 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
03-03 22:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-03 22:29 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-03 22:29 INFO   root: Running the installer...
03-03 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
03-03 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
03-03 22:30 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=thirumalar
03-03 22:30 INFO   root: Received settings
03-03 22:30 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
03-03 22:30 DEBUG  TaskList: # Running tasklist...
03-03 22:30 DEBUG  TaskList: ## Running select_target_dir...
03-03 22:30 INFO   WindowsBackend: Installing into E:\ubuntu
03-03 22:30 DEBUG  TaskList: ## Finished select_target_dir
03-03 22:30 DEBUG  TaskList: ## Running create_dir_structure...
03-03 22:30 DEBUG  CommonBackend: Creating dir E:\ubuntu
03-03 22:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
03-03 22:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
03-03 22:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
03-03 22:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
03-03 22:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
03-03 22:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
03-03 22:30 DEBUG  TaskList: ## Finished create_dir_structure
03-03 22:30 DEBUG  TaskList: ## Running uncompress_target_dir...
03-03 22:30 DEBUG  TaskList: ## Finished uncompress_target_dir
03-03 22:30 DEBUG  TaskList: ## Running create_uninstaller...
03-03 22:30 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-03 22:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-03 22:30 DEBUG  TaskList: ## Finished create_uninstaller
03-03 22:30 DEBUG  TaskList: ## Running copy_installation_files...
03-03 22:30 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
03-03 22:30 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\winboot -> E:\ubuntu\winboot
03-03 22:30 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl18.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
03-03 22:30 DEBUG  TaskList: ## Finished copy_installation_files
03-03 22:30 DEBUG  TaskList: ## Running get_iso...
03-03 22:30 DEBUG  TaskList: New task copy_file
03-03 22:30 DEBUG  TaskList: ### Running copy_file...
03-03 22:37 DEBUG  TaskList: ### Finished copy_file
03-03 22:37 DEBUG  TaskList: New task check_iso
03-03 22:37 DEBUG  TaskList: ### Running check_iso...
03-03 22:37 DEBUG  CommonBackend: Checking E:\ubuntu\install\installation.iso
03-03 22:37 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\installation.iso
03-03 22:37 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\installation.iso
03-03 22:37 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-03 22:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-03 22:37 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu\install\installation.iso
03-03 22:37 DEBUG  TaskList: New task get_metalink
03-03 22:37 DEBUG  TaskList: #### Running get_metalink...
03-03 22:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > E:\ubuntu\install
03-03 22:37 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
03-03 22:37 DEBUG  downloader: download finished (read 26651 bytes)
03-03 22:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > E:\ubuntu\install
03-03 22:37 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-03 22:37 DEBUG  downloader: download finished (read 562 bytes)
03-03 22:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > E:\ubuntu\install
03-03 22:37 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-03 22:37 DEBUG  downloader: download finished (read 189 bytes)
03-03 22:37 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-03 22:37 INFO   saplog: Checking block bindings..
03-03 22:37 INFO   saplog: Key verified successfully.
03-03 22:37 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-03 22:37 DEBUG  TaskList: #### Finished get_metalink
03-03 22:37 DEBUG  TaskList: New task get_file_md5
03-03 22:37 DEBUG  TaskList: #### Running get_file_md5...
03-03 22:37 DEBUG  TaskList: #### Finished get_file_md5
03-03 22:37 ERROR  CommonBackend: Invalid md5 for ISO E:\ubuntu\install\installation.iso (dc51c1d7e3e173dcab4e0b9ad2be2bbf != 4b4e42cd2e7be5b74bad7ec00f4ad529)
None
03-03 22:37 DEBUG  TaskList: ### Finished check_iso
03-03 22:37 DEBUG  CommonBackend: Searching for local ISO
03-03 22:37 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-03 22:37 DEBUG  TaskList: New task download
03-03 22:37 DEBUG  TaskList: ### Running download...
03-03 22:37 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
03-04 05:34 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-04 05:34 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-04 05:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Thirumalar\\My Documents\\Downloads\\wubi.exe"']
03-04 05:34 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\data
03-04 05:34 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\bin\7z.exe
03-04 05:34 DEBUG  CommonBackend: Fetching basic info...
03-04 05:34 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Thirumalar\My Documents\Downloads\wubi.exe
03-04 05:34 DEBUG  CommonBackend: platform=win32
03-04 05:34 DEBUG  CommonBackend: osname=nt
03-04 05:34 DEBUG  CommonBackend: language=en_US
03-04 05:34 DEBUG  CommonBackend: encoding=cp1252
03-04 05:34 DEBUG  WindowsBackend: arch=amd64
03-04 05:34 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\data\isolist.ini
03-04 05:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-04 05:34 DEBUG  WindowsBackend: Fetching host info...
03-04 05:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 05:34 DEBUG  WindowsBackend: windows version=xp
03-04 05:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-04 05:34 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-04 05:34 DEBUG  WindowsBackend: windows_build=2600
03-04 05:34 DEBUG  WindowsBackend: gmt=5
03-04 05:34 DEBUG  WindowsBackend: country=US
03-04 05:34 DEBUG  WindowsBackend: timezone=America/New_York
03-04 05:34 DEBUG  WindowsBackend: windows_username=Thirumalar
03-04 05:34 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-04 05:34 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-04 05:34 DEBUG  WindowsBackend: windows_language_code=1033
03-04 05:34 DEBUG  WindowsBackend: windows_language=English
03-04 05:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-04 05:34 DEBUG  WindowsBackend: bootloader=xp
03-04 05:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11075.1054688 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(C: hd 11075.1054688 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(E: hd 158783.953125 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.328125 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6640625 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
03-04 05:34 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
03-04 05:34 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 05:34 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 05:34 DEBUG  WindowsBackend: keyboard_layout=us
03-04 05:34 DEBUG  WindowsBackend: keyboard_variant=
03-04 05:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 05:34 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 05:34 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 05:34 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 05:34 DEBUG  CommonBackend: Searching for local CDs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 INFO   root: Already installed, running the uninstaller...
03-04 05:34 INFO   root: Running the uninstaller...
03-04 05:34 INFO   CommonBackend: This is the uninstaller running
03-04 05:34 DEBUG  WindowsFrontend: __init__...
03-04 05:34 DEBUG  WindowsFrontend: on_init...
03-04 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
03-04 05:34 INFO   root: Received settings
03-04 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
03-04 05:34 DEBUG  TaskList: # Running tasklist...
03-04 05:34 DEBUG  TaskList: ## Running Backup ISO...
03-04 05:34 DEBUG  TaskList: ## Finished Backup ISO
03-04 05:34 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 05:34 ERROR  WindowsBackend: Cannot find bcdedit
03-04 05:34 DEBUG  WindowsBackend: undo_bootini C:
03-04 05:34 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 11075.1054688 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: undo_bootini E:
03-04 05:34 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 158783.953125 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: undo_bootini F:
03-04 05:34 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 16310.328125 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: undo_bootini G:
03-04 05:34 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 86624.6640625 mb free ntfs)
03-04 05:34 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 05:34 DEBUG  TaskList: ## Running Remove target dir...
03-04 05:34 DEBUG  CommonBackend: Deleting E:\ubuntu
03-04 05:34 DEBUG  TaskList: ## Finished Remove target dir
03-04 05:34 DEBUG  TaskList: ## Running Remove registry key...
03-04 05:34 DEBUG  TaskList: ## Finished Remove registry key
03-04 05:34 DEBUG  TaskList: # Finished tasklist
03-04 05:34 INFO   root: Almost finished uninstalling
03-04 05:34 INFO   root: Finished uninstallation
03-04 05:34 DEBUG  CommonBackend: Fetching basic info...
03-04 05:34 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Thirumalar\My Documents\Downloads\wubi.exe
03-04 05:34 DEBUG  CommonBackend: platform=win32
03-04 05:34 DEBUG  CommonBackend: osname=nt
03-04 05:34 DEBUG  WindowsBackend: arch=amd64
03-04 05:34 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\data\isolist.ini
03-04 05:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 05:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 05:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-04 05:34 DEBUG  WindowsBackend: Fetching host info...
03-04 05:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 05:34 DEBUG  WindowsBackend: windows version=xp
03-04 05:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-04 05:34 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-04 05:34 DEBUG  WindowsBackend: windows_build=2600
03-04 05:34 DEBUG  WindowsBackend: gmt=5
03-04 05:34 DEBUG  WindowsBackend: country=US
03-04 05:34 DEBUG  WindowsBackend: timezone=America/New_York
03-04 05:34 DEBUG  WindowsBackend: windows_username=Thirumalar
03-04 05:34 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-04 05:34 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-04 05:34 DEBUG  WindowsBackend: windows_language_code=1033
03-04 05:34 DEBUG  WindowsBackend: windows_language=English
03-04 05:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-04 05:34 DEBUG  WindowsBackend: bootloader=xp
03-04 05:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11074.8359375 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(C: hd 11074.8359375 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(E: hd 159896.863281 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.328125 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6640625 mb free ntfs)
03-04 05:34 DEBUG  WindowsBackend: uninstaller_path=None
03-04 05:34 DEBUG  WindowsBackend: previous_target_dir=None
03-04 05:34 DEBUG  WindowsBackend: previous_distro_name=None
03-04 05:34 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 05:34 DEBUG  WindowsBackend: keyboard_layout=us
03-04 05:34 DEBUG  WindowsBackend: keyboard_variant=
03-04 05:34 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 05:34 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 05:34 DEBUG  CommonBackend: Searching for local CDs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-04 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:34 INFO   root: Running the installer...
03-04 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
03-04 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
03-04 05:35 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=thirumalar
03-04 05:35 INFO   root: Received settings
03-04 05:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
03-04 05:35 DEBUG  TaskList: # Running tasklist...
03-04 05:35 DEBUG  TaskList: ## Running select_target_dir...
03-04 05:35 INFO   WindowsBackend: Installing into E:\ubuntu
03-04 05:35 DEBUG  TaskList: ## Finished select_target_dir
03-04 05:35 DEBUG  TaskList: ## Running create_dir_structure...
03-04 05:35 DEBUG  CommonBackend: Creating dir E:\ubuntu
03-04 05:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
03-04 05:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
03-04 05:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
03-04 05:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
03-04 05:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
03-04 05:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
03-04 05:35 DEBUG  TaskList: ## Finished create_dir_structure
03-04 05:35 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 05:35 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 05:35 DEBUG  TaskList: ## Running create_uninstaller...
03-04 05:35 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Thirumalar\My Documents\Downloads\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 05:35 DEBUG  TaskList: ## Finished create_uninstaller
03-04 05:35 DEBUG  TaskList: ## Running copy_installation_files...
03-04 05:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
03-04 05:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\winboot -> E:\ubuntu\winboot
03-04 05:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
03-04 05:35 DEBUG  TaskList: ## Finished copy_installation_files
03-04 05:35 DEBUG  TaskList: ## Running get_iso...
03-04 05:35 DEBUG  CommonBackend: Searching for local CD
03-04 05:35 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
03-04 05:35 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
03-04 05:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-04 05:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-04 05:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-04 05:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-04 05:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:35 DEBUG  CommonBackend: Searching for local ISO
03-04 05:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-04 05:35 DEBUG  TaskList: New task get_metalink
03-04 05:35 DEBUG  TaskList: ### Running get_metalink...
03-04 05:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > E:\ubuntu\install
03-04 05:35 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
03-04 05:35 DEBUG  downloader: download finished (read 26651 bytes)
03-04 05:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > E:\ubuntu\install
03-04 05:35 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-04 05:35 DEBUG  downloader: download finished (read 562 bytes)
03-04 05:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > E:\ubuntu\install
03-04 05:35 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-04 05:35 DEBUG  downloader: download finished (read 189 bytes)
03-04 05:35 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-04 05:35 INFO   saplog: Checking block bindings..
03-04 05:35 INFO   saplog: Key verified successfully.
03-04 05:35 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-04 05:35 DEBUG  TaskList: ### Finished get_metalink
03-04 05:35 DEBUG  TaskList: New task download
03-04 05:35 DEBUG  TaskList: ### Running download...
03-04 05:35 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
03-04 05:42 INFO   WindowsFrontend: Operation cancelled
03-04 05:42 DEBUG  WindowsFrontend: frontend.quit
03-04 05:42 DEBUG  WindowsFrontend: frontend.on_quit
03-04 05:42 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-04 05:42 DEBUG  TaskList: # Cancelling tasklist
03-04 05:42 DEBUG  TaskList: ### Finished download
03-04 05:42 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-04 05:42 DEBUG  root: application.on_quit
03-04 05:42 DEBUG  root: Forceful exit
03-04 05:42 INFO   root: sys.exit
03-04 05:43 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-04 05:43 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-04 05:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 05:43 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\data
03-04 05:43 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\bin\7z.exe
03-04 05:43 DEBUG  CommonBackend: Fetching basic info...
03-04 05:43 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 05:43 DEBUG  CommonBackend: platform=win32
03-04 05:43 DEBUG  CommonBackend: osname=nt
03-04 05:43 DEBUG  CommonBackend: language=en_US
03-04 05:43 DEBUG  CommonBackend: encoding=cp1252
03-04 05:43 DEBUG  WindowsBackend: arch=amd64
03-04 05:43 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\data\isolist.ini
03-04 05:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 05:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 05:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 05:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 05:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 05:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 05:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 05:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 05:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 05:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-04 05:43 DEBUG  WindowsBackend: Fetching host info...
03-04 05:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 05:43 DEBUG  WindowsBackend: windows version=xp
03-04 05:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-04 05:43 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-04 05:43 DEBUG  WindowsBackend: windows_build=2600
03-04 05:43 DEBUG  WindowsBackend: gmt=5
03-04 05:43 DEBUG  WindowsBackend: country=US
03-04 05:43 DEBUG  WindowsBackend: timezone=America/New_York
03-04 05:43 DEBUG  WindowsBackend: windows_username=Thirumalar
03-04 05:43 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-04 05:43 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-04 05:43 DEBUG  WindowsBackend: windows_language_code=1033
03-04 05:43 DEBUG  WindowsBackend: windows_language=English
03-04 05:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-04 05:43 DEBUG  WindowsBackend: bootloader=xp
03-04 05:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11071.375 mb free ntfs)
03-04 05:43 DEBUG  WindowsBackend: drive=Drive(C: hd 11071.375 mb free ntfs)
03-04 05:43 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 05:43 DEBUG  WindowsBackend: drive=Drive(E: hd 159883.804688 mb free ntfs)
03-04 05:43 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.328125 mb free ntfs)
03-04 05:43 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6640625 mb free ntfs)
03-04 05:43 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
03-04 05:43 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
03-04 05:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 05:43 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 05:43 DEBUG  WindowsBackend: keyboard_layout=us
03-04 05:43 DEBUG  WindowsBackend: keyboard_variant=
03-04 05:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 05:43 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 05:43 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 05:43 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 05:43 DEBUG  CommonBackend: Searching for local CDs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Ubuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Ubuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Ubuntu Netbook Remix CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Kubuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Kubuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Kubuntu Netbook CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Xubuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Xubuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Mythbuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp is a valid Mythbuntu CD
03-04 05:43 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-04 05:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:43 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-04 05:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-04 05:43 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 05:43 INFO   root: Running the CD menu...
03-04 05:43 DEBUG  WindowsFrontend: __init__...
03-04 05:43 DEBUG  WindowsFrontend: on_init...
03-04 05:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\translations, languages=['en_US', 'en']
03-04 05:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\translations, languages=['en_US', 'en']
03-04 05:44 INFO   root: CD menu finished
03-04 05:44 INFO   root: Running the CD menu...
03-04 05:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\translations, languages=['en_US', 'en']
03-04 05:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1F.tmp\translations, languages=['en_US', 'en']
03-04 05:44 INFO   WindowsFrontend: Operation cancelled
03-04 05:44 DEBUG  WindowsFrontend: frontend.quit
03-04 05:44 DEBUG  WindowsFrontend: frontend.on_quit
03-04 05:44 DEBUG  root: application.on_quit
03-04 05:44 INFO   root: sys.exit
03-04 05:50 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-04 05:50 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-04 05:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
03-04 05:50 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\data
03-04 05:50 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\bin\7z.exe
03-04 05:50 DEBUG  CommonBackend: Fetching basic info...
03-04 05:50 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
03-04 05:50 DEBUG  CommonBackend: platform=win32
03-04 05:50 DEBUG  CommonBackend: osname=nt
03-04 05:50 DEBUG  CommonBackend: language=en_US
03-04 05:50 DEBUG  CommonBackend: encoding=cp1252
03-04 05:50 DEBUG  WindowsBackend: arch=amd64
03-04 05:50 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\data\isolist.ini
03-04 05:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 05:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 05:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 05:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 05:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 05:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 05:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 05:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 05:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 05:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-04 05:50 DEBUG  WindowsBackend: Fetching host info...
03-04 05:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 05:50 DEBUG  WindowsBackend: windows version=xp
03-04 05:50 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-04 05:50 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-04 05:50 DEBUG  WindowsBackend: windows_build=2600
03-04 05:50 DEBUG  WindowsBackend: gmt=5
03-04 05:50 DEBUG  WindowsBackend: country=US
03-04 05:50 DEBUG  WindowsBackend: timezone=America/New_York
03-04 05:50 DEBUG  WindowsBackend: windows_username=Thirumalar
03-04 05:50 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-04 05:50 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-04 05:50 DEBUG  WindowsBackend: windows_language_code=1033
03-04 05:50 DEBUG  WindowsBackend: windows_language=English
03-04 05:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-04 05:50 DEBUG  WindowsBackend: bootloader=xp
03-04 05:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11080.5078125 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: drive=Drive(C: hd 11080.5078125 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 05:50 DEBUG  WindowsBackend: drive=Drive(E: hd 159885.550781 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3398438 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: drive=Drive(G: hd 86624.6757813 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
03-04 05:50 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
03-04 05:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 05:50 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 05:50 DEBUG  WindowsBackend: keyboard_layout=us
03-04 05:50 DEBUG  WindowsBackend: keyboard_variant=
03-04 05:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 05:50 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 05:50 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 05:50 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 05:50 DEBUG  CommonBackend: Searching for local CDs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu Netbook Remix CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu Netbook CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain D:\casper\initrd.lz
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-04 05:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-04 05:50 INFO   root: Running the uninstaller...
03-04 05:50 INFO   CommonBackend: This is the uninstaller running
03-04 05:50 DEBUG  WindowsFrontend: __init__...
03-04 05:50 DEBUG  WindowsFrontend: on_init...
03-04 05:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
03-04 05:50 INFO   root: Received settings
03-04 05:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
03-04 05:50 DEBUG  TaskList: # Running tasklist...
03-04 05:50 DEBUG  TaskList: ## Running Backup ISO...
03-04 05:50 DEBUG  TaskList: ## Finished Backup ISO
03-04 05:50 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 05:50 ERROR  WindowsBackend: Cannot find bcdedit
03-04 05:50 DEBUG  WindowsBackend: undo_bootini C:
03-04 05:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 11080.5078125 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: undo_bootini E:
03-04 05:50 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 159885.550781 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: undo_bootini F:
03-04 05:50 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 16310.3398438 mb free ntfs)
03-04 05:50 DEBUG  WindowsBackend: undo_bootini G:
03-04 05:50 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 86624.6757813 mb free ntfs)
03-04 05:50 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 05:50 DEBUG  TaskList: ## Running Remove target dir...
03-04 05:50 DEBUG  CommonBackend: Deleting E:\ubuntu
03-04 05:50 DEBUG  TaskList: ## Finished Remove target dir
03-04 05:50 DEBUG  TaskList: ## Running Remove registry key...
03-04 05:50 DEBUG  TaskList: ## Finished Remove registry key
03-04 05:50 DEBUG  TaskList: # Finished tasklist
03-04 05:50 INFO   root: Almost finished uninstalling
03-04 05:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
03-04 05:50 INFO   root: Finished uninstallation
03-04 05:50 DEBUG  root: application.quit
03-04 05:50 DEBUG  WindowsFrontend: frontend.quit
03-04 05:50 DEBUG  WindowsFrontend: frontend.on_quit
03-04 05:50 DEBUG  root: application.on_quit
03-04 05:50 INFO   root: sys.exit
03-04 06:24 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-04 06:24 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-04 06:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 06:24 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\data
03-04 06:24 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\bin\7z.exe
03-04 06:24 DEBUG  CommonBackend: Fetching basic info...
03-04 06:24 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 06:24 DEBUG  CommonBackend: platform=win32
03-04 06:24 DEBUG  CommonBackend: osname=nt
03-04 06:24 DEBUG  CommonBackend: language=en_US
03-04 06:24 DEBUG  CommonBackend: encoding=cp1252
03-04 06:24 DEBUG  WindowsBackend: arch=amd64
03-04 06:24 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\data\isolist.ini
03-04 06:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 06:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 06:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 06:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 06:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 06:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 06:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 06:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 06:24 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 06:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-04 06:24 DEBUG  WindowsBackend: Fetching host info...
03-04 06:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 06:24 DEBUG  WindowsBackend: windows version=xp
03-04 06:24 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-04 06:24 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-04 06:24 DEBUG  WindowsBackend: windows_build=2600
03-04 06:24 DEBUG  WindowsBackend: gmt=5
03-04 06:24 DEBUG  WindowsBackend: country=US
03-04 06:24 DEBUG  WindowsBackend: timezone=America/New_York
03-04 06:24 DEBUG  WindowsBackend: windows_username=Thirumalar
03-04 06:24 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-04 06:24 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-04 06:24 DEBUG  WindowsBackend: windows_language_code=1033
03-04 06:24 DEBUG  WindowsBackend: windows_language=English
03-04 06:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-04 06:24 DEBUG  WindowsBackend: bootloader=xp
03-04 06:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11078.2148438 mb free ntfs)
03-04 06:24 DEBUG  WindowsBackend: drive=Drive(C: hd 11078.2148438 mb free ntfs)
03-04 06:24 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 06:24 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-04 06:24 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3398438 mb free ntfs)
03-04 06:24 DEBUG  WindowsBackend: drive=Drive(G: hd 86612.9140625 mb free ntfs)
03-04 06:24 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\Uninstall-Ubuntu.exe
03-04 06:24 DEBUG  WindowsBackend: previous_target_dir=None
03-04 06:24 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 06:24 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 06:24 DEBUG  WindowsBackend: keyboard_layout=us
03-04 06:24 DEBUG  WindowsBackend: keyboard_variant=
03-04 06:24 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 06:24 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 06:24 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 06:24 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 06:24 DEBUG  CommonBackend: Searching for local CDs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu Netbook Remix CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu Netbook CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Xubuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Xubuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Mythbuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp is a valid Mythbuntu CD
03-04 06:24 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
03-04 06:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 06:24 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-04 06:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-04 06:24 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 06:24 INFO   root: Running the CD menu...
03-04 06:24 DEBUG  WindowsFrontend: __init__...
03-04 06:24 DEBUG  WindowsFrontend: on_init...
03-04 06:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
03-04 06:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
03-04 06:24 INFO   root: CD menu finished
03-04 06:24 INFO   root: Running the CD boot helper...
03-04 06:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
03-04 06:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
03-04 06:24 INFO   root: CD boot helper confirmed
03-04 06:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
03-04 06:24 DEBUG  TaskList: # Running tasklist...
03-04 06:24 DEBUG  TaskList: ## Running select_target_dir...
03-04 06:24 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 06:24 DEBUG  TaskList: ## Finished select_target_dir
03-04 06:24 DEBUG  TaskList: ## Running create_dir_structure...
03-04 06:24 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 06:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 06:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 06:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 06:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 06:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 06:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 06:24 DEBUG  TaskList: ## Finished create_dir_structure
03-04 06:24 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 06:24 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 06:24 DEBUG  TaskList: ## Running create_uninstaller...
03-04 06:24 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 06:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 06:24 DEBUG  TaskList: ## Finished create_uninstaller
03-04 06:24 DEBUG  TaskList: ## Running copy_installation_files...
03-04 06:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 06:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\winboot -> C:\ubuntu\winboot
03-04 06:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl25.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 06:24 DEBUG  TaskList: ## Finished copy_installation_files
03-04 06:24 DEBUG  TaskList: ## Running use_cd...
03-04 06:24 DEBUG  TaskList: New task copy_file
03-04 06:24 DEBUG  TaskList: ### Running copy_file...
03-04 06:26 DEBUG  TaskList: ### Finished copy_file
03-04 06:26 DEBUG  TaskList: New task check_iso
03-04 06:26 DEBUG  TaskList: ### Running check_iso...
03-04 06:26 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-04 06:26 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-04 06:26 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-04 06:26 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-04 06:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-04 06:26 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-04 06:26 DEBUG  TaskList: New task get_metalink
03-04 06:26 DEBUG  TaskList: #### Running get_metalink...
03-04 06:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > C:\ubuntu\install
03-04 06:26 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
03-04 06:26 DEBUG  downloader: download finished (read 26651 bytes)
03-04 06:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
03-04 06:26 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-04 06:26 DEBUG  downloader: download finished (read 562 bytes)
03-04 06:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-04 06:26 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-04 06:26 DEBUG  downloader: download finished (read 189 bytes)
03-04 06:26 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-04 06:26 INFO   saplog: Checking block bindings..
03-04 06:26 INFO   saplog: Key verified successfully.
03-04 06:26 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-04 06:26 DEBUG  TaskList: #### Finished get_metalink
03-04 06:26 DEBUG  TaskList: New task get_file_md5
03-04 06:26 DEBUG  TaskList: #### Running get_file_md5...
03-04 06:26 DEBUG  TaskList: #### Finished get_file_md5
03-04 06:26 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dc51c1d7e3e173dcab4e0b9ad2be2bbf != 4b4e42cd2e7be5b74bad7ec00f4ad529)
None
03-04 06:26 DEBUG  TaskList: ### Finished check_iso
03-04 06:26 DEBUG  TaskList: ## Finished use_cd
03-04 06:26 DEBUG  TaskList: ## Running extract_kernel...
03-04 06:26 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-04 06:26 DEBUG  TaskList: # Cancelling tasklist
03-04 06:26 DEBUG  TaskList: # Finished tasklist
03-04 06:26 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-04 06:27 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-04 06:27 DEBUG  root: Logfile is c:\docume~1\thirum~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-04 06:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 06:27 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\data
03-04 06:27 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\bin\7z.exe
03-04 06:27 DEBUG  CommonBackend: Fetching basic info...
03-04 06:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 06:27 DEBUG  CommonBackend: platform=win32
03-04 06:27 DEBUG  CommonBackend: osname=nt
03-04 06:27 DEBUG  CommonBackend: language=en_US
03-04 06:27 DEBUG  CommonBackend: encoding=cp1252
03-04 06:27 DEBUG  WindowsBackend: arch=amd64
03-04 06:27 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\data\isolist.ini
03-04 06:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-04 06:27 DEBUG  WindowsBackend: Fetching host info...
03-04 06:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 06:27 DEBUG  WindowsBackend: windows version=xp
03-04 06:27 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-04 06:27 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-04 06:27 DEBUG  WindowsBackend: windows_build=2600
03-04 06:27 DEBUG  WindowsBackend: gmt=5
03-04 06:27 DEBUG  WindowsBackend: country=US
03-04 06:27 DEBUG  WindowsBackend: timezone=America/New_York
03-04 06:27 DEBUG  WindowsBackend: windows_username=Thirumalar
03-04 06:27 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-04 06:27 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-04 06:27 DEBUG  WindowsBackend: windows_language_code=1033
03-04 06:27 DEBUG  WindowsBackend: windows_language=English
03-04 06:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-04 06:27 DEBUG  WindowsBackend: bootloader=xp
03-04 06:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10385.3632813 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(C: hd 10385.3632813 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3398438 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(G: hd 86612.9140625 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 06:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 06:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 06:27 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 06:27 DEBUG  WindowsBackend: keyboard_layout=us
03-04 06:27 DEBUG  WindowsBackend: keyboard_variant=
03-04 06:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 06:27 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 06:27 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 06:27 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 06:27 DEBUG  CommonBackend: Searching for local CDs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu Netbook Remix CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu Netbook CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Xubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Xubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Mythbuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Mythbuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 06:27 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-04 06:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-04 06:27 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 06:27 INFO   root: Running the CD menu...
03-04 06:27 DEBUG  WindowsFrontend: __init__...
03-04 06:27 DEBUG  WindowsFrontend: on_init...
03-04 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\translations, languages=['en_US', 'en']
03-04 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\translations, languages=['en_US', 'en']
03-04 06:27 INFO   root: CD menu finished
03-04 06:27 INFO   root: Already installed, running the uninstaller...
03-04 06:27 INFO   root: Running the uninstaller...
03-04 06:27 INFO   CommonBackend: This is the uninstaller running
03-04 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\translations, languages=['en_US', 'en']
03-04 06:27 INFO   root: Received settings
03-04 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\translations, languages=['en_US', 'en']
03-04 06:27 DEBUG  TaskList: # Running tasklist...
03-04 06:27 DEBUG  TaskList: ## Running Backup ISO...
03-04 06:27 DEBUG  TaskList: ## Finished Backup ISO
03-04 06:27 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 06:27 ERROR  WindowsBackend: Cannot find bcdedit
03-04 06:27 DEBUG  WindowsBackend: undo_bootini C:
03-04 06:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 10385.3632813 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: undo_bootini E:
03-04 06:27 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 159930.652344 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: undo_bootini F:
03-04 06:27 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 16310.3398438 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: undo_bootini G:
03-04 06:27 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 86612.9140625 mb free ntfs)
03-04 06:27 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 06:27 DEBUG  TaskList: ## Running Remove target dir...
03-04 06:27 DEBUG  CommonBackend: Deleting C:\ubuntu
03-04 06:27 DEBUG  TaskList: ## Finished Remove target dir
03-04 06:27 DEBUG  TaskList: ## Running Remove registry key...
03-04 06:27 DEBUG  TaskList: ## Finished Remove registry key
03-04 06:27 DEBUG  TaskList: # Finished tasklist
03-04 06:27 INFO   root: Almost finished uninstalling
03-04 06:27 INFO   root: Finished uninstallation
03-04 06:27 DEBUG  CommonBackend: Fetching basic info...
03-04 06:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 06:27 DEBUG  CommonBackend: platform=win32
03-04 06:27 DEBUG  CommonBackend: osname=nt
03-04 06:27 DEBUG  WindowsBackend: arch=amd64
03-04 06:27 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\data\isolist.ini
03-04 06:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 06:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 06:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-04 06:27 DEBUG  WindowsBackend: Fetching host info...
03-04 06:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 06:27 DEBUG  WindowsBackend: windows version=xp
03-04 06:27 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-04 06:27 DEBUG  WindowsBackend: windows_sp=Service Pack 2
03-04 06:27 DEBUG  WindowsBackend: windows_build=2600
03-04 06:27 DEBUG  WindowsBackend: gmt=5
03-04 06:27 DEBUG  WindowsBackend: country=US
03-04 06:27 DEBUG  WindowsBackend: timezone=America/New_York
03-04 06:27 DEBUG  WindowsBackend: windows_username=Thirumalar
03-04 06:27 DEBUG  WindowsBackend: user_full_name=Thirumalar
03-04 06:27 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Thirumalar
03-04 06:27 DEBUG  WindowsBackend: windows_language_code=1033
03-04 06:27 DEBUG  WindowsBackend: windows_language=English
03-04 06:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
03-04 06:27 DEBUG  WindowsBackend: bootloader=xp
03-04 06:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11077.4179688 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(C: hd 11077.4179688 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(E: hd 159930.652344 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(F: hd 16310.3398438 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: drive=Drive(G: hd 86613.1054688 mb free ntfs)
03-04 06:27 DEBUG  WindowsBackend: uninstaller_path=None
03-04 06:27 DEBUG  WindowsBackend: previous_target_dir=None
03-04 06:27 DEBUG  WindowsBackend: previous_distro_name=None
03-04 06:27 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 06:27 DEBUG  WindowsBackend: keyboard_layout=us
03-04 06:27 DEBUG  WindowsBackend: keyboard_variant=
03-04 06:27 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 06:27 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 06:27 DEBUG  CommonBackend: Searching for local CDs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu Netbook Remix CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu Netbook CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Xubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Xubuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Mythbuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp is a valid Mythbuntu CD
03-04 06:27 DEBUG  Distro:     does not contain C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
03-04 06:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 06:27 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 06:27 INFO   root: Running the CD boot helper...
03-04 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\translations, languages=['en_US', 'en']
03-04 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\translations, languages=['en_US', 'en']
03-04 06:27 INFO   root: CD boot helper confirmed
03-04 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\translations, languages=['en_US', 'en']
03-04 06:27 DEBUG  TaskList: # Running tasklist...
03-04 06:27 DEBUG  TaskList: ## Running select_target_dir...
03-04 06:27 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 06:27 DEBUG  TaskList: ## Finished select_target_dir
03-04 06:27 DEBUG  TaskList: ## Running create_dir_structure...
03-04 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 06:27 DEBUG  TaskList: ## Finished create_dir_structure
03-04 06:27 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 06:27 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 06:27 DEBUG  TaskList: ## Running create_uninstaller...
03-04 06:27 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 06:27 DEBUG  TaskList: ## Finished create_uninstaller
03-04 06:27 DEBUG  TaskList: ## Running copy_installation_files...
03-04 06:27 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 06:27 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\winboot -> C:\ubuntu\winboot
03-04 06:27 DEBUG  WindowsBackend: Copying C:\DOCUME~1\THIRUM~1\LOCALS~1\Temp\pyl27.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 06:27 DEBUG  TaskList: ## Finished copy_installation_files
03-04 06:27 DEBUG  TaskList: ## Running use_cd...
03-04 06:27 DEBUG  TaskList: New task copy_file
03-04 06:27 DEBUG  TaskList: ### Running copy_file...
03-04 06:29 DEBUG  TaskList: ### Finished copy_file
03-04 06:29 DEBUG  TaskList: New task check_iso
03-04 06:29 DEBUG  TaskList: ### Running check_iso...
03-04 06:29 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-04 06:29 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-04 06:29 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-04 06:29 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-04 06:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-04 06:29 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-04 06:29 DEBUG  TaskList: New task get_metalink
03-04 06:29 DEBUG  TaskList: #### Running get_metalink...
03-04 06:29 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > C:\ubuntu\install
03-04 06:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
03-04 06:29 DEBUG  downloader: download finished (read 26651 bytes)
03-04 06:29 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
03-04 06:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-04 06:29 DEBUG  downloader: download finished (read 562 bytes)
03-04 06:29 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-04 06:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-04 06:29 DEBUG  downloader: download finished (read 189 bytes)
03-04 06:29 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-04 06:29 INFO   saplog: Checking block bindings..
03-04 06:29 INFO   saplog: Key verified successfully.
03-04 06:29 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-04 06:29 DEBUG  TaskList: #### Finished get_metalink
03-04 06:29 DEBUG  TaskList: New task get_file_md5
03-04 06:29 DEBUG  TaskList: #### Running get_file_md5...
03-04 06:30 DEBUG  TaskList: #### Finished get_file_md5
03-04 06:30 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (dc51c1d7e3e173dcab4e0b9ad2be2bbf != 4b4e42cd2e7be5b74bad7ec00f4ad529)
None
03-04 06:30 DEBUG  TaskList: ### Finished check_iso
03-04 06:30 DEBUG  TaskList: ## Finished use_cd
03-04 06:30 DEBUG  TaskList: ## Running extract_kernel...
03-04 06:30 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
03-04 06:30 DEBUG  TaskList: # Cancelling tasklist
03-04 06:30 DEBUG  TaskList: # Finished tasklist
03-04 06:30 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
```

---

### Post by overdrank on 2010-03-03
Hi and welcome, Moved to Absolute Beginner Talk

---

