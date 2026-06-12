---
title: "Help please !! Problem in installation"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by demon36 on 2009-06-20
um having a problem that is :
when i try to install ubuntu from a pre-downloaded iso by wubi Or by the CD Ive burnt I get the following messege 
[IMG]http://www.fileden.com/files/2008/7/27/2021609/2.jpg[/IMG]
note :
this is ubuntu 9.04 desktop edition 32bit

And this is wut I find in wubi-9.04-rev128.log

```
06-20 08:08 INFO   root: === wubi 9.04 rev128 ===
06-20 08:08 DEBUG  root: Logfile is c:\docume~1\hossam\locals~1\temp\wubi-9.04-rev128.log
06-20 08:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
06-20 08:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\data
06-20 08:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\bin\7z.exe
06-20 08:08 DEBUG  CommonBackend: Fetching basic info...
06-20 08:08 DEBUG  CommonBackend: original_exe=I:\wubi.exe
06-20 08:08 DEBUG  CommonBackend: platform=win32
06-20 08:08 DEBUG  CommonBackend: osname=nt
06-20 08:08 DEBUG  CommonBackend: language=en_US
06-20 08:08 DEBUG  CommonBackend: encoding=cp1252
06-20 08:08 DEBUG  WindowsBackend: arch=i386
06-20 08:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\data\isolist.ini
06-20 08:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-20 08:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-20 08:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-20 08:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-20 08:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-20 08:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-20 08:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-20 08:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-20 08:08 DEBUG  WindowsBackend: Fetching host info...
06-20 08:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-20 08:08 DEBUG  WindowsBackend: windows version=xp
06-20 08:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-20 08:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-20 08:08 DEBUG  WindowsBackend: windows_build=2600
06-20 08:08 DEBUG  WindowsBackend: gmt=2
06-20 08:08 DEBUG  WindowsBackend: country=US
06-20 08:08 DEBUG  WindowsBackend: timezone=America/New_York
06-20 08:08 DEBUG  WindowsBackend: windows_username=Hossam
06-20 08:08 DEBUG  WindowsBackend: user_full_name=Hossam
06-20 08:08 DEBUG  WindowsBackend: user_directory=Hossam
06-20 08:08 DEBUG  WindowsBackend: windows_language_code=1033
06-20 08:08 DEBUG  WindowsBackend: windows_language=English
06-20 08:08 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.40GHz
06-20 08:08 DEBUG  WindowsBackend: bootloader=xp
06-20 08:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 1686.95703125 mb free )
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(C: hd 1686.95703125 mb free )
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(D: hd 2521.7109375 mb free fat32)
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(E: hd 500.75 mb free fat32)
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(F: hd 223.8828125 mb free fat32)
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(G: hd 202.015625 mb free fat32)
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(H: hd 498.2578125 mb free fat32)
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
06-20 08:08 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
06-20 08:08 DEBUG  WindowsBackend: uninstaller_path=None
06-20 08:08 DEBUG  WindowsBackend: previous_target_dir=None
06-20 08:08 DEBUG  WindowsBackend: previous_distro_name=None
06-20 08:08 DEBUG  WindowsBackend: keyboard_id=67699721
06-20 08:08 DEBUG  WindowsBackend: keyboard_layout=us
06-20 08:08 DEBUG  WindowsBackend: keyboard_variant=
06-20 08:08 DEBUG  CommonBackend: locale=en_US.UTF-8
06-20 08:08 DEBUG  WindowsBackend: total_memory_mb=895.484375
06-20 08:08 DEBUG  CommonBackend: Searching ISOs on USB devices
06-20 08:08 DEBUG  CommonBackend: Searching for local CDs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Hossam\LOCALS~1\Temp\pylD94.tmp\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
06-20 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
06-20 08:08 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-20 08:08 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-20 08:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-20 08:08 DEBUG  Distro: wrong arch: i386 != amd64
06-20 08:08 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
06-20 08:08 INFO   Distro: Found a valid CD for Ubuntu: I:\
06-20 08:08 INFO   root: Running the CD menu...
06-20 08:08 DEBUG  WindowsFrontend: __init__...
06-20 08:08 DEBUG  WindowsFrontend: on_init...
06-20 08:08 INFO   root: CD menu finished
06-20 08:08 INFO   root: Running the installer...
06-20 08:08 ERROR  root: list index out of range
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 153, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 115, in show_installation_settings
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\winui\ui.py", line 168, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\winui\ui.py", line 91, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 201, in on_init
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 156, in populate_distro_list
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 268, in on_distro_change
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 99, in populate_drive_list
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 115, in select_default_drive
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 279, in on_drive_change
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 129, in populate_size_list
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\installation_page.py", line 139, in select_default_size
IndexError: list index out of range

```

SO Iam here asking 4 help
Tnx at all

---

### Post by 73ckn797 on 2009-06-20
Did you perform a md5sum check on the downloaded iso prior to burning the disk?
If so, did you run a disk self check from the menu on booting the burned disk?

---

### Post by demon36 on 2009-06-20
Ive performed a md5sum check .. but I cant install ubuntu from the iso file by wubi .. nvm about the burnt disk

---

