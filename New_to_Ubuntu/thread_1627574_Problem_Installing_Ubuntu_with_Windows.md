---
title: "Problem Installing Ubuntu with Windows"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Draginz on 2010-11-21
Hey, I've had a growing interest in Linux over the past few months, and I decided to install Ubuntu alongside Windows (Wubi). After downloading the Wubi installer and running it, I get an error before it can finish installing. The error is:
```
 Cannot download the metalink and therefore the ISO
```I wasn't sure what to do about this, so I checked the text installation log, here is what it says:
```
11-21 11:49 INFO   root: === wubi 10.04.1 rev190 ===
11-21 11:49 DEBUG  root: Logfile is c:\docume~1\tyler\locals~1\temp\wubi-10.04.1-rev190.log
11-21 11:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Tyler\\Desktop\\wubi.exe"']
11-21 11:49 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\data
11-21 11:49 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\bin\7z.exe
11-21 11:49 DEBUG  CommonBackend: Fetching basic info...
11-21 11:49 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Tyler\Desktop\wubi.exe
11-21 11:49 DEBUG  CommonBackend: platform=win32
11-21 11:49 DEBUG  CommonBackend: osname=nt
11-21 11:49 DEBUG  CommonBackend: language=en_US
11-21 11:49 DEBUG  CommonBackend: encoding=cp1252
11-21 11:49 DEBUG  WindowsBackend: arch=i386
11-21 11:49 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\data\isolist.ini
11-21 11:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-21 11:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-21 11:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-21 11:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-21 11:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-21 11:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-21 11:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-21 11:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-21 11:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-21 11:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-21 11:49 DEBUG  WindowsBackend: Fetching host info...
11-21 11:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-21 11:49 DEBUG  WindowsBackend: windows version=xp
11-21 11:49 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-21 11:49 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-21 11:49 DEBUG  WindowsBackend: windows_build=2600
11-21 11:49 DEBUG  WindowsBackend: gmt=-8
11-21 11:49 DEBUG  WindowsBackend: country=US
11-21 11:49 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-21 11:49 DEBUG  WindowsBackend: windows_username=Tyler
11-21 11:49 DEBUG  WindowsBackend: user_full_name=Tyler
11-21 11:49 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Tyler
11-21 11:49 DEBUG  WindowsBackend: windows_language_code=1033
11-21 11:49 DEBUG  WindowsBackend: windows_language=English
11-21 11:49 DEBUG  WindowsBackend: processor_name=AMD Athlon(TM) XP 1500+
11-21 11:49 DEBUG  WindowsBackend: bootloader=xp
11-21 11:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60251.3632813 mb free ntfs)
11-21 11:49 DEBUG  WindowsBackend: drive=Drive(C: hd 60251.3632813 mb free ntfs)
11-21 11:49 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-21 11:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-21 11:49 DEBUG  WindowsBackend: drive=Drive(F: hd 116610.800781 mb free ntfs)
11-21 11:49 DEBUG  WindowsBackend: drive=Drive(G: hd 2168.91015625 mb free fat32)
11-21 11:49 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
11-21 11:49 DEBUG  WindowsBackend: uninstaller_path=None
11-21 11:49 DEBUG  WindowsBackend: previous_target_dir=None
11-21 11:49 DEBUG  WindowsBackend: previous_distro_name=None
11-21 11:49 DEBUG  WindowsBackend: keyboard_id=67699721
11-21 11:49 DEBUG  WindowsBackend: keyboard_layout=us
11-21 11:49 DEBUG  WindowsBackend: keyboard_variant=
11-21 11:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-21 11:49 DEBUG  CommonBackend: locale=en_US.UTF-8
11-21 11:49 DEBUG  WindowsBackend: total_memory_mb=1023.53125
11-21 11:49 DEBUG  CommonBackend: Searching ISOs on USB devices
11-21 11:49 DEBUG  CommonBackend: Searching for local CDs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Ubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Kubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 INFO   root: Running the installer...
11-21 11:49 DEBUG  WindowsFrontend: __init__...
11-21 11:49 DEBUG  WindowsFrontend: on_init...
11-21 11:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\translations, languages=['en_US', 'en']
11-21 11:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\translations, languages=['en_US', 'en']
11-21 11:49 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=draginz
11-21 11:49 INFO   root: Received settings
11-21 11:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\translations, languages=['en_US', 'en']
11-21 11:49 DEBUG  TaskList: # Running tasklist...
11-21 11:49 DEBUG  TaskList: ## Running select_target_dir...
11-21 11:49 INFO   WindowsBackend: Installing into F:\ubuntu
11-21 11:49 DEBUG  TaskList: ## Finished select_target_dir
11-21 11:49 DEBUG  TaskList: ## Running create_dir_structure...
11-21 11:49 DEBUG  CommonBackend: Creating dir F:\ubuntu
11-21 11:49 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
11-21 11:49 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
11-21 11:49 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
11-21 11:49 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
11-21 11:49 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
11-21 11:49 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
11-21 11:49 DEBUG  TaskList: ## Finished create_dir_structure
11-21 11:49 DEBUG  TaskList: ## Running uncompress_target_dir...
11-21 11:49 DEBUG  TaskList: ## Finished uncompress_target_dir
11-21 11:49 DEBUG  TaskList: ## Running create_uninstaller...
11-21 11:49 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Tyler\Desktop\wubi.exe -> F:\ubuntu\uninstall-wubi.exe
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString F:\ubuntu\uninstall-wubi.exe
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir F:\ubuntu
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon F:\ubuntu\Ubuntu.ico
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-21 11:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-21 11:49 DEBUG  TaskList: ## Finished create_uninstaller
11-21 11:49 DEBUG  TaskList: ## Running copy_installation_files...
11-21 11:49 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\data\custom-installation -> F:\ubuntu\install\custom-installation
11-21 11:49 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\winboot -> F:\ubuntu\winboot
11-21 11:49 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\data\images\Ubuntu.ico -> F:\ubuntu\Ubuntu.ico
11-21 11:49 DEBUG  TaskList: ## Finished copy_installation_files
11-21 11:49 DEBUG  TaskList: ## Running get_iso...
11-21 11:49 DEBUG  CommonBackend: Searching for local CD
11-21 11:49 DEBUG  Distro:   checking whether C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain C:\DOCUME~1\Tyler\LOCALS~1\Temp\pyl10EB.tmp\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-21 11:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-21 11:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-21 11:49 DEBUG  CommonBackend: Searching for local ISO
11-21 11:49 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-21 11:49 DEBUG  TaskList: New task get_metalink
11-21 11:49 DEBUG  TaskList: ### Running get_metalink...
11-21 11:49 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink > F:\ubuntu\install
11-21 11:49 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
11-21 11:49 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink > F:\ubuntu\install
11-21 11:49 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
11-21 11:49 DEBUG  TaskList: ### Finished get_metalink
11-21 11:49 ERROR  TaskList: Cannot download the metalink and therefore the ISO
[B]Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-21 11:49 DEBUG  TaskList: # Cancelling tasklist
11-21 11:49 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO[/B]
11-21 11:49 DEBUG  TaskList: # Finished tasklist

```Sorry for stretching the page. I've highlighted the error parts in bold.
Any help is greatly appreciated in advance.

---

### Post by Rex Bouwense on 2010-11-21
Wubi does not install Ubuntu side by side with Windows.  It installs Ubuntu inside of Windows.  Is that what you want to do?

---

### Post by carl4926 on 2010-11-21
Why on earth can't you download the .iso?
There are plenty of options for doing that.

---

### Post by Draginz on 2010-11-21
> **Rex Bouwense said:**
> Wubi does not install Ubuntu side by side with Windows.  It installs Ubuntu inside of Windows.  Is that what you want to do?
Yeah, that's what I meant. Do you know how I can fix it?

---

### Post by Rex Bouwense on 2010-11-21
Here is a simple explanation on U-Tube:  [http://www.youtube.com/watch?v=n5x9iJWXbUY](http://www.youtube.com/watch?v=n5x9iJWXbUY)
Enjoy.
By the way there is a wealth of information out there if you Google "Wubi install of Ubuntu".

---

### Post by Draginz on 2010-11-21
> **Rex Bouwense said:**
> Here is a simple explanation on U-Tube:  [http://www.youtube.com/watch?v=n5x9iJWXbUY](http://www.youtube.com/watch?v=n5x9iJWXbUY)
Enjoy.
By the way there is a wealth of information out there if you Google "Wubi install of Ubuntu".

Thank you very much, but I can't get the proper sound drivers for this computer at the moment, basically rendering the video useless to me.
Could you please give me a summary?
Thanks in advance.

---

### Post by Rex Bouwense on 2010-11-21
Here you go, step by step.  [http://seogadget.co.uk/the-ubuntu-installation-guide/#Install-with-Wubi](http://seogadget.co.uk/the-ubuntu-installation-guide/#Install-with-Wubi)

---

### Post by Draginz on 2010-11-21
> **Rex Bouwense said:**
> Here you go, step by step.  [http://seogadget.co.uk/the-ubuntu-installation-guide/#Install-with-Wubi](http://seogadget.co.uk/the-ubuntu-installation-guide/#Install-with-Wubi)

Right, I followed that guide to the word, and at the end of step five (clicking install) I got the same error as the one in the OP. 
I think I might just do the demo installation from a CD.

---

### Post by magnatron on 2010-11-21
> **Draginz said:**
> I can't get the proper sound drivers for this computer at the moment, basically rendering the video useless to me.

Erm, dont know if you knew this but configuration of hardware is done automattically during system initalization on most Linux distributions are you sure you want to run Ubuntu inside Windows and not the other way around!?

---

