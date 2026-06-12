---
title: "Cant load Ubutu onto my Packard Bell dot s netbook."
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Lodi666 on 2011-05-23
I'm trying to load Ubutu onto my Packard Bell dot s netbook with wubi, but its not working.
 
Heres what pops up half way through the instillation process:
 
 
Cannot download the metalink and therefore the ISO
 
For more information, please see the log file:
c:\users\troub~1\appdata\local\temp\wubi-11.04-rev211.log
 
 
Anyone know whats going wrong and how I can deal with it? Thanks! :)

---

### Post by ajgreeny on 2011-05-23
And what does that log file tell you?

---

### Post by Lodi666 on 2011-05-23
It sais this:
 
 
05-23 21:01 INFO   root: === wubi 11.04 rev211 ===
05-23 21:01 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\PPQ9DQVM\\wubi[1].exe"']
05-23 21:01 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data
05-23 21:01 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\bin\7z.exe
05-23 21:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:01 DEBUG  CommonBackend: Fetching basic info...
05-23 21:01 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\PPQ9DQVM\wubi[1].exe
05-23 21:01 DEBUG  CommonBackend: platform=win32
05-23 21:01 DEBUG  CommonBackend: osname=nt
05-23 21:01 DEBUG  CommonBackend: language=en_GB
05-23 21:01 DEBUG  CommonBackend: encoding=cp1252
05-23 21:01 DEBUG  WindowsBackend: arch=amd64
05-23 21:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data\isolist.ini
05-23 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:01 DEBUG  WindowsBackend: Fetching host info...
05-23 21:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:01 DEBUG  WindowsBackend: windows version=vista
05-23 21:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:01 DEBUG  WindowsBackend: windows_sp=None
05-23 21:01 DEBUG  WindowsBackend: windows_build=7600
05-23 21:01 DEBUG  WindowsBackend: gmt=0
05-23 21:01 DEBUG  WindowsBackend: country=GB
05-23 21:01 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:01 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:01 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:01 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:01 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:01 DEBUG  WindowsBackend: windows_language=English
05-23 21:01 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:01 DEBUG  WindowsBackend: bootloader=vista
05-23 21:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174779.617188 mb free ntfs)
05-23 21:01 DEBUG  WindowsBackend: drive=Drive(C: hd 174779.617188 mb free ntfs)
05-23 21:01 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:01 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:01 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:01 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:01 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:01 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:01 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:01 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:01 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:01 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:01 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:01 DEBUG  CommonBackend: Searching for local CDs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu Netbook CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 INFO   root: Running the installer...
05-23 21:01 DEBUG  WindowsFrontend: __init__...
05-23 21:01 DEBUG  WindowsFrontend: on_init...
05-23 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\translations, languages=['en_GB', 'en']
05-23 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\translations, languages=['en_GB', 'en']
05-23 21:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:02 INFO   root: Received settings
05-23 21:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\translations, languages=['en_GB', 'en']
05-23 21:02 DEBUG  TaskList: # Running tasklist...
05-23 21:02 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:02 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:02 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:02 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:02 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:02 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:02 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:02 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\PPQ9DQVM\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:02 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:02 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:02 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:02 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\winboot -> C:\ubuntu\winboot
05-23 21:02 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:02 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:02 DEBUG  TaskList: ## Running get_iso...
05-23 21:02 DEBUG  CommonBackend: Searching for local CD
05-23 21:02 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu Netbook CD
05-23 21:02 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:02 DEBUG  CommonBackend: Searching for local ISO
05-23 21:02 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:02 DEBUG  TaskList: New task get_metalink
05-23 21:02 DEBUG  TaskList: ### Running get_metalink...
05-23 21:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:02 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:02 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:02 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:02 DEBUG  TaskList: ### Finished get_metalink
05-23 21:02 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:02 DEBUG  TaskList: # Cancelling tasklist
05-23 21:02 DEBUG  TaskList: # Finished tasklist
05-23 21:02 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:05 INFO   root: === wubi 11.04 rev211 ===
05-23 21:05 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\J5OFP1MQ\\wubi[1].exe"']
05-23 21:05 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data
05-23 21:05 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\bin\7z.exe
05-23 21:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:05 DEBUG  CommonBackend: Fetching basic info...
05-23 21:05 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\J5OFP1MQ\wubi[1].exe
05-23 21:05 DEBUG  CommonBackend: platform=win32
05-23 21:05 DEBUG  CommonBackend: osname=nt
05-23 21:05 DEBUG  CommonBackend: language=en_GB
05-23 21:05 DEBUG  CommonBackend: encoding=cp1252
05-23 21:05 DEBUG  WindowsBackend: arch=amd64
05-23 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\isolist.ini
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:05 DEBUG  WindowsBackend: Fetching host info...
05-23 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:05 DEBUG  WindowsBackend: windows version=vista
05-23 21:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:05 DEBUG  WindowsBackend: windows_sp=None
05-23 21:05 DEBUG  WindowsBackend: windows_build=7600
05-23 21:05 DEBUG  WindowsBackend: gmt=0
05-23 21:05 DEBUG  WindowsBackend: country=GB
05-23 21:05 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:05 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:05 DEBUG  WindowsBackend: windows_language=English
05-23 21:05 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:05 DEBUG  WindowsBackend: bootloader=vista
05-23 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174765.773438 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 174765.773438 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 21:05 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:05 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:05 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:05 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:05 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:05 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:05 DEBUG  CommonBackend: Searching for local CDs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 INFO   root: Already installed, running the uninstaller...
05-23 21:05 INFO   root: Running the uninstaller...
05-23 21:05 INFO   CommonBackend: This is the uninstaller running
05-23 21:05 DEBUG  WindowsFrontend: __init__...
05-23 21:05 DEBUG  WindowsFrontend: on_init...
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:05 INFO   root: Received settings
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:05 DEBUG  TaskList: # Running tasklist...
05-23 21:05 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:05 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:05 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:05 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:05 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174765.773438 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:05 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:05 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:05 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:05 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:05 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:05 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:05 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:05 DEBUG  TaskList: # Finished tasklist
05-23 21:05 INFO   root: Almost finished uninstalling
05-23 21:05 INFO   root: Finished uninstallation
05-23 21:05 DEBUG  CommonBackend: Fetching basic info...
05-23 21:05 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\J5OFP1MQ\wubi[1].exe
05-23 21:05 DEBUG  CommonBackend: platform=win32
05-23 21:05 DEBUG  CommonBackend: osname=nt
05-23 21:05 DEBUG  WindowsBackend: arch=amd64
05-23 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\isolist.ini
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:05 DEBUG  WindowsBackend: Fetching host info...
05-23 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:05 DEBUG  WindowsBackend: windows version=vista
05-23 21:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:05 DEBUG  WindowsBackend: windows_sp=None
05-23 21:05 DEBUG  WindowsBackend: windows_build=7600
05-23 21:05 DEBUG  WindowsBackend: gmt=0
05-23 21:05 DEBUG  WindowsBackend: country=GB
05-23 21:05 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:05 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:05 DEBUG  WindowsBackend: windows_language=English
05-23 21:05 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:05 DEBUG  WindowsBackend: bootloader=vista
05-23 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174767.152344 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 174767.152344 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:05 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:05 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:05 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:05 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:05 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:05 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:05 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:05 DEBUG  CommonBackend: Searching for local CDs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 INFO   root: Running the installer...
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:07 INFO   root: Received settings
05-23 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:07 DEBUG  TaskList: # Running tasklist...
05-23 21:07 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:07 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:07 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:07 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:07 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:07 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:07 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:07 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\J5OFP1MQ\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:07 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:07 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:07 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:07 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\winboot -> C:\ubuntu\winboot
05-23 21:07 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:07 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:07 DEBUG  TaskList: ## Running get_iso...
05-23 21:07 DEBUG  CommonBackend: Searching for local CD
05-23 21:07 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu Netbook CD
05-23 21:07 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:07 DEBUG  CommonBackend: Searching for local ISO
05-23 21:07 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:07 DEBUG  TaskList: New task get_metalink
05-23 21:07 DEBUG  TaskList: ### Running get_metalink...
05-23 21:07 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:07 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:07 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:07 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:07 DEBUG  TaskList: ### Finished get_metalink
05-23 21:07 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:07 DEBUG  TaskList: # Cancelling tasklist
05-23 21:07 DEBUG  TaskList: # Finished tasklist
05-23 21:07 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:15 INFO   root: === wubi 11.04 rev211 ===
05-23 21:15 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 21:15 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data
05-23 21:15 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\bin\7z.exe
05-23 21:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:15 DEBUG  CommonBackend: Fetching basic info...
05-23 21:15 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:15 DEBUG  CommonBackend: platform=win32
05-23 21:15 DEBUG  CommonBackend: osname=nt
05-23 21:15 DEBUG  CommonBackend: language=en_GB
05-23 21:15 DEBUG  CommonBackend: encoding=cp1252
05-23 21:15 DEBUG  WindowsBackend: arch=amd64
05-23 21:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\isolist.ini
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:15 DEBUG  WindowsBackend: Fetching host info...
05-23 21:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:15 DEBUG  WindowsBackend: windows version=vista
05-23 21:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:15 DEBUG  WindowsBackend: windows_sp=None
05-23 21:15 DEBUG  WindowsBackend: windows_build=7600
05-23 21:15 DEBUG  WindowsBackend: gmt=0
05-23 21:15 DEBUG  WindowsBackend: country=GB
05-23 21:15 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:15 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:15 DEBUG  WindowsBackend: windows_language=English
05-23 21:15 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:15 DEBUG  WindowsBackend: bootloader=vista
05-23 21:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174665.800781 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(C: hd 174665.800781 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 21:15 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:15 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:15 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:15 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:15 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:15 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:15 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:15 DEBUG  CommonBackend: Searching for local CDs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 INFO   root: Already installed, running the uninstaller...
05-23 21:15 INFO   root: Running the uninstaller...
05-23 21:15 INFO   CommonBackend: This is the uninstaller running
05-23 21:15 DEBUG  WindowsFrontend: __init__...
05-23 21:15 DEBUG  WindowsFrontend: on_init...
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:15 INFO   root: Received settings
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:15 DEBUG  TaskList: # Running tasklist...
05-23 21:15 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:15 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:15 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:15 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:15 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174665.800781 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:15 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:15 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:15 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:15 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:15 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:15 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:15 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:15 DEBUG  TaskList: # Finished tasklist
05-23 21:15 INFO   root: Almost finished uninstalling
05-23 21:15 INFO   root: Finished uninstallation
05-23 21:15 DEBUG  CommonBackend: Fetching basic info...
05-23 21:15 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:15 DEBUG  CommonBackend: platform=win32
05-23 21:15 DEBUG  CommonBackend: osname=nt
05-23 21:15 DEBUG  WindowsBackend: arch=amd64
05-23 21:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\isolist.ini
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:15 DEBUG  WindowsBackend: Fetching host info...
05-23 21:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:15 DEBUG  WindowsBackend: windows version=vista
05-23 21:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:15 DEBUG  WindowsBackend: windows_sp=None
05-23 21:15 DEBUG  WindowsBackend: windows_build=7600
05-23 21:15 DEBUG  WindowsBackend: gmt=0
05-23 21:15 DEBUG  WindowsBackend: country=GB
05-23 21:15 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:15 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:15 DEBUG  WindowsBackend: windows_language=English
05-23 21:15 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:15 DEBUG  WindowsBackend: bootloader=vista
05-23 21:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174667.441406 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(C: hd 174667.441406 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:15 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:15 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:15 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:15 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:15 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:15 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:15 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:15 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:15 DEBUG  CommonBackend: Searching for local CDs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 INFO   root: Running the installer...
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:16 INFO   root: Received settings
05-23 21:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:16 DEBUG  TaskList: # Running tasklist...
05-23 21:16 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:16 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:16 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:16 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:16 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:16 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:16 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:16 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:16 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:16 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:16 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:16 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\winboot -> C:\ubuntu\winboot
05-23 21:16 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:16 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:16 DEBUG  TaskList: ## Running get_iso...
05-23 21:16 DEBUG  CommonBackend: Searching for local CD
05-23 21:16 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu Netbook CD
05-23 21:16 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:16 DEBUG  CommonBackend: Searching for local ISO
05-23 21:16 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:16 DEBUG  TaskList: New task get_metalink
05-23 21:16 DEBUG  TaskList: ### Running get_metalink...
05-23 21:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:16 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-23 21:16 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:16 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-23 21:16 DEBUG  TaskList: ### Finished get_metalink
05-23 21:16 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:16 DEBUG  TaskList: # Cancelling tasklist
05-23 21:16 DEBUG  TaskList: # Finished tasklist
05-23 21:16 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:17 INFO   root: === wubi 11.04 rev211 ===
05-23 21:17 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 21:17 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data
05-23 21:17 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\bin\7z.exe
05-23 21:17 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:17 DEBUG  CommonBackend: Fetching basic info...
05-23 21:17 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:17 DEBUG  CommonBackend: platform=win32
05-23 21:17 DEBUG  CommonBackend: osname=nt
05-23 21:17 DEBUG  CommonBackend: language=en_GB
05-23 21:17 DEBUG  CommonBackend: encoding=cp1252
05-23 21:17 DEBUG  WindowsBackend: arch=amd64
05-23 21:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\isolist.ini
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:17 DEBUG  WindowsBackend: Fetching host info...
05-23 21:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:17 DEBUG  WindowsBackend: windows version=vista
05-23 21:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:17 DEBUG  WindowsBackend: windows_sp=None
05-23 21:17 DEBUG  WindowsBackend: windows_build=7600
05-23 21:17 DEBUG  WindowsBackend: gmt=0
05-23 21:17 DEBUG  WindowsBackend: country=GB
05-23 21:17 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:17 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:17 DEBUG  WindowsBackend: windows_language=English
05-23 21:17 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:17 DEBUG  WindowsBackend: bootloader=vista
05-23 21:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174723.125 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(C: hd 174723.125 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 21:17 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:17 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:17 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:17 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:17 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:17 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:17 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:17 DEBUG  CommonBackend: Searching for local CDs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 INFO   root: Already installed, running the uninstaller...
05-23 21:17 INFO   root: Running the uninstaller...
05-23 21:17 INFO   CommonBackend: This is the uninstaller running
05-23 21:17 DEBUG  WindowsFrontend: __init__...
05-23 21:17 DEBUG  WindowsFrontend: on_init...
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:17 INFO   root: Received settings
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:17 DEBUG  TaskList: # Running tasklist...
05-23 21:17 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:17 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:17 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:17 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:17 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174723.125 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:17 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:17 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:17 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:17 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:17 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:17 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:17 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:17 DEBUG  TaskList: # Finished tasklist
05-23 21:17 INFO   root: Almost finished uninstalling
05-23 21:17 INFO   root: Finished uninstallation
05-23 21:17 DEBUG  CommonBackend: Fetching basic info...
05-23 21:17 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:17 DEBUG  CommonBackend: platform=win32
05-23 21:17 DEBUG  CommonBackend: osname=nt
05-23 21:17 DEBUG  WindowsBackend: arch=amd64
05-23 21:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\isolist.ini
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:17 DEBUG  WindowsBackend: Fetching host info...
05-23 21:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:17 DEBUG  WindowsBackend: windows version=vista
05-23 21:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:17 DEBUG  WindowsBackend: windows_sp=None
05-23 21:17 DEBUG  WindowsBackend: windows_build=7600
05-23 21:17 DEBUG  WindowsBackend: gmt=0
05-23 21:17 DEBUG  WindowsBackend: country=GB
05-23 21:17 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:17 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:17 DEBUG  WindowsBackend: windows_language=English
05-23 21:17 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:17 DEBUG  WindowsBackend: bootloader=vista
05-23 21:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174724.632813 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(C: hd 174724.632813 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:17 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:17 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:17 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:17 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:17 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:17 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:17 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:17 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:17 DEBUG  CommonBackend: Searching for local CDs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 INFO   root: Running the installer...
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:18 INFO   root: Received settings
05-23 21:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:18 DEBUG  TaskList: # Running tasklist...
05-23 21:18 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:18 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:18 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:18 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:18 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:18 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:18 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:18 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:18 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:18 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:18 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:18 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:18 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\winboot -> C:\ubuntu\winboot
05-23 21:18 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-23 21:18 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:18 DEBUG  TaskList: ## Running get_iso...
05-23 21:18 DEBUG  CommonBackend: Searching for local CD
05-23 21:18 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:18 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:18 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:18 DEBUG  CommonBackend: Searching for local ISO
05-23 21:18 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:18 DEBUG  TaskList: New task get_metalink
05-23 21:18 DEBUG  TaskList: ### Running get_metalink...
05-23 21:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-23 21:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-23 21:18 DEBUG  downloader: download finished (read 28363 bytes)
05-23 21:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-23 21:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-23 21:18 DEBUG  downloader: download finished (read 874 bytes)
05-23 21:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-23 21:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-23 21:18 DEBUG  downloader: download finished (read 198 bytes)
05-23 21:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-23 21:18 INFO   saplog: Checking block bindings..
05-23 21:18 INFO   saplog: Key verified successfully.
05-23 21:18 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink
05-23 21:18 DEBUG  TaskList: ### Finished get_metalink
05-23 21:18 DEBUG  TaskList: New task download
05-23 21:18 DEBUG  TaskList: ### Running download...
05-23 21:18 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-23 21:22 INFO   WindowsFrontend: Operation cancelled
05-23 21:22 DEBUG  WindowsFrontend: frontend.quit
05-23 21:22 DEBUG  WindowsFrontend: frontend.on_quit
05-23 21:22 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-23 21:22 DEBUG  TaskList: # Cancelling tasklist
05-23 21:22 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-23 21:22 DEBUG  root: application.on_quit
05-23 21:22 DEBUG  root: Forceful exit
05-23 21:22 INFO   root: sys.exit
05-23 21:23 INFO   root: === wubi 11.04 rev211 ===
05-23 21:23 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 21:23 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data
05-23 21:23 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\bin\7z.exe
05-23 21:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:23 DEBUG  CommonBackend: Fetching basic info...
05-23 21:23 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:23 DEBUG  CommonBackend: platform=win32
05-23 21:23 DEBUG  CommonBackend: osname=nt
05-23 21:23 DEBUG  CommonBackend: language=en_GB
05-23 21:23 DEBUG  CommonBackend: encoding=cp1252
05-23 21:23 DEBUG  WindowsBackend: arch=amd64
05-23 21:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\isolist.ini
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:23 DEBUG  WindowsBackend: Fetching host info...
05-23 21:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:23 DEBUG  WindowsBackend: windows version=vista
05-23 21:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:23 DEBUG  WindowsBackend: windows_sp=None
05-23 21:23 DEBUG  WindowsBackend: windows_build=7600
05-23 21:23 DEBUG  WindowsBackend: gmt=0
05-23 21:23 DEBUG  WindowsBackend: country=GB
05-23 21:23 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:23 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:23 DEBUG  WindowsBackend: windows_language=English
05-23 21:23 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:23 DEBUG  WindowsBackend: bootloader=vista
05-23 21:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174715.09375 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(C: hd 174715.09375 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:23 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:23 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:23 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-23 21:23 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:23 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:23 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:23 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:23 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:23 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:23 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:23 DEBUG  CommonBackend: Searching for local CDs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 INFO   root: Already installed, running the uninstaller...
05-23 21:23 INFO   root: Running the uninstaller...
05-23 21:23 INFO   CommonBackend: This is the uninstaller running
05-23 21:23 DEBUG  WindowsFrontend: __init__...
05-23 21:23 DEBUG  WindowsFrontend: on_init...
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 INFO   root: Received settings
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 DEBUG  TaskList: # Running tasklist...
05-23 21:23 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:23 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:23 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:23 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:23 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:23 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174715.09375 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:23 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:23 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:23 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:23 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:23 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:23 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:23 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:23 DEBUG  TaskList: # Finished tasklist
05-23 21:23 INFO   root: Almost finished uninstalling
05-23 21:23 INFO   root: Finished uninstallation
05-23 21:23 DEBUG  CommonBackend: Fetching basic info...
05-23 21:23 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:23 DEBUG  CommonBackend: platform=win32
05-23 21:23 DEBUG  CommonBackend: osname=nt
05-23 21:23 DEBUG  WindowsBackend: arch=amd64
05-23 21:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\isolist.ini
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:23 DEBUG  WindowsBackend: Fetching host info...
05-23 21:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:23 DEBUG  WindowsBackend: windows version=vista
05-23 21:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:23 DEBUG  WindowsBackend: windows_sp=None
05-23 21:23 DEBUG  WindowsBackend: windows_build=7600
05-23 21:23 DEBUG  WindowsBackend: gmt=0
05-23 21:23 DEBUG  WindowsBackend: country=GB
05-23 21:23 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:23 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:23 DEBUG  WindowsBackend: windows_language=English
05-23 21:23 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:23 DEBUG  WindowsBackend: bootloader=vista
05-23 21:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174716.636719 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(C: hd 174716.636719 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:23 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:23 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:23 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:23 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:23 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:23 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:23 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:23 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:23 DEBUG  CommonBackend: Searching for local CDs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 INFO   root: Running the installer...
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:23 INFO   root: Received settings
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 DEBUG  TaskList: # Running tasklist...
05-23 21:23 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:23 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:23 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:23 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:23 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:23 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:23 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:23 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:23 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:23 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:23 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:23 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:23 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\winboot -> C:\ubuntu\winboot
05-23 21:23 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:23 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:23 DEBUG  TaskList: ## Running get_iso...
05-23 21:23 DEBUG  CommonBackend: Searching for local CD
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  CommonBackend: Searching for local ISO
05-23 21:23 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:23 DEBUG  TaskList: New task get_metalink
05-23 21:23 DEBUG  TaskList: ### Running get_metalink...
05-23 21:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:23 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:23 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:23 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:23 DEBUG  TaskList: ### Finished get_metalink
05-23 21:23 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:23 DEBUG  TaskList: # Cancelling tasklist
05-23 21:23 DEBUG  TaskList: # Finished tasklist
05-23 21:23 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 22:11 INFO   root: === wubi 11.04 rev211 ===
05-23 22:11 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 22:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 22:11 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data
05-23 22:11 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\bin\7z.exe
05-23 22:11 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 22:11 DEBUG  CommonBackend: Fetching basic info...
05-23 22:11 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 22:11 DEBUG  CommonBackend: platform=win32
05-23 22:11 DEBUG  CommonBackend: osname=nt
05-23 22:11 DEBUG  CommonBackend: language=en_GB
05-23 22:11 DEBUG  CommonBackend: encoding=cp1252
05-23 22:11 DEBUG  WindowsBackend: arch=amd64
05-23 22:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\isolist.ini
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 22:11 DEBUG  WindowsBackend: Fetching host info...
05-23 22:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 22:11 DEBUG  WindowsBackend: windows version=vista
05-23 22:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 22:11 DEBUG  WindowsBackend: windows_sp=None
05-23 22:11 DEBUG  WindowsBackend: windows_build=7600
05-23 22:11 DEBUG  WindowsBackend: gmt=0
05-23 22:11 DEBUG  WindowsBackend: country=GB
05-23 22:11 DEBUG  WindowsBackend: timezone=Europe/London
05-23 22:11 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: windows_language_code=1033
05-23 22:11 DEBUG  WindowsBackend: windows_language=English
05-23 22:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 22:11 DEBUG  WindowsBackend: bootloader=vista
05-23 22:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174427.644531 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(C: hd 174427.644531 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 22:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 22:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 22:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 22:11 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 22:11 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 22:11 DEBUG  WindowsBackend: keyboard_variant=
05-23 22:11 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 22:11 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 22:11 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 22:11 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 22:11 DEBUG  CommonBackend: Searching for local CDs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 INFO   root: Already installed, running the uninstaller...
05-23 22:11 INFO   root: Running the uninstaller...
05-23 22:11 INFO   CommonBackend: This is the uninstaller running
05-23 22:11 DEBUG  WindowsFrontend: __init__...
05-23 22:11 DEBUG  WindowsFrontend: on_init...
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 INFO   root: Received settings
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 DEBUG  TaskList: # Running tasklist...
05-23 22:11 DEBUG  TaskList: ## Running Backup ISO...
05-23 22:11 DEBUG  TaskList: ## Finished Backup ISO
05-23 22:11 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 22:11 DEBUG  WindowsBackend: Could not find bcd id
05-23 22:11 DEBUG  WindowsBackend: undo_bootini C:
05-23 22:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174427.644531 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: undo_bootini Q:
05-23 22:11 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 22:11 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 22:11 DEBUG  TaskList: ## Running Remove target dir....
05-23 22:11 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 22:11 DEBUG  TaskList: ## Finished Remove target dir.
05-23 22:11 DEBUG  TaskList: ## Running Remove registry key....
05-23 22:11 DEBUG  TaskList: ## Finished Remove registry key.
05-23 22:11 DEBUG  TaskList: # Finished tasklist
05-23 22:11 INFO   root: Almost finished uninstalling
05-23 22:11 INFO   root: Finished uninstallation
05-23 22:11 DEBUG  CommonBackend: Fetching basic info...
05-23 22:11 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 22:11 DEBUG  CommonBackend: platform=win32
05-23 22:11 DEBUG  CommonBackend: osname=nt
05-23 22:11 DEBUG  WindowsBackend: arch=amd64
05-23 22:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\isolist.ini
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 22:11 DEBUG  WindowsBackend: Fetching host info...
05-23 22:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 22:11 DEBUG  WindowsBackend: windows version=vista
05-23 22:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 22:11 DEBUG  WindowsBackend: windows_sp=None
05-23 22:11 DEBUG  WindowsBackend: windows_build=7600
05-23 22:11 DEBUG  WindowsBackend: gmt=0
05-23 22:11 DEBUG  WindowsBackend: country=GB
05-23 22:11 DEBUG  WindowsBackend: timezone=Europe/London
05-23 22:11 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: windows_language_code=1033
05-23 22:11 DEBUG  WindowsBackend: windows_language=English
05-23 22:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 22:11 DEBUG  WindowsBackend: bootloader=vista
05-23 22:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174429.285156 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(C: hd 174429.285156 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 22:11 DEBUG  WindowsBackend: uninstaller_path=None
05-23 22:11 DEBUG  WindowsBackend: previous_target_dir=None
05-23 22:11 DEBUG  WindowsBackend: previous_distro_name=None
05-23 22:11 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 22:11 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 22:11 DEBUG  WindowsBackend: keyboard_variant=
05-23 22:11 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 22:11 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 22:11 DEBUG  CommonBackend: Searching for local CDs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 INFO   root: Running the installer...
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 22:11 INFO   root: Received settings
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 DEBUG  TaskList: # Running tasklist...
05-23 22:11 DEBUG  TaskList: ## Running select_target_dir...
05-23 22:11 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 22:11 DEBUG  TaskList: ## Finished select_target_dir
05-23 22:11 DEBUG  TaskList: ## Running create_dir_structure...
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 22:11 DEBUG  TaskList: ## Finished create_dir_structure
05-23 22:11 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 22:11 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 22:11 DEBUG  TaskList: ## Running create_uninstaller...
05-23 22:11 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 22:11 DEBUG  TaskList: ## Finished create_uninstaller
05-23 22:11 DEBUG  TaskList: ## Running copy_installation_files...
05-23 22:11 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 22:11 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\winboot -> C:\ubuntu\winboot
05-23 22:11 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 22:11 DEBUG  TaskList: ## Finished copy_installation_files
05-23 22:11 DEBUG  TaskList: ## Running get_iso...
05-23 22:11 DEBUG  CommonBackend: Searching for local CD
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  CommonBackend: Searching for local ISO
05-23 22:11 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 22:11 DEBUG  TaskList: New task get_metalink
05-23 22:11 DEBUG  TaskList: ### Running get_metalink...
05-23 22:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 22:11 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 22:11 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 22:11 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 22:11 DEBUG  TaskList: ### Finished get_metalink
05-23 22:11 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 22:11 DEBUG  TaskList: # Cancelling tasklist
05-23 22:11 DEBUG  TaskList: # Finished tasklist
05-23 22:11 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO

---

### Post by wildmanne39 on 2011-05-23
> **Lodi666 said:**
> It sais this:
 
 
05-23 21:01 INFO   root: === wubi 11.04 rev211 ===
05-23 21:01 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\PPQ9DQVM\\wubi[1].exe"']
05-23 21:01 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data
05-23 21:01 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\bin\7z.exe
05-23 21:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:01 DEBUG  CommonBackend: Fetching basic info...
05-23 21:01 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\PPQ9DQVM\wubi[1].exe
05-23 21:01 DEBUG  CommonBackend: platform=win32
05-23 21:01 DEBUG  CommonBackend: osname=nt
05-23 21:01 DEBUG  CommonBackend: language=en_GB
05-23 21:01 DEBUG  CommonBackend: encoding=cp1252
05-23 21:01 DEBUG  WindowsBackend: arch=amd64
05-23 21:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data\isolist.ini
05-23 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:01 DEBUG  WindowsBackend: Fetching host info...
05-23 21:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:01 DEBUG  WindowsBackend: windows version=vista
05-23 21:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:01 DEBUG  WindowsBackend: windows_sp=None
05-23 21:01 DEBUG  WindowsBackend: windows_build=7600
05-23 21:01 DEBUG  WindowsBackend: gmt=0
05-23 21:01 DEBUG  WindowsBackend: country=GB
05-23 21:01 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:01 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:01 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:01 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:01 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:01 DEBUG  WindowsBackend: windows_language=English
05-23 21:01 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:01 DEBUG  WindowsBackend: bootloader=vista
05-23 21:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174779.617188 mb free ntfs)
05-23 21:01 DEBUG  WindowsBackend: drive=Drive(C: hd 174779.617188 mb free ntfs)
05-23 21:01 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:01 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:01 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:01 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:01 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:01 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:01 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:01 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:01 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:01 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:01 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:01 DEBUG  CommonBackend: Searching for local CDs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu Netbook CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:01 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:01 INFO   root: Running the installer...
05-23 21:01 DEBUG  WindowsFrontend: __init__...
05-23 21:01 DEBUG  WindowsFrontend: on_init...
05-23 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\translations, languages=['en_GB', 'en']
05-23 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\translations, languages=['en_GB', 'en']
05-23 21:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:02 INFO   root: Received settings
05-23 21:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\translations, languages=['en_GB', 'en']
05-23 21:02 DEBUG  TaskList: # Running tasklist...
05-23 21:02 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:02 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:02 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:02 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:02 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:02 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:02 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:02 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\PPQ9DQVM\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:02 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:02 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:02 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:02 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\winboot -> C:\ubuntu\winboot
05-23 21:02 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:02 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:02 DEBUG  TaskList: ## Running get_iso...
05-23 21:02 DEBUG  CommonBackend: Searching for local CD
05-23 21:02 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp is a valid Ubuntu Netbook CD
05-23 21:02 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylD6BF.tmp\casper\filesystem.squashfs
05-23 21:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:02 DEBUG  CommonBackend: Searching for local ISO
05-23 21:02 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:02 DEBUG  TaskList: New task get_metalink
05-23 21:02 DEBUG  TaskList: ### Running get_metalink...
05-23 21:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:02 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:02 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:02 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:02 DEBUG  TaskList: ### Finished get_metalink
05-23 21:02 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:02 DEBUG  TaskList: # Cancelling tasklist
05-23 21:02 DEBUG  TaskList: # Finished tasklist
05-23 21:02 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:05 INFO   root: === wubi 11.04 rev211 ===
05-23 21:05 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\J5OFP1MQ\\wubi[1].exe"']
05-23 21:05 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data
05-23 21:05 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\bin\7z.exe
05-23 21:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:05 DEBUG  CommonBackend: Fetching basic info...
05-23 21:05 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\J5OFP1MQ\wubi[1].exe
05-23 21:05 DEBUG  CommonBackend: platform=win32
05-23 21:05 DEBUG  CommonBackend: osname=nt
05-23 21:05 DEBUG  CommonBackend: language=en_GB
05-23 21:05 DEBUG  CommonBackend: encoding=cp1252
05-23 21:05 DEBUG  WindowsBackend: arch=amd64
05-23 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\isolist.ini
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:05 DEBUG  WindowsBackend: Fetching host info...
05-23 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:05 DEBUG  WindowsBackend: windows version=vista
05-23 21:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:05 DEBUG  WindowsBackend: windows_sp=None
05-23 21:05 DEBUG  WindowsBackend: windows_build=7600
05-23 21:05 DEBUG  WindowsBackend: gmt=0
05-23 21:05 DEBUG  WindowsBackend: country=GB
05-23 21:05 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:05 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:05 DEBUG  WindowsBackend: windows_language=English
05-23 21:05 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:05 DEBUG  WindowsBackend: bootloader=vista
05-23 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174765.773438 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 174765.773438 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 21:05 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:05 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:05 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:05 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:05 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:05 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:05 DEBUG  CommonBackend: Searching for local CDs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 INFO   root: Already installed, running the uninstaller...
05-23 21:05 INFO   root: Running the uninstaller...
05-23 21:05 INFO   CommonBackend: This is the uninstaller running
05-23 21:05 DEBUG  WindowsFrontend: __init__...
05-23 21:05 DEBUG  WindowsFrontend: on_init...
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:05 INFO   root: Received settings
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:05 DEBUG  TaskList: # Running tasklist...
05-23 21:05 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:05 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:05 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:05 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:05 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174765.773438 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:05 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:05 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:05 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:05 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:05 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:05 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:05 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:05 DEBUG  TaskList: # Finished tasklist
05-23 21:05 INFO   root: Almost finished uninstalling
05-23 21:05 INFO   root: Finished uninstallation
05-23 21:05 DEBUG  CommonBackend: Fetching basic info...
05-23 21:05 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\J5OFP1MQ\wubi[1].exe
05-23 21:05 DEBUG  CommonBackend: platform=win32
05-23 21:05 DEBUG  CommonBackend: osname=nt
05-23 21:05 DEBUG  WindowsBackend: arch=amd64
05-23 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\isolist.ini
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:05 DEBUG  WindowsBackend: Fetching host info...
05-23 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:05 DEBUG  WindowsBackend: windows version=vista
05-23 21:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:05 DEBUG  WindowsBackend: windows_sp=None
05-23 21:05 DEBUG  WindowsBackend: windows_build=7600
05-23 21:05 DEBUG  WindowsBackend: gmt=0
05-23 21:05 DEBUG  WindowsBackend: country=GB
05-23 21:05 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:05 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:05 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:05 DEBUG  WindowsBackend: windows_language=English
05-23 21:05 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:05 DEBUG  WindowsBackend: bootloader=vista
05-23 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174767.152344 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 174767.152344 mb free ntfs)
05-23 21:05 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:05 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:05 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:05 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:05 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:05 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:05 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:05 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:05 DEBUG  CommonBackend: Searching for local CDs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:05 INFO   root: Running the installer...
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:07 INFO   root: Received settings
05-23 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\translations, languages=['en_GB', 'en']
05-23 21:07 DEBUG  TaskList: # Running tasklist...
05-23 21:07 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:07 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:07 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:07 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:07 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:07 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:07 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:07 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\J5OFP1MQ\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:07 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:07 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:07 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:07 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\winboot -> C:\ubuntu\winboot
05-23 21:07 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:07 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:07 DEBUG  TaskList: ## Running get_iso...
05-23 21:07 DEBUG  CommonBackend: Searching for local CD
05-23 21:07 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp is a valid Ubuntu Netbook CD
05-23 21:07 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl5244.tmp\casper\filesystem.squashfs
05-23 21:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:07 DEBUG  CommonBackend: Searching for local ISO
05-23 21:07 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:07 DEBUG  TaskList: New task get_metalink
05-23 21:07 DEBUG  TaskList: ### Running get_metalink...
05-23 21:07 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:07 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:07 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:07 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:07 DEBUG  TaskList: ### Finished get_metalink
05-23 21:07 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:07 DEBUG  TaskList: # Cancelling tasklist
05-23 21:07 DEBUG  TaskList: # Finished tasklist
05-23 21:07 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:15 INFO   root: === wubi 11.04 rev211 ===
05-23 21:15 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 21:15 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data
05-23 21:15 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\bin\7z.exe
05-23 21:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:15 DEBUG  CommonBackend: Fetching basic info...
05-23 21:15 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:15 DEBUG  CommonBackend: platform=win32
05-23 21:15 DEBUG  CommonBackend: osname=nt
05-23 21:15 DEBUG  CommonBackend: language=en_GB
05-23 21:15 DEBUG  CommonBackend: encoding=cp1252
05-23 21:15 DEBUG  WindowsBackend: arch=amd64
05-23 21:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\isolist.ini
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:15 DEBUG  WindowsBackend: Fetching host info...
05-23 21:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:15 DEBUG  WindowsBackend: windows version=vista
05-23 21:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:15 DEBUG  WindowsBackend: windows_sp=None
05-23 21:15 DEBUG  WindowsBackend: windows_build=7600
05-23 21:15 DEBUG  WindowsBackend: gmt=0
05-23 21:15 DEBUG  WindowsBackend: country=GB
05-23 21:15 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:15 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:15 DEBUG  WindowsBackend: windows_language=English
05-23 21:15 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:15 DEBUG  WindowsBackend: bootloader=vista
05-23 21:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174665.800781 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(C: hd 174665.800781 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 21:15 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:15 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:15 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:15 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:15 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:15 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:15 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:15 DEBUG  CommonBackend: Searching for local CDs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 INFO   root: Already installed, running the uninstaller...
05-23 21:15 INFO   root: Running the uninstaller...
05-23 21:15 INFO   CommonBackend: This is the uninstaller running
05-23 21:15 DEBUG  WindowsFrontend: __init__...
05-23 21:15 DEBUG  WindowsFrontend: on_init...
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:15 INFO   root: Received settings
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:15 DEBUG  TaskList: # Running tasklist...
05-23 21:15 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:15 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:15 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:15 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:15 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174665.800781 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:15 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:15 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:15 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:15 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:15 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:15 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:15 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:15 DEBUG  TaskList: # Finished tasklist
05-23 21:15 INFO   root: Almost finished uninstalling
05-23 21:15 INFO   root: Finished uninstallation
05-23 21:15 DEBUG  CommonBackend: Fetching basic info...
05-23 21:15 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:15 DEBUG  CommonBackend: platform=win32
05-23 21:15 DEBUG  CommonBackend: osname=nt
05-23 21:15 DEBUG  WindowsBackend: arch=amd64
05-23 21:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\isolist.ini
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:15 DEBUG  WindowsBackend: Fetching host info...
05-23 21:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:15 DEBUG  WindowsBackend: windows version=vista
05-23 21:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:15 DEBUG  WindowsBackend: windows_sp=None
05-23 21:15 DEBUG  WindowsBackend: windows_build=7600
05-23 21:15 DEBUG  WindowsBackend: gmt=0
05-23 21:15 DEBUG  WindowsBackend: country=GB
05-23 21:15 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:15 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:15 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:15 DEBUG  WindowsBackend: windows_language=English
05-23 21:15 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:15 DEBUG  WindowsBackend: bootloader=vista
05-23 21:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174667.441406 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(C: hd 174667.441406 mb free ntfs)
05-23 21:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:15 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:15 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:15 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:15 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:15 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:15 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:15 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:15 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:15 DEBUG  CommonBackend: Searching for local CDs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:15 INFO   root: Running the installer...
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:16 INFO   root: Received settings
05-23 21:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\translations, languages=['en_GB', 'en']
05-23 21:16 DEBUG  TaskList: # Running tasklist...
05-23 21:16 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:16 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:16 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:16 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:16 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:16 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:16 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:16 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:16 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:16 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:16 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:16 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\winboot -> C:\ubuntu\winboot
05-23 21:16 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:16 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:16 DEBUG  TaskList: ## Running get_iso...
05-23 21:16 DEBUG  CommonBackend: Searching for local CD
05-23 21:16 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp is a valid Ubuntu Netbook CD
05-23 21:16 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylBBB0.tmp\casper\filesystem.squashfs
05-23 21:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:16 DEBUG  CommonBackend: Searching for local ISO
05-23 21:16 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:16 DEBUG  TaskList: New task get_metalink
05-23 21:16 DEBUG  TaskList: ### Running get_metalink...
05-23 21:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:16 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-23 21:16 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:16 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-23 21:16 DEBUG  TaskList: ### Finished get_metalink
05-23 21:16 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:16 DEBUG  TaskList: # Cancelling tasklist
05-23 21:16 DEBUG  TaskList: # Finished tasklist
05-23 21:16 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:17 INFO   root: === wubi 11.04 rev211 ===
05-23 21:17 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 21:17 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data
05-23 21:17 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\bin\7z.exe
05-23 21:17 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:17 DEBUG  CommonBackend: Fetching basic info...
05-23 21:17 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:17 DEBUG  CommonBackend: platform=win32
05-23 21:17 DEBUG  CommonBackend: osname=nt
05-23 21:17 DEBUG  CommonBackend: language=en_GB
05-23 21:17 DEBUG  CommonBackend: encoding=cp1252
05-23 21:17 DEBUG  WindowsBackend: arch=amd64
05-23 21:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\isolist.ini
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:17 DEBUG  WindowsBackend: Fetching host info...
05-23 21:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:17 DEBUG  WindowsBackend: windows version=vista
05-23 21:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:17 DEBUG  WindowsBackend: windows_sp=None
05-23 21:17 DEBUG  WindowsBackend: windows_build=7600
05-23 21:17 DEBUG  WindowsBackend: gmt=0
05-23 21:17 DEBUG  WindowsBackend: country=GB
05-23 21:17 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:17 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:17 DEBUG  WindowsBackend: windows_language=English
05-23 21:17 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:17 DEBUG  WindowsBackend: bootloader=vista
05-23 21:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174723.125 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(C: hd 174723.125 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 21:17 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:17 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:17 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:17 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:17 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:17 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:17 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:17 DEBUG  CommonBackend: Searching for local CDs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 INFO   root: Already installed, running the uninstaller...
05-23 21:17 INFO   root: Running the uninstaller...
05-23 21:17 INFO   CommonBackend: This is the uninstaller running
05-23 21:17 DEBUG  WindowsFrontend: __init__...
05-23 21:17 DEBUG  WindowsFrontend: on_init...
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:17 INFO   root: Received settings
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:17 DEBUG  TaskList: # Running tasklist...
05-23 21:17 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:17 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:17 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:17 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:17 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174723.125 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:17 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:17 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:17 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:17 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:17 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:17 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:17 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:17 DEBUG  TaskList: # Finished tasklist
05-23 21:17 INFO   root: Almost finished uninstalling
05-23 21:17 INFO   root: Finished uninstallation
05-23 21:17 DEBUG  CommonBackend: Fetching basic info...
05-23 21:17 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:17 DEBUG  CommonBackend: platform=win32
05-23 21:17 DEBUG  CommonBackend: osname=nt
05-23 21:17 DEBUG  WindowsBackend: arch=amd64
05-23 21:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\isolist.ini
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:17 DEBUG  WindowsBackend: Fetching host info...
05-23 21:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:17 DEBUG  WindowsBackend: windows version=vista
05-23 21:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:17 DEBUG  WindowsBackend: windows_sp=None
05-23 21:17 DEBUG  WindowsBackend: windows_build=7600
05-23 21:17 DEBUG  WindowsBackend: gmt=0
05-23 21:17 DEBUG  WindowsBackend: country=GB
05-23 21:17 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:17 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:17 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:17 DEBUG  WindowsBackend: windows_language=English
05-23 21:17 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:17 DEBUG  WindowsBackend: bootloader=vista
05-23 21:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174724.632813 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(C: hd 174724.632813 mb free ntfs)
05-23 21:17 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:17 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:17 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:17 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:17 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:17 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:17 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:17 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:17 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:17 DEBUG  CommonBackend: Searching for local CDs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:17 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:17 INFO   root: Running the installer...
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:18 INFO   root: Received settings
05-23 21:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\translations, languages=['en_GB', 'en']
05-23 21:18 DEBUG  TaskList: # Running tasklist...
05-23 21:18 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:18 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:18 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:18 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:18 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:18 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:18 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:18 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:18 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:18 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:18 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:18 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:18 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\winboot -> C:\ubuntu\winboot
05-23 21:18 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-23 21:18 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:18 DEBUG  TaskList: ## Running get_iso...
05-23 21:18 DEBUG  CommonBackend: Searching for local CD
05-23 21:18 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp is a valid Ubuntu CD
05-23 21:18 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylCE46.tmp\casper\filesystem.squashfs
05-23 21:18 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:18 DEBUG  CommonBackend: Searching for local ISO
05-23 21:18 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:18 DEBUG  TaskList: New task get_metalink
05-23 21:18 DEBUG  TaskList: ### Running get_metalink...
05-23 21:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-23 21:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-23 21:18 DEBUG  downloader: download finished (read 28363 bytes)
05-23 21:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-23 21:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-23 21:18 DEBUG  downloader: download finished (read 874 bytes)
05-23 21:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-23 21:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-23 21:18 DEBUG  downloader: download finished (read 198 bytes)
05-23 21:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-23 21:18 INFO   saplog: Checking block bindings..
05-23 21:18 INFO   saplog: Key verified successfully.
05-23 21:18 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink
05-23 21:18 DEBUG  TaskList: ### Finished get_metalink
05-23 21:18 DEBUG  TaskList: New task download
05-23 21:18 DEBUG  TaskList: ### Running download...
05-23 21:18 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-23 21:22 INFO   WindowsFrontend: Operation cancelled
05-23 21:22 DEBUG  WindowsFrontend: frontend.quit
05-23 21:22 DEBUG  WindowsFrontend: frontend.on_quit
05-23 21:22 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-23 21:22 DEBUG  TaskList: # Cancelling tasklist
05-23 21:22 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-23 21:22 DEBUG  root: application.on_quit
05-23 21:22 DEBUG  root: Forceful exit
05-23 21:22 INFO   root: sys.exit
05-23 21:23 INFO   root: === wubi 11.04 rev211 ===
05-23 21:23 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 21:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 21:23 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data
05-23 21:23 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\bin\7z.exe
05-23 21:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 21:23 DEBUG  CommonBackend: Fetching basic info...
05-23 21:23 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:23 DEBUG  CommonBackend: platform=win32
05-23 21:23 DEBUG  CommonBackend: osname=nt
05-23 21:23 DEBUG  CommonBackend: language=en_GB
05-23 21:23 DEBUG  CommonBackend: encoding=cp1252
05-23 21:23 DEBUG  WindowsBackend: arch=amd64
05-23 21:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\isolist.ini
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:23 DEBUG  WindowsBackend: Fetching host info...
05-23 21:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:23 DEBUG  WindowsBackend: windows version=vista
05-23 21:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:23 DEBUG  WindowsBackend: windows_sp=None
05-23 21:23 DEBUG  WindowsBackend: windows_build=7600
05-23 21:23 DEBUG  WindowsBackend: gmt=0
05-23 21:23 DEBUG  WindowsBackend: country=GB
05-23 21:23 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:23 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:23 DEBUG  WindowsBackend: windows_language=English
05-23 21:23 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:23 DEBUG  WindowsBackend: bootloader=vista
05-23 21:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174715.09375 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(C: hd 174715.09375 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:23 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 21:23 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 21:23 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-23 21:23 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:23 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:23 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:23 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 21:23 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 21:23 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:23 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:23 DEBUG  CommonBackend: Searching for local CDs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 INFO   root: Already installed, running the uninstaller...
05-23 21:23 INFO   root: Running the uninstaller...
05-23 21:23 INFO   CommonBackend: This is the uninstaller running
05-23 21:23 DEBUG  WindowsFrontend: __init__...
05-23 21:23 DEBUG  WindowsFrontend: on_init...
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 INFO   root: Received settings
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 DEBUG  TaskList: # Running tasklist...
05-23 21:23 DEBUG  TaskList: ## Running Backup ISO...
05-23 21:23 DEBUG  TaskList: ## Finished Backup ISO
05-23 21:23 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 21:23 DEBUG  WindowsBackend: Could not find bcd id
05-23 21:23 DEBUG  WindowsBackend: undo_bootini C:
05-23 21:23 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174715.09375 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: undo_bootini Q:
05-23 21:23 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 21:23 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 21:23 DEBUG  TaskList: ## Running Remove target dir....
05-23 21:23 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 21:23 DEBUG  TaskList: ## Finished Remove target dir.
05-23 21:23 DEBUG  TaskList: ## Running Remove registry key....
05-23 21:23 DEBUG  TaskList: ## Finished Remove registry key.
05-23 21:23 DEBUG  TaskList: # Finished tasklist
05-23 21:23 INFO   root: Almost finished uninstalling
05-23 21:23 INFO   root: Finished uninstallation
05-23 21:23 DEBUG  CommonBackend: Fetching basic info...
05-23 21:23 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 21:23 DEBUG  CommonBackend: platform=win32
05-23 21:23 DEBUG  CommonBackend: osname=nt
05-23 21:23 DEBUG  WindowsBackend: arch=amd64
05-23 21:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\isolist.ini
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 21:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 21:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 21:23 DEBUG  WindowsBackend: Fetching host info...
05-23 21:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 21:23 DEBUG  WindowsBackend: windows version=vista
05-23 21:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 21:23 DEBUG  WindowsBackend: windows_sp=None
05-23 21:23 DEBUG  WindowsBackend: windows_build=7600
05-23 21:23 DEBUG  WindowsBackend: gmt=0
05-23 21:23 DEBUG  WindowsBackend: country=GB
05-23 21:23 DEBUG  WindowsBackend: timezone=Europe/London
05-23 21:23 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 21:23 DEBUG  WindowsBackend: windows_language_code=1033
05-23 21:23 DEBUG  WindowsBackend: windows_language=English
05-23 21:23 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 21:23 DEBUG  WindowsBackend: bootloader=vista
05-23 21:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174716.636719 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(C: hd 174716.636719 mb free ntfs)
05-23 21:23 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 21:23 DEBUG  WindowsBackend: uninstaller_path=None
05-23 21:23 DEBUG  WindowsBackend: previous_target_dir=None
05-23 21:23 DEBUG  WindowsBackend: previous_distro_name=None
05-23 21:23 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 21:23 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 21:23 DEBUG  WindowsBackend: keyboard_variant=
05-23 21:23 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 21:23 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 21:23 DEBUG  CommonBackend: Searching for local CDs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 INFO   root: Running the installer...
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 21:23 INFO   root: Received settings
05-23 21:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\translations, languages=['en_GB', 'en']
05-23 21:23 DEBUG  TaskList: # Running tasklist...
05-23 21:23 DEBUG  TaskList: ## Running select_target_dir...
05-23 21:23 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 21:23 DEBUG  TaskList: ## Finished select_target_dir
05-23 21:23 DEBUG  TaskList: ## Running create_dir_structure...
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 21:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 21:23 DEBUG  TaskList: ## Finished create_dir_structure
05-23 21:23 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 21:23 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 21:23 DEBUG  TaskList: ## Running create_uninstaller...
05-23 21:23 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 21:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 21:23 DEBUG  TaskList: ## Finished create_uninstaller
05-23 21:23 DEBUG  TaskList: ## Running copy_installation_files...
05-23 21:23 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 21:23 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\winboot -> C:\ubuntu\winboot
05-23 21:23 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 21:23 DEBUG  TaskList: ## Finished copy_installation_files
05-23 21:23 DEBUG  TaskList: ## Running get_iso...
05-23 21:23 DEBUG  CommonBackend: Searching for local CD
05-23 21:23 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pyl8804.tmp\casper\filesystem.squashfs
05-23 21:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 21:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 21:23 DEBUG  CommonBackend: Searching for local ISO
05-23 21:23 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 21:23 DEBUG  TaskList: New task get_metalink
05-23 21:23 DEBUG  TaskList: ### Running get_metalink...
05-23 21:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:23 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:23 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 21:23 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 21:23 DEBUG  TaskList: ### Finished get_metalink
05-23 21:23 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 21:23 DEBUG  TaskList: # Cancelling tasklist
05-23 21:23 DEBUG  TaskList: # Finished tasklist
05-23 21:23 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 22:11 INFO   root: === wubi 11.04 rev211 ===
05-23 22:11 DEBUG  root: Logfile is c:\users\troubl~1\appdata\local\temp\wubi-11.04-rev211.log
05-23 22:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Trouble Maker\\Downloads\\wubi.exe"']
05-23 22:11 DEBUG  CommonBackend: data_dir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data
05-23 22:11 DEBUG  WindowsBackend: 7z=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\bin\7z.exe
05-23 22:11 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 22:11 DEBUG  CommonBackend: Fetching basic info...
05-23 22:11 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 22:11 DEBUG  CommonBackend: platform=win32
05-23 22:11 DEBUG  CommonBackend: osname=nt
05-23 22:11 DEBUG  CommonBackend: language=en_GB
05-23 22:11 DEBUG  CommonBackend: encoding=cp1252
05-23 22:11 DEBUG  WindowsBackend: arch=amd64
05-23 22:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\isolist.ini
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 22:11 DEBUG  WindowsBackend: Fetching host info...
05-23 22:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 22:11 DEBUG  WindowsBackend: windows version=vista
05-23 22:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 22:11 DEBUG  WindowsBackend: windows_sp=None
05-23 22:11 DEBUG  WindowsBackend: windows_build=7600
05-23 22:11 DEBUG  WindowsBackend: gmt=0
05-23 22:11 DEBUG  WindowsBackend: country=GB
05-23 22:11 DEBUG  WindowsBackend: timezone=Europe/London
05-23 22:11 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: windows_language_code=1033
05-23 22:11 DEBUG  WindowsBackend: windows_language=English
05-23 22:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 22:11 DEBUG  WindowsBackend: bootloader=vista
05-23 22:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174427.644531 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(C: hd 174427.644531 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 22:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 22:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 22:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-23 22:11 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 22:11 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 22:11 DEBUG  WindowsBackend: keyboard_variant=
05-23 22:11 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
05-23 22:11 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-23 22:11 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 22:11 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 22:11 DEBUG  CommonBackend: Searching for local CDs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 INFO   root: Already installed, running the uninstaller...
05-23 22:11 INFO   root: Running the uninstaller...
05-23 22:11 INFO   CommonBackend: This is the uninstaller running
05-23 22:11 DEBUG  WindowsFrontend: __init__...
05-23 22:11 DEBUG  WindowsFrontend: on_init...
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 INFO   root: Received settings
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 DEBUG  TaskList: # Running tasklist...
05-23 22:11 DEBUG  TaskList: ## Running Backup ISO...
05-23 22:11 DEBUG  TaskList: ## Finished Backup ISO
05-23 22:11 DEBUG  TaskList: ## Running Remove bootloader entry....
05-23 22:11 DEBUG  WindowsBackend: Could not find bcd id
05-23 22:11 DEBUG  WindowsBackend: undo_bootini C:
05-23 22:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 174427.644531 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: undo_bootini Q:
05-23 22:11 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
05-23 22:11 DEBUG  TaskList: ## Finished Remove bootloader entry.
05-23 22:11 DEBUG  TaskList: ## Running Remove target dir....
05-23 22:11 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 22:11 DEBUG  TaskList: ## Finished Remove target dir.
05-23 22:11 DEBUG  TaskList: ## Running Remove registry key....
05-23 22:11 DEBUG  TaskList: ## Finished Remove registry key.
05-23 22:11 DEBUG  TaskList: # Finished tasklist
05-23 22:11 INFO   root: Almost finished uninstalling
05-23 22:11 INFO   root: Finished uninstallation
05-23 22:11 DEBUG  CommonBackend: Fetching basic info...
05-23 22:11 DEBUG  CommonBackend: original_exe=C:\Users\Trouble Maker\Downloads\wubi.exe
05-23 22:11 DEBUG  CommonBackend: platform=win32
05-23 22:11 DEBUG  CommonBackend: osname=nt
05-23 22:11 DEBUG  WindowsBackend: arch=amd64
05-23 22:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\isolist.ini
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 22:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 22:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-23 22:11 DEBUG  WindowsBackend: Fetching host info...
05-23 22:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 22:11 DEBUG  WindowsBackend: windows version=vista
05-23 22:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-23 22:11 DEBUG  WindowsBackend: windows_sp=None
05-23 22:11 DEBUG  WindowsBackend: windows_build=7600
05-23 22:11 DEBUG  WindowsBackend: gmt=0
05-23 22:11 DEBUG  WindowsBackend: country=GB
05-23 22:11 DEBUG  WindowsBackend: timezone=Europe/London
05-23 22:11 DEBUG  WindowsBackend: windows_username=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_full_name=Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: user_directory=C:\Users\Trouble Maker
05-23 22:11 DEBUG  WindowsBackend: windows_language_code=1033
05-23 22:11 DEBUG  WindowsBackend: windows_language=English
05-23 22:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-23 22:11 DEBUG  WindowsBackend: bootloader=vista
05-23 22:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 174429.285156 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(C: hd 174429.285156 mb free ntfs)
05-23 22:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
05-23 22:11 DEBUG  WindowsBackend: uninstaller_path=None
05-23 22:11 DEBUG  WindowsBackend: previous_target_dir=None
05-23 22:11 DEBUG  WindowsBackend: previous_distro_name=None
05-23 22:11 DEBUG  WindowsBackend: keyboard_id=134809609
05-23 22:11 DEBUG  WindowsBackend: keyboard_layout=gb
05-23 22:11 DEBUG  WindowsBackend: keyboard_variant=
05-23 22:11 DEBUG  WindowsBackend: total_memory_mb=1013.09375
05-23 22:11 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 22:11 DEBUG  CommonBackend: Searching for local CDs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 INFO   root: Running the installer...
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_GB, locale=en_GB.UTF-8, username=troublemaker
05-23 22:11 INFO   root: Received settings
05-23 22:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\translations, languages=['en_GB', 'en']
05-23 22:11 DEBUG  TaskList: # Running tasklist...
05-23 22:11 DEBUG  TaskList: ## Running select_target_dir...
05-23 22:11 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 22:11 DEBUG  TaskList: ## Finished select_target_dir
05-23 22:11 DEBUG  TaskList: ## Running create_dir_structure...
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 22:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 22:11 DEBUG  TaskList: ## Finished create_dir_structure
05-23 22:11 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 22:11 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 22:11 DEBUG  TaskList: ## Running create_uninstaller...
05-23 22:11 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Trouble Maker\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 22:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 22:11 DEBUG  TaskList: ## Finished create_uninstaller
05-23 22:11 DEBUG  TaskList: ## Running copy_installation_files...
05-23 22:11 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 22:11 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\winboot -> C:\ubuntu\winboot
05-23 22:11 DEBUG  WindowsBackend: Copying C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-23 22:11 DEBUG  TaskList: ## Finished copy_installation_files
05-23 22:11 DEBUG  TaskList: ## Running get_iso...
05-23 22:11 DEBUG  CommonBackend: Searching for local CD
05-23 22:11 DEBUG  Distro:   checking whether C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain C:\Users\TROUBL~1\AppData\Local\Temp\pylC8CB.tmp\casper\filesystem.squashfs
05-23 22:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
05-23 22:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
05-23 22:11 DEBUG  CommonBackend: Searching for local ISO
05-23 22:11 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 22:11 DEBUG  TaskList: New task get_metalink
05-23 22:11 DEBUG  TaskList: ### Running get_metalink...
05-23 22:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
05-23 22:11 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 22:11 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
05-23 22:11 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
05-23 22:11 DEBUG  TaskList: ### Finished get_metalink
05-23 22:11 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 22:11 DEBUG  TaskList: # Cancelling tasklist
05-23 22:11 DEBUG  TaskList: # Finished tasklist
05-23 22:11 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
Hi, according to that message it can not connect to the server where those install files are or it connects and they are not there, try downloading from another server.

---

