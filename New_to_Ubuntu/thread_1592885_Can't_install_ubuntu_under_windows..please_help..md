---
title: "Can't install ubuntu under windows..please help."
date: 2010-10-11
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-10-11
I am trying to install ubuntu under windows but i am getting the following error...


it says, "installation failed....please see the log file in c:\users\amit\appdata\local\temp\wubi-10.04-rev-189.log"


and the file says,...


10-11 10:59 INFO   root: === wubi 10.04 rev189 ===
10-11 10:59 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-10.04-rev189.log
10-11 10:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
10-11 10:59 DEBUG  CommonBackend: data_dir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\data
10-11 10:59 DEBUG  WindowsBackend: 7z=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\bin\7z.exe
10-11 10:59 DEBUG  CommonBackend: Fetching basic info...
10-11 10:59 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-11 10:59 DEBUG  CommonBackend: platform=win32
10-11 10:59 DEBUG  CommonBackend: osname=nt
10-11 10:59 DEBUG  CommonBackend: language=en_US
10-11 10:59 DEBUG  CommonBackend: encoding=cp1252
10-11 10:59 DEBUG  WindowsBackend: arch=amd64
10-11 10:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\data\isolist.ini
10-11 10:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-11 10:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-11 10:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-11 10:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-11 10:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-11 10:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-11 10:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-11 10:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-11 10:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-11 10:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-11 10:59 DEBUG  WindowsBackend: Fetching host info...
10-11 10:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-11 10:59 DEBUG  WindowsBackend: windows version=vista
10-11 10:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-11 10:59 DEBUG  WindowsBackend: windows_sp=None
10-11 10:59 DEBUG  WindowsBackend: windows_build=7100
10-11 10:59 DEBUG  WindowsBackend: gmt=5
10-11 10:59 DEBUG  WindowsBackend: country=US
10-11 10:59 DEBUG  WindowsBackend: timezone=America/New_York
10-11 10:59 DEBUG  WindowsBackend: windows_username=amit
10-11 10:59 DEBUG  WindowsBackend: user_full_name=amit
10-11 10:59 DEBUG  WindowsBackend: user_directory=C:\Users\amit
10-11 10:59 DEBUG  WindowsBackend: windows_language_code=1033
10-11 10:59 DEBUG  WindowsBackend: windows_language=English
10-11 10:59 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
10-11 10:59 DEBUG  WindowsBackend: bootloader=vista
10-11 10:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14703.234375 mb free ntfs)
10-11 10:59 DEBUG  WindowsBackend: drive=Drive(C: hd 14703.234375 mb free ntfs)
10-11 10:59 DEBUG  WindowsBackend: drive=Drive(D: hd 8226.92578125 mb free ntfs)
10-11 10:59 DEBUG  WindowsBackend: drive=Drive(E: hd 84097.0664063 mb free ntfs)
10-11 10:59 DEBUG  WindowsBackend: drive=Drive(F: hd 69656.2265625 mb free ntfs)
10-11 10:59 DEBUG  WindowsBackend: drive=Drive(G: hd 59742.8984375 mb free ntfs)
10-11 10:59 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-11 10:59 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
10-11 10:59 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
10-11 10:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-11 10:59 DEBUG  WindowsBackend: keyboard_id=67699721
10-11 10:59 DEBUG  WindowsBackend: keyboard_layout=us
10-11 10:59 DEBUG  WindowsBackend: keyboard_variant=
10-11 10:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-11 10:59 DEBUG  CommonBackend: locale=en_US.UTF-8
10-11 10:59 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-11 10:59 DEBUG  CommonBackend: Searching ISOs on USB devices
10-11 10:59 DEBUG  CommonBackend: Searching for local CDs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Ubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Kubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-11 10:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 10:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-11 10:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
10-11 10:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
10-11 10:59 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-11 10:59 INFO   root: Running the CD menu...
10-11 10:59 DEBUG  WindowsFrontend: __init__...
10-11 10:59 DEBUG  WindowsFrontend: on_init...
10-11 10:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\translations, languages=['en_US', 'en']
10-11 10:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\translations, languages=['en_US', 'en']
10-11 10:59 INFO   root: CD menu finished
10-11 10:59 INFO   root: Already installed, running the uninstaller...
10-11 10:59 INFO   root: Running the uninstaller...
10-11 10:59 INFO   CommonBackend: This is the uninstaller running
10-11 10:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\translations, languages=['en_US', 'en']
10-11 11:00 INFO   root: Received settings
10-11 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\translations, languages=['en_US', 'en']
10-11 11:00 DEBUG  TaskList: # Running tasklist...
10-11 11:00 DEBUG  TaskList: ## Running Backup ISO...
10-11 11:00 DEBUG  TaskList: ## Finished Backup ISO
10-11 11:00 DEBUG  TaskList: ## Running Remove bootloader entry...
10-11 11:00 DEBUG  WindowsBackend: Could not find bcd id
10-11 11:00 DEBUG  WindowsBackend: undo_bootini C:
10-11 11:00 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 14703.234375 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: undo_bootini D:
10-11 11:00 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 8226.92578125 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: undo_bootini E:
10-11 11:00 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 84097.0664063 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: undo_bootini F:
10-11 11:00 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 69656.2265625 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: undo_bootini G:
10-11 11:00 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 59742.8984375 mb free ntfs)
10-11 11:00 DEBUG  TaskList: ## Finished Remove bootloader entry
10-11 11:00 DEBUG  TaskList: ## Running Remove target dir...
10-11 11:00 DEBUG  CommonBackend: Deleting G:\ubuntu
10-11 11:00 DEBUG  TaskList: ## Finished Remove target dir
10-11 11:00 DEBUG  TaskList: ## Running Remove registry key...
10-11 11:00 DEBUG  TaskList: ## Finished Remove registry key
10-11 11:00 DEBUG  TaskList: # Finished tasklist
10-11 11:00 INFO   root: Almost finished uninstalling
10-11 11:00 INFO   root: Finished uninstallation
10-11 11:00 DEBUG  CommonBackend: Fetching basic info...
10-11 11:00 DEBUG  CommonBackend: original_exe=H:\wubi.exe
10-11 11:00 DEBUG  CommonBackend: platform=win32
10-11 11:00 DEBUG  CommonBackend: osname=nt
10-11 11:00 DEBUG  WindowsBackend: arch=amd64
10-11 11:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\data\isolist.ini
10-11 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-11 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-11 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-11 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-11 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-11 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-11 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-11 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-11 11:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-11 11:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-11 11:00 DEBUG  WindowsBackend: Fetching host info...
10-11 11:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-11 11:00 DEBUG  WindowsBackend: windows version=vista
10-11 11:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-11 11:00 DEBUG  WindowsBackend: windows_sp=None
10-11 11:00 DEBUG  WindowsBackend: windows_build=7100
10-11 11:00 DEBUG  WindowsBackend: gmt=5
10-11 11:00 DEBUG  WindowsBackend: country=US
10-11 11:00 DEBUG  WindowsBackend: timezone=America/New_York
10-11 11:00 DEBUG  WindowsBackend: windows_username=amit
10-11 11:00 DEBUG  WindowsBackend: user_full_name=amit
10-11 11:00 DEBUG  WindowsBackend: user_directory=C:\Users\amit
10-11 11:00 DEBUG  WindowsBackend: windows_language_code=1033
10-11 11:00 DEBUG  WindowsBackend: windows_language=English
10-11 11:00 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
10-11 11:00 DEBUG  WindowsBackend: bootloader=vista
10-11 11:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14703.1757813 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: drive=Drive(C: hd 14703.1757813 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: drive=Drive(D: hd 8226.92578125 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: drive=Drive(E: hd 84097.0664063 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: drive=Drive(F: hd 69656.2265625 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: drive=Drive(G: hd 59907.4140625 mb free ntfs)
10-11 11:00 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-11 11:00 DEBUG  WindowsBackend: uninstaller_path=None
10-11 11:00 DEBUG  WindowsBackend: previous_target_dir=None
10-11 11:00 DEBUG  WindowsBackend: previous_distro_name=None
10-11 11:00 DEBUG  WindowsBackend: keyboard_id=67699721
10-11 11:00 DEBUG  WindowsBackend: keyboard_layout=us
10-11 11:00 DEBUG  WindowsBackend: keyboard_variant=
10-11 11:00 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-11 11:00 DEBUG  CommonBackend: Searching ISOs on USB devices
10-11 11:00 DEBUG  CommonBackend: Searching for local CDs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Ubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Kubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether C:\Users\amit\AppData\Local\Temp\pylD96E.tmp is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-11 11:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-11 11:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-11 11:00 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-11 11:00 INFO   root: Running the installer...
10-11 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\translations, languages=['en_US', 'en']
10-11 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\translations, languages=['en_US', 'en']
10-11 11:00 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=amit
10-11 11:00 INFO   root: Received settings
10-11 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\translations, languages=['en_US', 'en']
10-11 11:00 DEBUG  TaskList: # Running tasklist...
10-11 11:00 DEBUG  TaskList: ## Running select_target_dir...
10-11 11:00 INFO   WindowsBackend: Installing into G:\ubuntu
10-11 11:00 DEBUG  TaskList: ## Finished select_target_dir
10-11 11:00 DEBUG  TaskList: ## Running create_dir_structure...
10-11 11:00 DEBUG  CommonBackend: Creating dir G:\ubuntu
10-11 11:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
10-11 11:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
10-11 11:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
10-11 11:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
10-11 11:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
10-11 11:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
10-11 11:00 DEBUG  TaskList: ## Finished create_dir_structure
10-11 11:00 DEBUG  TaskList: ## Running uncompress_target_dir...
10-11 11:00 DEBUG  TaskList: ## Finished uncompress_target_dir
10-11 11:00 DEBUG  TaskList: ## Running create_uninstaller...
10-11 11:00 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-11 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-11 11:00 DEBUG  TaskList: ## Finished create_uninstaller
10-11 11:00 DEBUG  TaskList: ## Running copy_installation_files...
10-11 11:00 DEBUG  WindowsBackend: Copying C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
10-11 11:00 DEBUG  WindowsBackend: Copying C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\winboot -> G:\ubuntu\winboot
10-11 11:00 DEBUG  WindowsBackend: Copying C:\Users\amit\AppData\Local\Temp\pylD96E.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
10-11 11:00 DEBUG  TaskList: ## Finished copy_installation_files
10-11 11:00 DEBUG  TaskList: ## Running get_iso...
10-11 11:00 DEBUG  TaskList: New task copy_file
10-11 11:00 DEBUG  TaskList: ### Running copy_file...
10-11 11:06 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-11 11:06 DEBUG  TaskList: # Cancelling tasklist
10-11 11:06 DEBUG  TaskList: New task check_iso
10-11 11:06 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-11 11:06 DEBUG  CommonBackend: Searching for local ISO
10-11 11:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-11 11:06 DEBUG  TaskList: New task get_metalink
10-11 11:06 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-11 11:06 DEBUG  TaskList: # Cancelling tasklist
10-11 11:06 DEBUG  TaskList: # Finished tasklist

---

### Post by jtarin on 2010-10-11
Are you using a verified CD?

---

### Post by amityadav9314 on 2010-10-11
yes, i am using the verified cd
i downloaded the iso image from ubuntu.com and burn it.
but while installing it throws this error.

---

### Post by Rubi1200 on 2010-10-11
There appear to be new issues with Wubi in this release:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

---

### Post by Clever_Username on 2010-10-11
It looks like your using Wubi to install.
Doesn't Wubi download all the necessary files automagically making a cd unnecessary?
The log says it's checking the e drive, f drive etc.... Where are you trying to install Ubuntu? What were the steps that you took that preceded the error?

---

### Post by dcsoldschool53 on 2010-10-11
Is this windows 7

[Windows7 and ubuntu]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html")

---

### Post by amityadav9314 on 2010-10-11
yes I am doing it under windows 7

I have done it before but due to some reasons i uninstalled it and doing it again.

the steps that i followed prior the error are as follows..

First i burned a cd
then I click over the run setup file
then i choose to install it under windows
then i gave the destination drive to G:
the i put the password 
and then hit "next" to install it.

---

