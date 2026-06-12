---
title: "invalid arguement error during installation....  plz help"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by shiv0806 on 2011-07-04
m trying to install ubuntu inside windows xp.. bt it is showing "invalid arguement" error. i have even reinstalled the windows. plz help

here is the log file:
```

07-03 01:13 INFO   root: === wubi 9.04 rev128 ===
07-03 01:13 DEBUG  root: Logfile is c:\docume~1\pooja\locals~1\temp\wubi-9.04-rev128.log
07-03 01:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
07-03 01:13 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\data
07-03 01:13 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\bin\7z.exe
07-03 01:13 DEBUG  CommonBackend: Fetching basic info...
07-03 01:13 DEBUG  CommonBackend: original_exe=F:\wubi.exe
07-03 01:13 DEBUG  CommonBackend: platform=win32
07-03 01:13 DEBUG  CommonBackend: osname=nt
07-03 01:13 DEBUG  CommonBackend: language=en_US
07-03 01:13 DEBUG  CommonBackend: encoding=cp1252
07-03 01:13 DEBUG  WindowsBackend: arch=amd64
07-03 01:13 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\data\isolist.ini
07-03 01:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 01:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 01:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 01:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 01:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 01:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 01:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 01:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 01:13 DEBUG  WindowsBackend: Fetching host info...
07-03 01:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 01:13 DEBUG  WindowsBackend: windows version=xp
07-03 01:13 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-03 01:13 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-03 01:13 DEBUG  WindowsBackend: windows_build=2600
07-03 01:13 DEBUG  WindowsBackend: gmt=-8
07-03 01:13 DEBUG  WindowsBackend: country=US
07-03 01:13 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-03 01:13 DEBUG  WindowsBackend: windows_username=pooja
07-03 01:13 DEBUG  WindowsBackend: user_full_name=pooja
07-03 01:13 DEBUG  WindowsBackend: user_directory=pooja
07-03 01:13 DEBUG  WindowsBackend: windows_language_code=1033
07-03 01:13 DEBUG  WindowsBackend: windows_language=English
07-03 01:13 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
07-03 01:13 DEBUG  WindowsBackend: bootloader=xp
07-03 01:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 13604.4921875 mb free )
07-03 01:13 DEBUG  WindowsBackend: drive=Drive(C: hd 13604.4921875 mb free )
07-03 01:13 DEBUG  WindowsBackend: drive=Drive(D: hd 12316.453125 mb free ntfs)
07-03 01:13 DEBUG  WindowsBackend: drive=Drive(E: hd 25737.3984375 mb free ntfs)
07-03 01:13 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 01:13 DEBUG  WindowsBackend: uninstaller_path=None
07-03 01:13 DEBUG  WindowsBackend: previous_target_dir=None
07-03 01:13 DEBUG  WindowsBackend: previous_distro_name=None
07-03 01:13 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 01:13 DEBUG  WindowsBackend: keyboard_layout=us
07-03 01:13 DEBUG  WindowsBackend: keyboard_variant=
07-03 01:13 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 01:13 DEBUG  WindowsBackend: total_memory_mb=445.9375
07-03 01:13 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 01:13 DEBUG  CommonBackend: Searching for local CDs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Ubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Ubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Kubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Kubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Xubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Xubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Mythbuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp is a valid Mythbuntu CD
07-03 01:13 DEBUG  Distro:     does not contain C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 01:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 01:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 01:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 01:13 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-03 01:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-03 01:13 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 01:13 INFO   root: Running the CD menu...
07-03 01:13 DEBUG  WindowsFrontend: __init__...
07-03 01:13 DEBUG  WindowsFrontend: on_init...
07-03 01:13 INFO   root: CD menu finished
07-03 01:13 INFO   root: Running the installer...
07-03 01:13 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=8000MB, distro_name=Ubuntu, language=English, username=pooja
07-03 01:13 INFO   root: Received settings
07-03 01:13 DEBUG  TaskList: # Running tasklist...
07-03 01:13 DEBUG  TaskList: ## Running select_target_dir...
07-03 01:13 INFO   WindowsBackend: Installing into E:\ubuntu
07-03 01:13 DEBUG  TaskList: ## Finished select_target_dir
07-03 01:13 DEBUG  TaskList: ## Running create_dir_structure...
07-03 01:13 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-03 01:13 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-03 01:13 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-03 01:13 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-03 01:13 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-03 01:13 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-03 01:13 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-03 01:13 DEBUG  TaskList: ## Finished create_dir_structure
07-03 01:13 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 01:13 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 01:13 DEBUG  TaskList: ## Running create_uninstaller...
07-03 01:13 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 01:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 01:13 DEBUG  TaskList: ## Finished create_uninstaller
07-03 01:13 DEBUG  TaskList: ## Running copy_installation_files...
07-03 01:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-03 01:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\winboot -> E:\ubuntu\winboot
07-03 01:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\pooja\LOCALS~1\Temp\pyl1F.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-03 01:13 DEBUG  TaskList: ## Finished copy_installation_files
07-03 01:13 DEBUG  TaskList: ## Running get_iso...
07-03 01:13 DEBUG  TaskList: New task copy_file
07-03 01:13 DEBUG  TaskList: ### Running copy_file...
07-03 01:17 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
07-03 01:17 DEBUG  TaskList: # Cancelling tasklist
07-03 01:17 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
07-03 01:17 DEBUG  TaskList: New task check_iso
07-03 01:17 DEBUG  CommonBackend: Searching for local ISO
07-03 01:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 01:17 DEBUG  TaskList: New task get_metalink
07-03 01:17 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 01:17 DEBUG  TaskList: # Cancelling tasklist
07-03 01:17 DEBUG  TaskList: # Finished tasklist

```

I'm trying to install ubuntu inside windows xp.. bt it is showing "invalid arguement" error. i have even reinstalled the windows. plz help

Here copy_file is accessing Z:\ drive.  Only at the time of accessing Z:\ drive, we arefacing this issue. More over, there is I/O error prior to the invalid arguments. Look in to the Z:\ drive, whether it has formatted properly with the required FS type.

---

### Post by wildmanne39 on 2011-07-04
Hi here is a link that should help.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by amjjawad on 2011-07-04
Wubi? why Wubi?

I recommend a normal installation but of course it's your call.

Good luck!

---

### Post by drs305 on 2011-07-04
I don't know about the Wubi repositories, but the normal repositories for Ubuntu 9.04 no longer exist. It reached its End of Life last fall and the repositories were moved. If this isn't the reason the installation is failing it may still cause problems later in the installation sequence.

Even if the repositories are available to Wubi installers (which I doubt), you might want to consider installing a newer version unless you have some special need for Jaunty.

---

### Post by bcbc on 2011-07-04
If you've reinstalled Windows, then it shouldn't be too difficult to do a proper partitioned wubi install. Wubi is for people to try out Ubuntu without the fear of risking their Windows install.

That error is likely from a bad burn on the CD. 

That Z: drive is just a code diagnostic where the failure occurred (the developer who generated the wubi.exe is Evan) - and you don't have a Z: drive.

So... as mentioned, don't install 9.04. It's no longer supported. Consider installing a normal partitioned install. Make sure any ubuntu cd is burned at the slowest possible speed.

---

