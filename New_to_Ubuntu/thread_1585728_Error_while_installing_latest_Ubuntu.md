---
title: "Error while installing latest Ubuntu"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Berkyt on 2010-09-30
So I am a complete Ubunto noob. I downloaded the latest version. Burned it to a disc, and during the installation it tells me to look at a log for why it won't install. 

I am running W7 64 Bit Ultimate. And I wanted to install this Ubuntu inside windows, so I can choose how I boot. 

I uploaded the error log, can someone tell me what is wrong?

[http://www.filedropper.com/wubi-10041-rev190](http://www.filedropper.com/wubi-10041-rev190)

---

### Post by 23dornot23d on 2010-09-30
Seems to have failed after doing some things ok ..... but fails when it starts to copy the files across from the CD I think .......

```

09-30 21:41 DEBUG  TaskList: ## Finished create_uninstaller 
09-30 21:41 DEBUG  TaskList: ## Running copy_installation_files... 
09-30 21:41 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation 
09-30 21:41 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\winboot -> C:\ubuntu\winboot 
09-30 21:41 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico 
09-30 21:41 DEBUG  TaskList: ## Finished copy_installation_files 
09-30 21:41 DEBUG  TaskList: ## Running get_iso... 
09-30 21:41 DEBUG  TaskList: New task copy_file 
09-30 21:41 DEBUG  TaskList: ### Running copy_file... 
[B]09-30 21:43 ERROR  TaskList: [Errno 22] Invalid argument 
Traceback (most recent call last): 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file 
IOError: [Errno 22] Invalid argument [/B]
09-30 21:43 DEBUG  TaskList: # Cancelling tasklist 
09-30 21:43 DEBUG  TaskList: New task check_iso 
09-30 21:43 ERROR  root: [Errno 22] Invalid argument 
Traceback (most recent call last): 
  File "\lib\wubi\application.py", line 56, in run 
  File "\lib\wubi\application.py", line 128, in select_task 
  File "\lib\wubi\application.py", line 194, in run_cd_menu 
  File "\lib\wubi\application.py", line 118, in select_task 
  File "\lib\wubi\application.py", line 156, in run_installer 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file 
IOError: [Errno 22] Invalid argument 
09-30 21:43 DEBUG  CommonBackend: Searching for local ISO 
09-30 21:43 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now 
09-30 21:43 DEBUG  TaskList: New task get_metalink 
09-30 21:43 ERROR  TaskList: Cannot download the metalink and therefore the ISO 
Traceback (most recent call last): 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso 
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso 
Exception: Cannot download the metalink and therefore the ISO 
09-30 21:43 DEBUG  TaskList: # Cancelling tasklist 
09-30 21:43 DEBUG  TaskList: # Finished tasklist

```Seems to fail there ..... but was this a special installation .... was there plenty of room for it ...... 

I have not done a wubi install ...... 

My first thoughts are is the ISO good .... but not sure how it uses it ...... * Could not find any ISO or CD, downloading one now

I always install to a separate partition but by me adding the error above here in {code quotes} may help someone track it down for you ......

Full File listing here _**[COLOR=Blue]keeps it all visible and available[/COLOR]**_ to check thtough .......

```

09-30 21:33 INFO   root: === wubi 10.04.1 rev190 === 
09-30 21:33 DEBUG  root: Logfile is c:\users\igor\appdata\local\temp\wubi-10.04.1-rev190.log 
09-30 21:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu'] 
09-30 21:33 DEBUG  CommonBackend: data_dir=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\data 
09-30 21:33 DEBUG  WindowsBackend: 7z=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\bin\7z.exe 
09-30 21:33 DEBUG  CommonBackend: Fetching basic info... 
09-30 21:33 DEBUG  CommonBackend: original_exe=D:\wubi.exe 
09-30 21:33 DEBUG  CommonBackend: platform=win32 
09-30 21:33 DEBUG  CommonBackend: osname=nt 
09-30 21:33 DEBUG  CommonBackend: language=en_US 
09-30 21:33 DEBUG  CommonBackend: encoding=cp1252 
09-30 21:33 DEBUG  WindowsBackend: arch=amd64 
09-30 21:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\data\isolist.ini 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 
09-30 21:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 
09-30 21:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386 
09-30 21:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386 
09-30 21:33 DEBUG  WindowsBackend: Fetching host info... 
09-30 21:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 
09-30 21:33 DEBUG  WindowsBackend: windows version=vista 
09-30 21:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium 
09-30 21:33 DEBUG  WindowsBackend: windows_sp=None 
09-30 21:33 DEBUG  WindowsBackend: windows_build=7600 
09-30 21:33 DEBUG  WindowsBackend: gmt=-6 
09-30 21:33 DEBUG  WindowsBackend: country=US 
09-30 21:33 DEBUG  WindowsBackend: timezone=America/Chicago 
09-30 21:33 DEBUG  WindowsBackend: windows_username=Igor 
09-30 21:33 DEBUG  WindowsBackend: user_full_name=Igor 
09-30 21:33 DEBUG  WindowsBackend: user_directory=C:\Users\Igor 
09-30 21:33 DEBUG  WindowsBackend: windows_language_code=1033 
09-30 21:33 DEBUG  WindowsBackend: windows_language=English 
09-30 21:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz 
09-30 21:33 DEBUG  WindowsBackend: bootloader=vista 
09-30 21:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 342733.152344 mb free ntfs) 
09-30 21:33 DEBUG  WindowsBackend: drive=Drive(C: hd 342733.152344 mb free ntfs) 
09-30 21:33 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 
09-30 21:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free ) 
09-30 21:33 DEBUG  WindowsBackend: uninstaller_path=None 
09-30 21:33 DEBUG  WindowsBackend: previous_target_dir=None 
09-30 21:33 DEBUG  WindowsBackend: previous_distro_name=None 
09-30 21:33 DEBUG  WindowsBackend: keyboard_id=67699721 
09-30 21:33 DEBUG  WindowsBackend: keyboard_layout=us 
09-30 21:33 DEBUG  WindowsBackend: keyboard_variant= 
09-30 21:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252') 
09-30 21:33 DEBUG  CommonBackend: locale=en_US.UTF-8 
09-30 21:33 DEBUG  WindowsBackend: total_memory_mb=3963.984375 
09-30 21:33 DEBUG  CommonBackend: Searching ISOs on USB devices 
09-30 21:33 DEBUG  CommonBackend: Searching for local CDs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Ubuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Ubuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Ubuntu Netbook CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Kubuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Kubuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Kubuntu Netbook CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Xubuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Xubuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Mythbuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp is a valid Mythbuntu CD 
09-30 21:33 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\casper\filesystem.squashfs 
09-30 21:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 
09-30 21:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.1 LTS "Lucid Lynx" - Release amd64 (20100816.1) 
09-30 21:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'} 
**09-30 21:33 INFO   Distro: Found a valid CD for Ubuntu: D:\ **
09-30 21:33 INFO   root: Running the CD menu... 
09-30 21:33 DEBUG  WindowsFrontend: __init__... 
09-30 21:33 DEBUG  WindowsFrontend: on_init... 
09-30 21:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\translations, languages=['en_US', 'en'] 
09-30 21:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\translations, languages=['en_US', 'en'] 
09-30 21:33 INFO   root: CD menu finished 
09-30 21:33 INFO   root: Running the installer... 
09-30 21:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\translations, languages=['en_US', 'en'] 
09-30 21:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\translations, languages=['en_US', 'en'] 
09-30 21:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=16000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=igor 
09-30 21:40 INFO   root: Received settings 
09-30 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\translations, languages=['en_US', 'en'] 
09-30 21:40 DEBUG  TaskList: # Running tasklist... 
09-30 21:40 DEBUG  TaskList: ## Running select_target_dir... 
09-30 21:40 INFO   WindowsBackend: Installing into C:\ubuntu 
09-30 21:40 DEBUG  TaskList: ## Finished select_target_dir 
09-30 21:40 DEBUG  TaskList: ## Running create_dir_structure... 
09-30 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu 
09-30 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks 
09-30 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install 
09-30 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot 
09-30 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot 
09-30 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub 
09-30 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub 
09-30 21:40 DEBUG  TaskList: ## Finished create_dir_structure 
09-30 21:40 DEBUG  TaskList: ## Running uncompress_target_dir... 
09-30 21:40 DEBUG  TaskList: ## Finished uncompress_target_dir 
09-30 21:40 DEBUG  TaskList: ## Running create_uninstaller... 
09-30 21:40 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com 
09-30 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support 
09-30 21:40 DEBUG  TaskList: ## Finished create_uninstaller 
09-30 21:40 DEBUG  TaskList: ## Running copy_installation_files... 
09-30 21:40 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation 
09-30 21:40 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\winboot -> C:\ubuntu\winboot 
09-30 21:40 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pylA05B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico 
09-30 21:40 DEBUG  TaskList: ## Finished copy_installation_files 
09-30 21:40 DEBUG  TaskList: ## Running get_iso... 
09-30 21:40 DEBUG  TaskList: New task copy_file 
09-30 21:40 DEBUG  TaskList: ### Running copy_file... 
[B]09-30 21:40 ERROR  TaskList: [Errno 22] Invalid argument 
Traceback (most recent call last): 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file 
IOError: [Errno 22] Invalid argument [/B]
09-30 21:40 DEBUG  TaskList: # Cancelling tasklist 
09-30 21:40 DEBUG  TaskList: New task check_iso 
09-30 21:40 ERROR  root: [Errno 22] Invalid argument 
Traceback (most recent call last): 
  File "\lib\wubi\application.py", line 56, in run 
  File "\lib\wubi\application.py", line 128, in select_task 
  File "\lib\wubi\application.py", line 194, in run_cd_menu 
  File "\lib\wubi\application.py", line 118, in select_task 
  File "\lib\wubi\application.py", line 156, in run_installer 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file 
IOError: [Errno 22] Invalid argument 
09-30 21:40 DEBUG  CommonBackend: Searching for local ISO 
09-30 21:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now 
09-30 21:40 DEBUG  TaskList: New task get_metalink 
09-30 21:40 ERROR  TaskList: Cannot download the metalink and therefore the ISO 
Traceback (most recent call last): 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso 
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso 
Exception: Cannot download the metalink and therefore the ISO 
09-30 21:40 DEBUG  TaskList: # Cancelling tasklist 
09-30 21:40 DEBUG  TaskList: # Finished tasklist 
09-30 21:41 INFO   root: === wubi 10.04.1 rev190 === 
09-30 21:41 DEBUG  root: Logfile is c:\users\igor\appdata\local\temp\wubi-10.04.1-rev190.log 
09-30 21:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu'] 
09-30 21:41 DEBUG  CommonBackend: data_dir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\data 
09-30 21:41 DEBUG  WindowsBackend: 7z=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\bin\7z.exe 
09-30 21:41 DEBUG  CommonBackend: Fetching basic info... 
09-30 21:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe 
09-30 21:41 DEBUG  CommonBackend: platform=win32 
09-30 21:41 DEBUG  CommonBackend: osname=nt 
09-30 21:41 DEBUG  CommonBackend: language=en_US 
09-30 21:41 DEBUG  CommonBackend: encoding=cp1252 
09-30 21:41 DEBUG  WindowsBackend: arch=amd64 
09-30 21:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\data\isolist.ini 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386 
09-30 21:41 DEBUG  WindowsBackend: Fetching host info... 
09-30 21:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 
09-30 21:41 DEBUG  WindowsBackend: windows version=vista 
09-30 21:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium 
09-30 21:41 DEBUG  WindowsBackend: windows_sp=None 
09-30 21:41 DEBUG  WindowsBackend: windows_build=7600 
09-30 21:41 DEBUG  WindowsBackend: gmt=-6 
09-30 21:41 DEBUG  WindowsBackend: country=US 
09-30 21:41 DEBUG  WindowsBackend: timezone=America/Chicago 
09-30 21:41 DEBUG  WindowsBackend: windows_username=Igor 
09-30 21:41 DEBUG  WindowsBackend: user_full_name=Igor 
09-30 21:41 DEBUG  WindowsBackend: user_directory=C:\Users\Igor 
09-30 21:41 DEBUG  WindowsBackend: windows_language_code=1033 
09-30 21:41 DEBUG  WindowsBackend: windows_language=English 
09-30 21:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz 
09-30 21:41 DEBUG  WindowsBackend: bootloader=vista 
09-30 21:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 342661.960938 mb free ntfs) 
09-30 21:41 DEBUG  WindowsBackend: drive=Drive(C: hd 342661.960938 mb free ntfs) 
09-30 21:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 
09-30 21:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free ) 
09-30 21:41 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe 
09-30 21:41 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu 
09-30 21:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu 
09-30 21:41 DEBUG  WindowsBackend: keyboard_id=67699721 
09-30 21:41 DEBUG  WindowsBackend: keyboard_layout=us 
09-30 21:41 DEBUG  WindowsBackend: keyboard_variant= 
09-30 21:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252') 
09-30 21:41 DEBUG  CommonBackend: locale=en_US.UTF-8 
09-30 21:41 DEBUG  WindowsBackend: total_memory_mb=3963.984375 
09-30 21:41 DEBUG  CommonBackend: Searching ISOs on USB devices 
09-30 21:41 DEBUG  CommonBackend: Searching for local CDs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Ubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Ubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Ubuntu Netbook CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Kubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Kubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Kubuntu Netbook CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Xubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Xubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Mythbuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Mythbuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 
09-30 21:41 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.1 LTS "Lucid Lynx" - Release amd64 (20100816.1) 
09-30 21:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'} 
09-30 21:41 INFO   Distro: Found a valid CD for Ubuntu: D:\ 
09-30 21:41 INFO   root: Running the CD menu... 
09-30 21:41 DEBUG  WindowsFrontend: __init__... 
09-30 21:41 DEBUG  WindowsFrontend: on_init... 
09-30 21:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\translations, languages=['en_US', 'en'] 
09-30 21:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\translations, languages=['en_US', 'en'] 
09-30 21:41 INFO   root: CD menu finished 
09-30 21:41 INFO   root: Already installed, running the uninstaller... 
09-30 21:41 INFO   root: Running the uninstaller... 
09-30 21:41 INFO   CommonBackend: This is the uninstaller running 
09-30 21:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\translations, languages=['en_US', 'en'] 
09-30 21:41 INFO   root: Received settings 
09-30 21:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\translations, languages=['en_US', 'en'] 
09-30 21:41 DEBUG  TaskList: # Running tasklist... 
09-30 21:41 DEBUG  TaskList: ## Running Backup ISO... 
09-30 21:41 DEBUG  TaskList: ## Finished Backup ISO 
09-30 21:41 DEBUG  TaskList: ## Running Remove bootloader entry... 
09-30 21:41 DEBUG  WindowsBackend: Could not find bcd id 
09-30 21:41 DEBUG  WindowsBackend: undo_bootini C: 
09-30 21:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 342661.960938 mb free ntfs) 
09-30 21:41 DEBUG  TaskList: ## Finished Remove bootloader entry 
09-30 21:41 DEBUG  TaskList: ## Running Remove target dir... 
09-30 21:41 DEBUG  CommonBackend: Deleting C:\ubuntu 
09-30 21:41 DEBUG  TaskList: ## Finished Remove target dir 
09-30 21:41 DEBUG  TaskList: ## Running Remove registry key... 
09-30 21:41 DEBUG  TaskList: ## Finished Remove registry key 
09-30 21:41 DEBUG  TaskList: # Finished tasklist 
09-30 21:41 INFO   root: Almost finished uninstalling 
09-30 21:41 INFO   root: Finished uninstallation 
09-30 21:41 DEBUG  CommonBackend: Fetching basic info... 
09-30 21:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe 
09-30 21:41 DEBUG  CommonBackend: platform=win32 
09-30 21:41 DEBUG  CommonBackend: osname=nt 
09-30 21:41 DEBUG  WindowsBackend: arch=amd64 
09-30 21:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\data\isolist.ini 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64 
09-30 21:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386 
09-30 21:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386 
09-30 21:41 DEBUG  WindowsBackend: Fetching host info... 
09-30 21:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 
09-30 21:41 DEBUG  WindowsBackend: windows version=vista 
09-30 21:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium 
09-30 21:41 DEBUG  WindowsBackend: windows_sp=None 
09-30 21:41 DEBUG  WindowsBackend: windows_build=7600 
09-30 21:41 DEBUG  WindowsBackend: gmt=-6 
09-30 21:41 DEBUG  WindowsBackend: country=US 
09-30 21:41 DEBUG  WindowsBackend: timezone=America/Chicago 
09-30 21:41 DEBUG  WindowsBackend: windows_username=Igor 
09-30 21:41 DEBUG  WindowsBackend: user_full_name=Igor 
09-30 21:41 DEBUG  WindowsBackend: user_directory=C:\Users\Igor 
09-30 21:41 DEBUG  WindowsBackend: windows_language_code=1033 
09-30 21:41 DEBUG  WindowsBackend: windows_language=English 
09-30 21:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz 
09-30 21:41 DEBUG  WindowsBackend: bootloader=vista 
09-30 21:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 342732.453125 mb free ntfs) 
09-30 21:41 DEBUG  WindowsBackend: drive=Drive(C: hd 342732.453125 mb free ntfs) 
09-30 21:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs) 
09-30 21:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free ) 
09-30 21:41 DEBUG  WindowsBackend: uninstaller_path=None 
09-30 21:41 DEBUG  WindowsBackend: previous_target_dir=None 
09-30 21:41 DEBUG  WindowsBackend: previous_distro_name=None 
09-30 21:41 DEBUG  WindowsBackend: keyboard_id=67699721 
09-30 21:41 DEBUG  WindowsBackend: keyboard_layout=us 
09-30 21:41 DEBUG  WindowsBackend: keyboard_variant= 
09-30 21:41 DEBUG  WindowsBackend: total_memory_mb=3963.984375 
09-30 21:41 DEBUG  CommonBackend: Searching ISOs on USB devices 
09-30 21:41 DEBUG  CommonBackend: Searching for local CDs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Ubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Ubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Ubuntu Netbook CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Kubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Kubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Kubuntu Netbook CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Xubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Xubuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Mythbuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp is a valid Mythbuntu CD 
09-30 21:41 DEBUG  Distro:     does not contain C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\casper\filesystem.squashfs 
09-30 21:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD 
09-30 21:41 INFO   Distro: Found a valid CD for Ubuntu: D:\ 
09-30 21:41 INFO   root: Running the installer... 
09-30 21:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\translations, languages=['en_US', 'en'] 
09-30 21:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\translations, languages=['en_US', 'en'] 
09-30 21:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=igor 
09-30 21:41 INFO   root: Received settings 
09-30 21:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\translations, languages=['en_US', 'en'] 
09-30 21:41 DEBUG  TaskList: # Running tasklist... 
09-30 21:41 DEBUG  TaskList: ## Running select_target_dir... 
09-30 21:41 INFO   WindowsBackend: Installing into C:\ubuntu 
09-30 21:41 DEBUG  TaskList: ## Finished select_target_dir 
09-30 21:41 DEBUG  TaskList: ## Running create_dir_structure... 
09-30 21:41 DEBUG  CommonBackend: Creating dir C:\ubuntu 
09-30 21:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks 
09-30 21:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install 
09-30 21:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot 
09-30 21:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot 
09-30 21:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub 
09-30 21:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub 
09-30 21:41 DEBUG  TaskList: ## Finished create_dir_structure 
09-30 21:41 DEBUG  TaskList: ## Running uncompress_target_dir... 
09-30 21:41 DEBUG  TaskList: ## Finished uncompress_target_dir 
09-30 21:41 DEBUG  TaskList: ## Running create_uninstaller... 
09-30 21:41 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com 
09-30 21:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support 
09-30 21:41 DEBUG  TaskList: ## Finished create_uninstaller 
09-30 21:41 DEBUG  TaskList: ## Running copy_installation_files... 
09-30 21:41 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation 
09-30 21:41 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\winboot -> C:\ubuntu\winboot 
09-30 21:41 DEBUG  WindowsBackend: Copying C:\Users\Igor\AppData\Local\Temp\pyl13B6.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico 
09-30 21:41 DEBUG  TaskList: ## Finished copy_installation_files 
09-30 21:41 DEBUG  TaskList: ## Running get_iso... 
09-30 21:41 DEBUG  TaskList: New task copy_file 
09-30 21:41 DEBUG  TaskList: ### Running copy_file... 
09-30 21:43 ERROR  TaskList: [Errno 22] Invalid argument 
Traceback (most recent call last): 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file 
IOError: [Errno 22] Invalid argument 
09-30 21:43 DEBUG  TaskList: # Cancelling tasklist 
09-30 21:43 DEBUG  TaskList: New task check_iso 
09-30 21:43 ERROR  root: [Errno 22] Invalid argument 
Traceback (most recent call last): 
  File "\lib\wubi\application.py", line 56, in run 
  File "\lib\wubi\application.py", line 128, in select_task 
  File "\lib\wubi\application.py", line 194, in run_cd_menu 
  File "\lib\wubi\application.py", line 118, in select_task 
  File "\lib\wubi\application.py", line 156, in run_installer 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file 
IOError: [Errno 22] Invalid argument 
09-30 21:43 DEBUG  CommonBackend: Searching for local ISO 
09-30 21:43 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now 
09-30 21:43 DEBUG  TaskList: New task get_metalink 
09-30 21:43 ERROR  TaskList: Cannot download the metalink and therefore the ISO 
Traceback (most recent call last): 
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__ 
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso 
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso 
Exception: Cannot download the metalink and therefore the ISO 
09-30 21:43 DEBUG  TaskList: # Cancelling tasklist 
09-30 21:43 DEBUG  TaskList: # Finished tasklist

```**Distro: Found a valid CD for Ubuntu: D:\**
Maybe its having a problem reading the disk in ...... [B]D:\

Did you _[COLOR=Blue][check the checksum]("https://help.ubuntu.com/community/UbuntuHashes")[/COLOR]_ .... of the CD
[/B]

---

