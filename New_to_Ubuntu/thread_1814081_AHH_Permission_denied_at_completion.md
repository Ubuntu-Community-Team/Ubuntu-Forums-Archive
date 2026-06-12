---
title: "AHH Permission denied at completion"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-28
Hello there,

I decided to switch to Xubuntu 11.04. I uninstalled my Wubi-installed Ubuntu  11.04, 10.04 and used wubi.exe to install Xubuntu 11.04. It has gotten  to the end of the installation when a pop-up says "Permission denied",  and gave a path to a temporary file that it has created.

I apologize for having to post this out here; it would not let me upload it (file size is too big).

I did a search for this particular issue in the forum but I didn't get any solution. 
```

07-01 23:00 INFO   root: === wubi 11.04 

rev211 ===
07-01 23:00 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-01 23:00 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\Users\\ARQ\

\Desktop\\wubi.exe"']
07-01 23:00 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\data
07-01 23:00 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylFC88.tmp\bin\7z.exe
07-01 23:00 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-01 23:00 DEBUG  CommonBackend: 

Fetching basic info...
07-01 23:00 DEBUG  CommonBackend: 

original_exe=C:\Users\ARQ\Desktop

\wubi.exe
07-01 23:00 DEBUG  CommonBackend: 

platform=win32
07-01 23:00 DEBUG  CommonBackend: 

osname=nt
07-01 23:00 DEBUG  CommonBackend: 

language=en_CA
07-01 23:00 DEBUG  CommonBackend: 

encoding=cp1252
07-01 23:00 DEBUG  WindowsBackend: 

arch=amd64
07-01 23:00 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylFC88.tmp\data\isolist.ini
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-01 23:00 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-01 23:00 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-01 23:00 DEBUG  WindowsBackend: 

Fetching host info...
07-01 23:00 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-01 23:00 DEBUG  WindowsBackend: 

windows version=vista
07-01 23:00 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-01 23:00 DEBUG  WindowsBackend: 

windows_sp=None
07-01 23:00 DEBUG  WindowsBackend: 

windows_build=7600
07-01 23:00 DEBUG  WindowsBackend: 

gmt=-5
07-01 23:00 DEBUG  WindowsBackend: 

country=CA
07-01 23:00 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-01 23:00 DEBUG  WindowsBackend: 

windows_username=ARQ
07-01 23:00 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-01 23:00 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-01 23:00 DEBUG  WindowsBackend: 

windows_language_code=1033
07-01 23:00 DEBUG  WindowsBackend: 

windows_language=English
07-01 23:00 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-01 23:00 DEBUG  WindowsBackend: 

bootloader=vista
07-01 23:00 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 240727.21875 mb 

free ntfs)
07-01 23:00 DEBUG  WindowsBackend: 

drive=Drive(C: hd 240727.21875 mb free ntfs)
07-01 23:00 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-01 23:00 DEBUG  WindowsBackend: 

drive=Drive(E: cd 0.0 mb free )
07-01 23:00 DEBUG  WindowsBackend: 

drive=Drive(F: cd 0.0 mb free )
07-01 23:00 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-01 23:00 DEBUG  WindowsBackend: 

uninstaller_path=None
07-01 23:00 DEBUG  WindowsBackend: 

previous_target_dir=None
07-01 23:00 DEBUG  WindowsBackend: 

previous_distro_name=None
07-01 23:00 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-01 23:00 DEBUG  WindowsBackend: 

keyboard_layout=us
07-01 23:00 DEBUG  WindowsBackend: 

keyboard_variant=
07-01 23:00 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-01 23:00 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-01 23:00 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-01 23:00 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-01 23:00 DEBUG  CommonBackend: 

Searching for local CDs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Ubuntu Netbook 

CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFC88.tmp\casper

\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu Netbook CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu Netbook CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu Netbook CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu Netbook CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-01 23:00 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:00 INFO   root: Running the 

installer...
07-01 23:00 DEBUG  WindowsFrontend: 

__init__...
07-01 23:00 DEBUG  WindowsFrontend: 

on_init...
07-01 23:00 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylFC88.tmp

\translations, languages=['en_CA', 'en']
07-01 23:00 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylFC88.tmp

\translations, languages=['en_CA', 'en']
07-01 23:01 INFO   WindowsFrontend: 

Operation cancelled
07-01 23:01 DEBUG  WindowsFrontend: 

frontend.quit
07-01 23:01 DEBUG  WindowsFrontend: 

frontend.on_quit
07-01 23:01 DEBUG  root: application.on_quit
07-01 23:01 INFO   root: sys.exit
07-01 23:06 INFO   root: === wubi 11.04 

rev211 ===
07-01 23:06 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-01 23:06 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\Users\\ARQ\

\Desktop\\wubi.exe"']
07-01 23:06 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\data
07-01 23:06 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylE7E0.tmp\bin\7z.exe
07-01 23:06 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-01 23:06 DEBUG  CommonBackend: 

Fetching basic info...
07-01 23:06 DEBUG  CommonBackend: 

original_exe=C:\Users\ARQ\Desktop

\wubi.exe
07-01 23:06 DEBUG  CommonBackend: 

platform=win32
07-01 23:06 DEBUG  CommonBackend: 

osname=nt
07-01 23:06 DEBUG  CommonBackend: 

language=en_CA
07-01 23:06 DEBUG  CommonBackend: 

encoding=cp1252
07-01 23:06 DEBUG  WindowsBackend: 

arch=amd64
07-01 23:06 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylE7E0.tmp\data\isolist.ini
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-01 23:06 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-01 23:06 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-01 23:06 DEBUG  WindowsBackend: 

Fetching host info...
07-01 23:06 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-01 23:06 DEBUG  WindowsBackend: 

windows version=vista
07-01 23:06 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-01 23:06 DEBUG  WindowsBackend: 

windows_sp=None
07-01 23:06 DEBUG  WindowsBackend: 

windows_build=7600
07-01 23:06 DEBUG  WindowsBackend: 

gmt=-5
07-01 23:06 DEBUG  WindowsBackend: 

country=CA
07-01 23:06 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-01 23:06 DEBUG  WindowsBackend: 

windows_username=ARQ
07-01 23:06 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-01 23:06 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-01 23:06 DEBUG  WindowsBackend: 

windows_language_code=1033
07-01 23:06 DEBUG  WindowsBackend: 

windows_language=English
07-01 23:06 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-01 23:06 DEBUG  WindowsBackend: 

bootloader=vista
07-01 23:06 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 240562.34375 mb 

free ntfs)
07-01 23:06 DEBUG  WindowsBackend: 

drive=Drive(C: hd 240562.34375 mb free ntfs)
07-01 23:06 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-01 23:06 DEBUG  WindowsBackend: 

drive=Drive(E: cd 0.0 mb free )
07-01 23:06 DEBUG  WindowsBackend: 

drive=Drive(F: cd 0.0 mb free )
07-01 23:06 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-01 23:06 DEBUG  WindowsBackend: 

uninstaller_path=None
07-01 23:06 DEBUG  WindowsBackend: 

previous_target_dir=None
07-01 23:06 DEBUG  WindowsBackend: 

previous_distro_name=None
07-01 23:06 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-01 23:06 DEBUG  WindowsBackend: 

keyboard_layout=us
07-01 23:06 DEBUG  WindowsBackend: 

keyboard_variant=
07-01 23:06 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-01 23:06 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-01 23:06 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-01 23:06 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-01 23:06 DEBUG  CommonBackend: 

Searching for local CDs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Ubuntu Netbook 

CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylE7E0.tmp\casper

\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu Netbook CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu Netbook CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu Netbook CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu Netbook CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-01 23:06 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-01 23:06 INFO   root: Running the 

installer...
07-01 23:06 DEBUG  WindowsFrontend: 

__init__...
07-01 23:06 DEBUG  WindowsFrontend: 

on_init...
07-01 23:06 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylE7E0.tmp

\translations, languages=['en_CA', 'en']
07-01 23:06 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylE7E0.tmp

\translations, languages=['en_CA', 'en']
07-01 23:09 INFO   WindowsFrontend: 

Operation cancelled
07-01 23:09 DEBUG  WindowsFrontend: 

frontend.quit
07-01 23:09 DEBUG  WindowsFrontend: 

frontend.on_quit
07-01 23:09 DEBUG  root: application.on_quit
07-01 23:09 INFO   root: sys.exit
07-02 12:01 INFO   root: === wubi 11.04 

rev211 ===
07-02 12:01 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-02 12:01 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\Users\\ARQ\

\Desktop\\wubi.exe"']
07-02 12:01 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\data
07-02 12:01 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pyl8333.tmp\bin\7z.exe
07-02 12:01 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-02 12:01 DEBUG  CommonBackend: 

Fetching basic info...
07-02 12:01 DEBUG  CommonBackend: 

original_exe=C:\Users\ARQ\Desktop

\wubi.exe
07-02 12:01 DEBUG  CommonBackend: 

platform=win32
07-02 12:01 DEBUG  CommonBackend: 

osname=nt
07-02 12:01 DEBUG  CommonBackend: 

language=en_CA
07-02 12:01 DEBUG  CommonBackend: 

encoding=cp1252
07-02 12:01 DEBUG  WindowsBackend: 

arch=amd64
07-02 12:01 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pyl8333.tmp\data\isolist.ini
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-02 12:01 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-02 12:01 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-02 12:01 DEBUG  WindowsBackend: 

Fetching host info...
07-02 12:01 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-02 12:01 DEBUG  WindowsBackend: 

windows version=vista
07-02 12:01 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-02 12:01 DEBUG  WindowsBackend: 

windows_sp=None
07-02 12:01 DEBUG  WindowsBackend: 

windows_build=7600
07-02 12:01 DEBUG  WindowsBackend: 

gmt=-5
07-02 12:01 DEBUG  WindowsBackend: 

country=CA
07-02 12:01 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-02 12:01 DEBUG  WindowsBackend: 

windows_username=ARQ
07-02 12:01 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-02 12:01 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-02 12:01 DEBUG  WindowsBackend: 

windows_language_code=1033
07-02 12:01 DEBUG  WindowsBackend: 

windows_language=English
07-02 12:01 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-02 12:01 DEBUG  WindowsBackend: 

bootloader=vista
07-02 12:01 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 241885.609375 mb 

free ntfs)
07-02 12:01 DEBUG  WindowsBackend: 

drive=Drive(C: hd 241885.609375 mb free ntfs)
07-02 12:01 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-02 12:01 DEBUG  WindowsBackend: 

drive=Drive(E: cd 0.0 mb free )
07-02 12:01 DEBUG  WindowsBackend: 

drive=Drive(F: cd 0.0 mb free )
07-02 12:01 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-02 12:01 DEBUG  WindowsBackend: 

uninstaller_path=None
07-02 12:01 DEBUG  WindowsBackend: 

previous_target_dir=None
07-02 12:01 DEBUG  WindowsBackend: 

previous_distro_name=None
07-02 12:01 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-02 12:01 DEBUG  WindowsBackend: 

keyboard_layout=us
07-02 12:01 DEBUG  WindowsBackend: 

keyboard_variant=
07-02 12:01 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-02 12:01 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-02 12:01 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-02 12:01 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-02 12:01 DEBUG  CommonBackend: 

Searching for local CDs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Ubuntu Netbook 

CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu Netbook CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu Netbook CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu Netbook CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu Netbook CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 INFO   root: Running the 

installer...
07-02 12:01 DEBUG  WindowsFrontend: 

__init__...
07-02 12:01 DEBUG  WindowsFrontend: 

on_init...
07-02 12:01 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pyl8333.tmp

\translations, languages=['en_CA', 'en']
07-02 12:01 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pyl8333.tmp

\translations, languages=['en_CA', 'en']
07-02 12:01 DEBUG  WinuiInstallationPage: 

target_drive=C:, installation_size=17000MB, 

distro_name=Ubuntu, language=en_US, 

locale=en_US.UTF-8, username=manshi
07-02 12:01 INFO   root: Received settings
07-02 12:01 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pyl8333.tmp

\translations, languages=['en_US', 'en']
07-02 12:01 DEBUG  TaskList: # Running 

tasklist...
07-02 12:01 DEBUG  TaskList: ## Running 

select_target_dir...
07-02 12:01 INFO   WindowsBackend: 

Installing into C:\ubuntu
07-02 12:01 DEBUG  TaskList: ## Finished 

select_target_dir
07-02 12:01 DEBUG  TaskList: ## Running 

create_dir_structure...
07-02 12:01 DEBUG  CommonBackend: 

Creating dir C:\ubuntu
07-02 12:01 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks
07-02 12:01 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install
07-02 12:01 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install\boot
07-02 12:01 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks\boot
07-02 12:01 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks\boot\grub
07-02 12:01 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install\boot\grub
07-02 12:01 DEBUG  TaskList: ## Finished 

create_dir_structure
07-02 12:01 DEBUG  TaskList: ## Running 

uncompress_target_dir...
07-02 12:01 DEBUG  TaskList: ## Finished 

uncompress_target_dir
07-02 12:01 DEBUG  TaskList: ## Running 

create_uninstaller...
07-02 12:01 DEBUG  WindowsBackend: 

Copying uninstaller C:\Users\ARQ\Desktop

\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

UninstallString C:\ubuntu\uninstall-wubi.exe
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

InstallationDir C:\ubuntu
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayName Ubuntu
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayIcon C:\ubuntu\Ubuntu.ico
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayVersion 11.04-rev211
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

Publisher Ubuntu
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

URLInfoAbout http://www.ubuntu.com
07-02 12:01 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

HelpLink http://www.ubuntu.com/support
07-02 12:01 DEBUG  TaskList: ## Finished 

create_uninstaller
07-02 12:01 DEBUG  TaskList: ## Running 

copy_installation_files...
07-02 12:01 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\data\custom-installation 

-> C:\ubuntu\install\custom-installation
07-02 12:01 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\winboot -> C:\ubuntu

\winboot
07-02 12:01 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\data\images\Ubuntu.ico 

-> C:\ubuntu\Ubuntu.ico
07-02 12:01 DEBUG  TaskList: ## Finished 

copy_installation_files
07-02 12:01 DEBUG  TaskList: ## Running 

get_iso...
07-02 12:01 DEBUG  CommonBackend: 

Searching for local CD
07-02 12:01 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pyl8333.tmp\casper

\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 12:01 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-02 12:01 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 12:01 DEBUG  CommonBackend: 

Searching for local ISO
07-02 12:01 DEBUG  CommonBackend: Could 

not find any ISO or CD, downloading one now
07-02 12:01 DEBUG  TaskList: New task 

get_metalink
07-02 12:01 DEBUG  TaskList: ### Running 

get_metalink...
07-02 12:01 DEBUG  downloader: 

downloading 

http://releases.ubuntu.com/11.04/ubuntu-

11.04-desktop-amd64.metalink > C:\ubuntu

\install
07-02 12:01 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\ubuntu-11.04

-desktop-amd64.metalink, 

url=http://releases.ubuntu.com/11.04/ubuntu-

11.04-desktop-amd64.metalink, 

basename=ubuntu-11.04-desktop-

amd64.metalink, length=28363, text=None
07-02 12:01 DEBUG  downloader: download 

finished (read 28363 bytes)
07-02 12:01 DEBUG  downloader: 

downloading 

http://releases.ubuntu.com/11.04/MD5SUMS-

metalink > C:\ubuntu\install
07-02 12:01 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\MD5SUMS-

metalink, 

url=http://releases.ubuntu.com/11.04/MD5SU

MS-metalink, basename=MD5SUMS-metalink, 

length=874, text=None
07-02 12:01 DEBUG  downloader: download 

finished (read 874 bytes)
07-02 12:01 DEBUG  downloader: 

downloading 

http://releases.ubuntu.com/11.04/MD5SUMS-

metalink.gpg > C:\ubuntu\install
07-02 12:01 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\MD5SUMS-

metalink.gpg, 

url=http://releases.ubuntu.com/11.04/MD5SU

MS-metalink.gpg, basename=MD5SUMS-

metalink.gpg, length=198, text=None
07-02 12:01 DEBUG  downloader: download 

finished (read 198 bytes)
07-02 12:01 INFO   saplog: Verified a signature 

from ID:'46181433FBB75451'.
07-02 12:01 INFO   saplog: Checking block 

bindings..
07-02 12:01 INFO   saplog: Key verified 

successfully.
07-02 12:01 DEBUG  CommonBackend: 

metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-

11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-

11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-

11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-

11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-

11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-

11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-

11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-

11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-

11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-

11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-

11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-

11.04-server-i386.metalink

07-02 12:01 DEBUG  TaskList: ### Finished 

get_metalink
07-02 12:01 DEBUG  TaskList: New task 

download
07-02 12:01 DEBUG  TaskList: ### Running 

download...
07-02 12:01 DEBUG  btdownloader: 

downloading 

http://releases.ubuntu.com/11.04/ubuntu-

11.04-desktop-amd64.iso.torrent > C:\ubuntu

\install\ubuntu-11.04-desktop-amd64.iso
07-02 12:38 DEBUG  TaskList: ### Finished 

download
07-02 12:38 DEBUG  TaskList: New task 

check_iso
07-02 12:38 DEBUG  TaskList: ### Running 

check_iso...
07-02 12:38 DEBUG  CommonBackend: 

Checking C:\ubuntu\install\ubuntu-11.04-

desktop-amd64.iso
07-02 12:38 DEBUG  Distro:   checking Ubuntu 

ISO C:\ubuntu\install\ubuntu-11.04-desktop-

amd64.iso
07-02 12:38 DEBUG  WindowsBackend:   

extracting .disk\info from C:\ubuntu\install

\ubuntu-11.04-desktop-amd64.iso
07-02 12:38 DEBUG  Distro:   parsing info 

from str=Ubuntu 11.04 "Natty Narwhal" - 

Release amd64 (20110427.1)
07-02 12:38 DEBUG  Distro:   parsed info=

{'name': 'Ubuntu', 'subversion': 'Release', 

'version': '11.04', 'build': '20110427.1', 

'codename': 'Natty Narwhal', 'arch': 'amd64'}
07-02 12:38 INFO   Distro: Found a valid iso 

for Ubuntu: C:\ubuntu\install\ubuntu-11.04-

desktop-amd64.iso
07-02 12:38 DEBUG  TaskList: New task 

get_file_md5
07-02 12:38 DEBUG  TaskList: #### Running 

get_file_md5...
07-02 12:38 DEBUG  TaskList: #### Finished 

get_file_md5
07-02 12:38 ERROR  CommonBackend: 

Invalid md5 for ISO C:\ubuntu\install\ubuntu-

11.04-desktop-amd64.iso 

(7de611b50c283c1755b4007a4feb0379 != 

23b71414a76d4ebd5a18827a4cb9a9e1)
None
07-02 12:38 DEBUG  TaskList: ### Finished 

check_iso
07-02 12:38 DEBUG  TaskList: New task 

download
07-02 12:38 DEBUG  TaskList: ### Running 

download...
07-02 12:38 DEBUG  downloader: 

downloading http://ftp.heanet.ie/pub/ubuntu-

releases/11.04/ubuntu-11.04-desktop-

amd64.iso > C:\ubuntu\install\ubuntu-11.04-

desktop-amd64.iso
07-02 12:38 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\ubuntu-11.04

-desktop-amd64.iso, 

url=http://ftp.heanet.ie/pub/ubuntu-

releases/11.04/ubuntu-11.04-desktop-

amd64.iso, basename=ubuntu-11.04-desktop-

amd64.iso, length=732112896, text=None
07-02 13:15 DEBUG  TaskList: ### Finished 

download
07-02 13:15 DEBUG  downloader: download 

finished (read 732112896 bytes)
07-02 13:15 DEBUG  TaskList: New task 

check_iso
07-02 13:15 DEBUG  TaskList: ### Running 

check_iso...
07-02 13:15 DEBUG  CommonBackend: 

Checking C:\ubuntu\install\ubuntu-11.04-

desktop-amd64.iso
07-02 13:15 DEBUG  Distro:   checking Ubuntu 

ISO C:\ubuntu\install\ubuntu-11.04-desktop-

amd64.iso
07-02 13:15 INFO   Distro: Found a valid iso 

for Ubuntu: C:\ubuntu\install\ubuntu-11.04-

desktop-amd64.iso
07-02 13:15 DEBUG  TaskList: New task 

get_file_md5
07-02 13:15 DEBUG  TaskList: #### Running 

get_file_md5...
07-02 13:15 DEBUG  TaskList: #### Finished 

get_file_md5
07-02 13:15 DEBUG  TaskList: ### Finished 

check_iso
07-02 13:15 DEBUG  TaskList: ## Finished 

get_iso
07-02 13:15 DEBUG  TaskList: ## Running 

extract_kernel...
07-02 13:15 DEBUG  CommonBackend: 

Extracting files from ISO C:\ubuntu\install

\ubuntu-11.04-desktop-amd64.iso
07-02 13:15 DEBUG  WindowsBackend:   

extracting md5sum.txt from C:\ubuntu\install

\ubuntu-11.04-desktop-amd64.iso
07-02 13:15 DEBUG  WindowsBackend:   

extracting casper\vmlinuz from C:\ubuntu

\install\ubuntu-11.04-desktop-amd64.iso
07-02 13:15 DEBUG  WindowsBackend:   

extracting casper\initrd.lz from C:\ubuntu

\install\ubuntu-11.04-desktop-amd64.iso
07-02 13:15 DEBUG  CommonBackend: 

Checking kernel, initrd and md5sums
07-02 13:15 DEBUG  CommonBackend:   

checking C:\ubuntu\install\boot\vmlinuz
07-02 13:15 DEBUG  CommonBackend:   C:

\ubuntu\install\boot\vmlinuz md5 = 

45a7bee6779b8cd75634a70fd7a566dd == 

45a7bee6779b8cd75634a70fd7a566dd
07-02 13:15 DEBUG  CommonBackend:   

checking C:\ubuntu\install\boot\initrd.lz
07-02 13:15 DEBUG  CommonBackend:   C:

\ubuntu\install\boot\initrd.lz md5 = 

4aa66b9da42e1a3f667ab0c8009cc801 == 

4aa66b9da42e1a3f667ab0c8009cc801
07-02 13:15 DEBUG  TaskList: ## Finished 

extract_kernel
07-02 13:15 DEBUG  TaskList: ## Running 

choose_disk_sizes...
07-02 13:15 DEBUG  WindowsBackend: total 

size=17000
  root=16744
  swap=256
  home=0
  usr=0
07-02 13:15 DEBUG  TaskList: ## Finished 

choose_disk_sizes
07-02 13:15 DEBUG  TaskList: ## Running 

create_preseed...
07-02 13:15 DEBUG  TaskList: ## Finished 

create_preseed
07-02 13:15 DEBUG  TaskList: ## Running 

modify_bootloader...
07-02 13:15 DEBUG  TaskList: New task 

modify_bcd
07-02 13:15 DEBUG  TaskList: ### Running 

modify_bcd...
07-02 13:15 DEBUG  WindowsBackend: 

modify_bcd Drive(C: hd 241885.609375 mb free 

ntfs)
07-02 13:15 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

VistaBootDrive {efa075be-a4ce-11e0-8908-

82bc6dbfe48e}
07-02 13:15 DEBUG  TaskList: ### Finished 

modify_bcd
07-02 13:15 DEBUG  TaskList: ## Finished 

modify_bootloader
07-02 13:15 DEBUG  TaskList: ## Running 

modify_grub_configuration...
07-02 13:15 DEBUG  TaskList: ## Finished 

modify_grub_configuration
07-02 13:15 DEBUG  TaskList: ## Running 

create_virtual_disks...
07-02 13:15 DEBUG  Virtualdisk:  Creating 

virtual disk C:\ubuntu\disks\root.disk of 

16744MB
07-02 13:15 DEBUG  Virtualdisk:  Creating 

virtual disk C:\ubuntu\disks\swap.disk of 

256MB
07-02 13:15 DEBUG  TaskList: ## Finished 

create_virtual_disks
07-02 13:15 DEBUG  TaskList: ## Running 

uncompress_files...
07-02 13:15 DEBUG  WindowsBackend: 

compact C:\ubuntu\install\boot /U /A /F
07-02 13:15 DEBUG  WindowsBackend: 

compact C:\ubuntu\install\boot\*.* /U /A /F
07-02 13:15 DEBUG  TaskList: ## Finished 

uncompress_files
07-02 13:15 DEBUG  TaskList: ## Running 

eject_cd...
07-02 13:15 DEBUG  TaskList: ## Finished 

eject_cd
07-02 13:15 DEBUG  TaskList: # Finished 

tasklist
07-02 13:15 INFO   root: Almost finished 

installing
07-02 13:15 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pyl8333.tmp

\translations, languages=['en_US', 'en']
07-02 13:16 INFO   root: Finished installation
07-02 13:16 INFO   root: Rebooting
07-02 13:16 DEBUG  TaskList: # Running 

tasklist...
07-02 13:16 DEBUG  TaskList: ## Running 

reboot...
07-02 13:16 DEBUG  TaskList: ## Finished 

reboot
07-02 13:16 DEBUG  TaskList: # Finished 

tasklist
07-02 13:16 DEBUG  root: application.quit
07-02 13:16 DEBUG  WindowsFrontend: 

frontend.quit
07-02 13:16 DEBUG  WindowsFrontend: 

frontend.on_quit
07-02 13:16 DEBUG  root: application.on_quit
07-02 13:16 INFO   root: sys.exit
07-02 13:22 INFO   root: === wubi 11.04 

rev211 ===
07-02 13:22 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-02 13:22 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\Users\\ARQ\

\Desktop\\wubi.exe"']
07-02 13:22 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\data
07-02 13:22 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylBB43.tmp\bin\7z.exe
07-02 13:22 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-02 13:22 DEBUG  CommonBackend: 

Fetching basic info...
07-02 13:22 DEBUG  CommonBackend: 

original_exe=C:\Users\ARQ\Desktop

\wubi.exe
07-02 13:22 DEBUG  CommonBackend: 

platform=win32
07-02 13:22 DEBUG  CommonBackend: 

osname=nt
07-02 13:22 DEBUG  CommonBackend: 

language=en_CA
07-02 13:22 DEBUG  CommonBackend: 

encoding=cp1252
07-02 13:22 DEBUG  WindowsBackend: 

arch=amd64
07-02 13:22 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylBB43.tmp\data\isolist.ini
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-02 13:22 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-02 13:22 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-02 13:22 DEBUG  WindowsBackend: 

Fetching host info...
07-02 13:22 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-02 13:22 DEBUG  WindowsBackend: 

windows version=vista
07-02 13:22 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-02 13:22 DEBUG  WindowsBackend: 

windows_sp=None
07-02 13:22 DEBUG  WindowsBackend: 

windows_build=7600
07-02 13:22 DEBUG  WindowsBackend: 

gmt=-5
07-02 13:22 DEBUG  WindowsBackend: 

country=CA
07-02 13:22 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-02 13:22 DEBUG  WindowsBackend: 

windows_username=ARQ
07-02 13:22 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-02 13:22 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-02 13:22 DEBUG  WindowsBackend: 

windows_language_code=1033
07-02 13:22 DEBUG  WindowsBackend: 

windows_language=English
07-02 13:22 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-02 13:22 DEBUG  WindowsBackend: 

bootloader=vista
07-02 13:22 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 223975.800781 mb 

free ntfs)
07-02 13:22 DEBUG  WindowsBackend: 

drive=Drive(C: hd 223975.800781 mb free ntfs)
07-02 13:22 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-02 13:22 DEBUG  WindowsBackend: 

drive=Drive(E: cd 0.0 mb free )
07-02 13:22 DEBUG  WindowsBackend: 

drive=Drive(F: cd 0.0 mb free )
07-02 13:22 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-02 13:22 DEBUG  WindowsBackend: 

uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-02 13:22 DEBUG  WindowsBackend: 

previous_target_dir=C:\ubuntu
07-02 13:22 DEBUG  WindowsBackend: 

previous_distro_name=Ubuntu
07-02 13:22 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-02 13:22 DEBUG  WindowsBackend: 

keyboard_layout=us
07-02 13:22 DEBUG  WindowsBackend: 

keyboard_variant=
07-02 13:22 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-02 13:22 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-02 13:22 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-02 13:22 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-02 13:22 DEBUG  CommonBackend: 

Searching for local CDs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Ubuntu Netbook 

CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylBB43.tmp\casper

\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu Netbook CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu Netbook CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu Netbook CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu Netbook CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-02 13:22 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 13:22 INFO   root: Already installed, 

running the uninstaller...
07-02 13:22 INFO   root: Running the 

uninstaller...
07-02 13:22 INFO   CommonBackend: This is 

the uninstaller running
07-02 13:22 DEBUG  WindowsFrontend: 

__init__...
07-02 13:22 DEBUG  WindowsFrontend: 

on_init...
07-02 13:22 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylBB43.tmp

\translations, languages=['en_CA', 'en']
07-02 13:22 INFO   WindowsFrontend: 

Operation cancelled
07-02 13:22 DEBUG  WindowsFrontend: 

frontend.quit
07-02 13:22 DEBUG  WindowsFrontend: 

frontend.on_quit
07-02 13:22 DEBUG  root: application.on_quit
07-02 13:22 INFO   root: sys.exit
07-02 18:35 INFO   root: === wubi 11.04 

rev211 ===
07-02 18:35 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-02 18:35 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\ubuntu\

\uninstall-wubi.exe"']
07-02 18:35 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\data
07-02 18:35 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylDB50.tmp\bin\7z.exe
07-02 18:35 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-02 18:35 DEBUG  CommonBackend: 

Fetching basic info...
07-02 18:35 DEBUG  CommonBackend: 

original_exe=C:\ubuntu\uninstall-wubi.exe
07-02 18:35 DEBUG  CommonBackend: 

platform=win32
07-02 18:35 DEBUG  CommonBackend: 

osname=nt
07-02 18:35 DEBUG  CommonBackend: 

language=en_CA
07-02 18:35 DEBUG  CommonBackend: 

encoding=cp1252
07-02 18:35 DEBUG  WindowsBackend: 

arch=amd64
07-02 18:35 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylDB50.tmp\data\isolist.ini
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-02 18:35 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-02 18:35 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-02 18:35 DEBUG  WindowsBackend: 

Fetching host info...
07-02 18:35 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-02 18:35 DEBUG  WindowsBackend: 

windows version=vista
07-02 18:35 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-02 18:35 DEBUG  WindowsBackend: 

windows_sp=None
07-02 18:35 DEBUG  WindowsBackend: 

windows_build=7600
07-02 18:35 DEBUG  WindowsBackend: 

gmt=-5
07-02 18:35 DEBUG  WindowsBackend: 

country=CA
07-02 18:35 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-02 18:35 DEBUG  WindowsBackend: 

windows_username=ARQ
07-02 18:35 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-02 18:35 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-02 18:35 DEBUG  WindowsBackend: 

windows_language_code=1033
07-02 18:35 DEBUG  WindowsBackend: 

windows_language=English
07-02 18:35 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-02 18:35 DEBUG  WindowsBackend: 

bootloader=vista
07-02 18:35 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 223991.230469 mb 

free ntfs)
07-02 18:35 DEBUG  WindowsBackend: 

drive=Drive(C: hd 223991.230469 mb free ntfs)
07-02 18:35 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-02 18:35 DEBUG  WindowsBackend: 

drive=Drive(E: cd 0.0 mb free )
07-02 18:35 DEBUG  WindowsBackend: 

drive=Drive(F: cd 0.0 mb free )
07-02 18:35 DEBUG  WindowsBackend: 

drive=Drive(G: removable 1417.25 mb free 

fat32)
07-02 18:35 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-02 18:35 DEBUG  WindowsBackend: 

uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-02 18:35 DEBUG  WindowsBackend: 

previous_target_dir=C:\ubuntu
07-02 18:35 DEBUG  WindowsBackend: 

previous_distro_name=Ubuntu
07-02 18:35 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-02 18:35 DEBUG  WindowsBackend: 

keyboard_layout=us
07-02 18:35 DEBUG  WindowsBackend: 

keyboard_variant=
07-02 18:35 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-02 18:35 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-02 18:35 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-02 18:35 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-02 18:35 DEBUG  CommonBackend: 

Searching for local CDs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Ubuntu 

Netbook CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylDB50.tmp\casper

\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu Netbook CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Ubuntu Netbook CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether E:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Ubuntu Netbook CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether F:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Ubuntu Netbook CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether G:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu Netbook CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-02 18:35 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-02 18:35 INFO   root: Running the 

uninstaller...
07-02 18:35 INFO   CommonBackend: This is 

the uninstaller running
07-02 18:35 DEBUG  WindowsFrontend: 

__init__...
07-02 18:35 DEBUG  WindowsFrontend: 

on_init...
07-02 18:35 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylDB50.tmp

\translations, languages=['en_CA', 'en']
07-02 18:36 INFO   root: Received settings
07-02 18:36 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylDB50.tmp

\translations, languages=['en_CA', 'en']
07-02 18:36 DEBUG  TaskList: # Running 

tasklist...
07-02 18:36 DEBUG  TaskList: ## Running 

Backup ISO...
07-02 18:36 DEBUG  TaskList: ## Finished 

Backup ISO
07-02 18:36 DEBUG  TaskList: ## Running 

Remove bootloader entry...
07-02 18:36 DEBUG  WindowsBackend: 

Removing bcd entry {efa075be-a4ce-11e0-8908

-82bc6dbfe48e}
07-02 18:36 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

VistaBootDrive 
07-02 18:36 DEBUG  WindowsBackend: 

undo_bootini C:
07-02 18:36 DEBUG  WindowsBackend: 

undo_configsys Drive(C: hd 223991.230469 mb 

free ntfs)
07-02 18:36 DEBUG  WindowsBackend: 

undo_bootini G:
07-02 18:36 DEBUG  WindowsBackend: 

undo_configsys Drive(G: removable 1417.25 

mb free fat32)
07-02 18:36 DEBUG  TaskList: ## Finished 

Remove bootloader entry
07-02 18:36 DEBUG  TaskList: ## Running 

Remove target dir...
07-02 18:36 DEBUG  CommonBackend: 

Deleting C:\ubuntu
07-02 18:36 DEBUG  TaskList: ## Finished 

Remove target dir
07-02 18:36 DEBUG  TaskList: ## Running 

Remove registry key...
07-02 18:36 DEBUG  TaskList: ## Finished 

Remove registry key
07-02 18:36 DEBUG  TaskList: # Finished 

tasklist
07-02 18:36 INFO   root: Almost finished 

uninstalling
07-02 18:36 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylDB50.tmp

\translations, languages=['en_CA', 'en']
07-02 18:36 INFO   root: Finished 

uninstallation
07-02 18:36 DEBUG  root: application.quit
07-02 18:36 DEBUG  WindowsFrontend: 

frontend.quit
07-02 18:36 DEBUG  WindowsFrontend: 

frontend.on_quit
07-02 18:36 DEBUG  root: application.on_quit
07-02 18:36 INFO   root: sys.exit
07-03 10:55 INFO   root: === wubi 11.04 

rev211 ===
07-03 10:55 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-03 10:55 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\Users\\ARQ\

\Desktop\\wubi.exe"']
07-03 10:55 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\data
07-03 10:55 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp\bin\7z.exe
07-03 10:55 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-03 10:55 DEBUG  CommonBackend: 

Fetching basic info...
07-03 10:55 DEBUG  CommonBackend: 

original_exe=C:\Users\ARQ\Desktop

\wubi.exe
07-03 10:55 DEBUG  CommonBackend: 

platform=win32
07-03 10:55 DEBUG  CommonBackend: 

osname=nt
07-03 10:55 DEBUG  CommonBackend: 

language=en_CA
07-03 10:55 DEBUG  CommonBackend: 

encoding=cp1252
07-03 10:55 DEBUG  WindowsBackend: 

arch=amd64
07-03 10:55 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylFDAF.tmp\data\isolist.ini
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-03 10:55 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-03 10:55 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-03 10:55 DEBUG  WindowsBackend: 

Fetching host info...
07-03 10:55 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-03 10:55 DEBUG  WindowsBackend: 

windows version=vista
07-03 10:55 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-03 10:55 DEBUG  WindowsBackend: 

windows_sp=None
07-03 10:55 DEBUG  WindowsBackend: 

windows_build=7600
07-03 10:55 DEBUG  WindowsBackend: 

gmt=-5
07-03 10:55 DEBUG  WindowsBackend: 

country=CA
07-03 10:55 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-03 10:55 DEBUG  WindowsBackend: 

windows_username=ARQ
07-03 10:55 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-03 10:55 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-03 10:55 DEBUG  WindowsBackend: 

windows_language_code=1033
07-03 10:55 DEBUG  WindowsBackend: 

windows_language=English
07-03 10:55 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-03 10:55 DEBUG  WindowsBackend: 

bootloader=vista
07-03 10:55 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 238957.609375 mb 

free ntfs)
07-03 10:55 DEBUG  WindowsBackend: 

drive=Drive(C: hd 238957.609375 mb free ntfs)
07-03 10:55 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-03 10:55 DEBUG  WindowsBackend: 

drive=Drive(E: cd 0.0 mb free )
07-03 10:55 DEBUG  WindowsBackend: 

drive=Drive(F: cd 0.0 mb free )
07-03 10:55 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-03 10:55 DEBUG  WindowsBackend: 

uninstaller_path=None
07-03 10:55 DEBUG  WindowsBackend: 

previous_target_dir=None
07-03 10:55 DEBUG  WindowsBackend: 

previous_distro_name=None
07-03 10:55 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-03 10:55 DEBUG  WindowsBackend: 

keyboard_layout=us
07-03 10:55 DEBUG  WindowsBackend: 

keyboard_variant=
07-03 10:55 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-03 10:55 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-03 10:55 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-03 10:55 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-03 10:55 DEBUG  CommonBackend: 

Searching for local CDs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Ubuntu Netbook CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu Netbook CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

D:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Ubuntu Netbook CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

E:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Ubuntu Netbook CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

F:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu Netbook CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Kubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Xubuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 DEBUG  Distro:   checking whether 

H:\ is a valid Mythbuntu CD
07-03 10:55 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:55 INFO   root: Running the 

installer...
07-03 10:55 DEBUG  WindowsFrontend: 

__init__...
07-03 10:55 DEBUG  WindowsFrontend: 

on_init...
07-03 10:55 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylFDAF.tmp

\translations, languages=['en_CA', 'en']
07-03 10:55 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylFDAF.tmp

\translations, languages=['en_CA', 'en']
07-03 10:56 DEBUG  WinuiInstallationPage: 

target_drive=C:, installation_size=17000MB, 

distro_name=Ubuntu, language=en_US, 

locale=en_US.UTF-8, username=arqman
07-03 10:56 INFO   root: Received settings
07-03 10:56 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylFDAF.tmp

\translations, languages=['en_US', 'en']
07-03 10:56 DEBUG  TaskList: # Running 

tasklist...
07-03 10:56 DEBUG  TaskList: ## Running 

select_target_dir...
07-03 10:56 INFO   WindowsBackend: 

Installing into C:\ubuntu
07-03 10:56 DEBUG  TaskList: ## Finished 

select_target_dir
07-03 10:56 DEBUG  TaskList: ## Running 

create_dir_structure...
07-03 10:56 DEBUG  CommonBackend: 

Creating dir C:\ubuntu
07-03 10:56 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks
07-03 10:56 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install
07-03 10:56 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install\boot
07-03 10:56 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks\boot
07-03 10:56 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks\boot\grub
07-03 10:56 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install\boot\grub
07-03 10:56 DEBUG  TaskList: ## Finished 

create_dir_structure
07-03 10:56 DEBUG  TaskList: ## Running 

uncompress_target_dir...
07-03 10:56 DEBUG  TaskList: ## Finished 

uncompress_target_dir
07-03 10:56 DEBUG  TaskList: ## Running 

create_uninstaller...
07-03 10:56 DEBUG  WindowsBackend: 

Copying uninstaller C:\Users\ARQ\Desktop

\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

UninstallString C:\ubuntu\uninstall-wubi.exe
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

InstallationDir C:\ubuntu
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayName Ubuntu
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayIcon C:\ubuntu\Ubuntu.ico
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayVersion 11.04-rev211
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

Publisher Ubuntu
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

URLInfoAbout http://www.ubuntu.com
07-03 10:56 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

HelpLink http://www.ubuntu.com/support
07-03 10:56 DEBUG  TaskList: ## Finished 

create_uninstaller
07-03 10:56 DEBUG  TaskList: ## Running 

copy_installation_files...
07-03 10:56 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\data\custom-installation 

-> C:\ubuntu\install\custom-installation
07-03 10:56 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\winboot -> C:\ubuntu

\winboot
07-03 10:56 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\data\images\Ubuntu.ico 

-> C:\ubuntu\Ubuntu.ico
07-03 10:56 DEBUG  TaskList: ## Finished 

copy_installation_files
07-03 10:56 DEBUG  TaskList: ## Running 

get_iso...
07-03 10:56 DEBUG  CommonBackend: 

Searching for local CD
07-03 10:56 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylFDAF.tmp is a valid Ubuntu CD
07-03 10:56 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylFDAF.tmp\casper

\filesystem.squashfs
07-03 10:56 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu CD
07-03 10:56 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-03 10:56 DEBUG  Distro:   checking whether 

E:\ is a valid Ubuntu CD
07-03 10:56 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-03 10:56 DEBUG  Distro:   checking whether 

F:\ is a valid Ubuntu CD
07-03 10:56 DEBUG  Distro:     does not 

contain F:\casper\filesystem.squashfs
07-03 10:56 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu CD
07-03 10:56 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-03 10:56 DEBUG  CommonBackend: 

Searching for local ISO
07-03 10:56 DEBUG  CommonBackend: Could 

not find any ISO or CD, downloading one now
07-03 10:56 DEBUG  TaskList: New task 

get_metalink
07-03 10:56 DEBUG  TaskList: ### Running 

get_metalink...
07-03 10:56 DEBUG  downloader: 

downloading 

http://releases.ubuntu.com/11.04/ubuntu-

11.04-desktop-amd64.metalink > C:\ubuntu

\install
07-03 10:56 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\ubuntu-11.04

-desktop-amd64.metalink, 

url=http://releases.ubuntu.com/11.04/ubuntu-

11.04-desktop-amd64.metalink, 

basename=ubuntu-11.04-desktop-

amd64.metalink, length=28363, text=None
07-03 10:56 DEBUG  downloader: download 

finished (read 28363 bytes)
07-03 10:56 DEBUG  downloader: 

downloading 

http://releases.ubuntu.com/11.04/MD5SUMS-

metalink > C:\ubuntu\install
07-03 10:56 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\MD5SUMS-

metalink, 

url=http://releases.ubuntu.com/11.04/MD5SU

MS-metalink, basename=MD5SUMS-metalink, 

length=874, text=None
07-03 10:56 DEBUG  downloader: download 

finished (read 874 bytes)
07-03 10:56 DEBUG  downloader: 

downloading 

http://releases.ubuntu.com/11.04/MD5SUMS-

metalink.gpg > C:\ubuntu\install
07-03 10:56 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\MD5SUMS-

metalink.gpg, 

url=http://releases.ubuntu.com/11.04/MD5SU

MS-metalink.gpg, basename=MD5SUMS-

metalink.gpg, length=198, text=None
07-03 10:56 DEBUG  downloader: download 

finished (read 198 bytes)
07-03 10:56 INFO   saplog: Verified a signature 

from ID:'46181433FBB75451'.
07-03 10:56 INFO   saplog: Checking block 

bindings..
07-03 10:56 INFO   saplog: Key verified 

successfully.
07-03 10:56 DEBUG  CommonBackend: 

metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-

11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-

11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-

11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-

11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-

11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-

11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-

11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-

11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-

11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-

11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-

11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-

11.04-server-i386.metalink

07-03 10:56 DEBUG  TaskList: ### Finished 

get_metalink
07-03 10:56 DEBUG  TaskList: New task 

download
07-03 10:56 DEBUG  TaskList: ### Running 

download...
07-03 10:56 DEBUG  btdownloader: 

downloading 

http://releases.ubuntu.com/11.04/ubuntu-

11.04-desktop-amd64.iso.torrent > C:\ubuntu

\install\ubuntu-11.04-desktop-amd64.iso
07-03 12:10 DEBUG  TaskList: ### Finished 

download
07-03 12:10 DEBUG  TaskList: New task 

check_iso
07-03 12:10 DEBUG  TaskList: ### Running 

check_iso...
07-03 12:10 DEBUG  CommonBackend: 

Checking C:\ubuntu\install\ubuntu-11.04-

desktop-amd64.iso
07-03 12:10 DEBUG  Distro:   checking Ubuntu 

ISO C:\ubuntu\install\ubuntu-11.04-desktop-

amd64.iso
07-03 12:10 DEBUG  WindowsBackend:   

extracting .disk\info from C:\ubuntu\install

\ubuntu-11.04-desktop-amd64.iso
07-03 12:10 DEBUG  Distro:   parsing info from 

str=Ubuntu 11.04 "Natty Narwhal" - Release 

amd64 (20110427.1)
07-03 12:10 DEBUG  Distro:   parsed info=

{'name': 'Ubuntu', 'subversion': 'Release', 

'version': '11.04', 'build': '20110427.1', 

'codename': 'Natty Narwhal', 'arch': 'amd64'}
07-03 12:10 INFO   Distro: Found a valid iso 

for Ubuntu: C:\ubuntu\install\ubuntu-11.04-

desktop-amd64.iso
07-03 12:10 DEBUG  TaskList: New task 

get_file_md5
07-03 12:10 DEBUG  TaskList: #### Running 

get_file_md5...
07-03 12:10 DEBUG  TaskList: #### Finished 

get_file_md5
07-03 12:10 DEBUG  TaskList: ### Finished 

check_iso
07-03 12:10 DEBUG  TaskList: ## Finished 

get_iso
07-03 12:10 DEBUG  TaskList: ## Running 

extract_kernel...
07-03 12:10 DEBUG  CommonBackend: 

Extracting files from ISO C:\ubuntu\install

\ubuntu-11.04-desktop-amd64.iso
07-03 12:10 DEBUG  WindowsBackend:   

extracting md5sum.txt from C:\ubuntu\install

\ubuntu-11.04-desktop-amd64.iso
07-03 12:10 DEBUG  WindowsBackend:   

extracting casper\vmlinuz from C:\ubuntu

\install\ubuntu-11.04-desktop-amd64.iso
07-03 12:10 DEBUG  WindowsBackend:   

extracting casper\initrd.lz from C:\ubuntu

\install\ubuntu-11.04-desktop-amd64.iso
07-03 12:10 DEBUG  CommonBackend: 

Checking kernel, initrd and md5sums
07-03 12:10 DEBUG  CommonBackend:   

checking C:\ubuntu\install\boot\vmlinuz
07-03 12:10 DEBUG  CommonBackend:   C:

\ubuntu\install\boot\vmlinuz md5 = 

45a7bee6779b8cd75634a70fd7a566dd == 

45a7bee6779b8cd75634a70fd7a566dd
07-03 12:10 DEBUG  CommonBackend:   

checking C:\ubuntu\install\boot\initrd.lz
07-03 12:10 DEBUG  CommonBackend:   C:

\ubuntu\install\boot\initrd.lz md5 = 

4aa66b9da42e1a3f667ab0c8009cc801 == 

4aa66b9da42e1a3f667ab0c8009cc801
07-03 12:10 DEBUG  TaskList: ## Finished 

extract_kernel
07-03 12:10 DEBUG  TaskList: ## Running 

choose_disk_sizes...
07-03 12:10 DEBUG  WindowsBackend: total 

size=17000
  root=16744
  swap=256
  home=0
  usr=0
07-03 12:10 DEBUG  TaskList: ## Finished 

choose_disk_sizes
07-03 12:10 DEBUG  TaskList: ## Running 

create_preseed...
07-03 12:10 DEBUG  TaskList: ## Finished 

create_preseed
07-03 12:10 DEBUG  TaskList: ## Running 

modify_bootloader...
07-03 12:10 DEBUG  TaskList: New task 

modify_bcd
07-03 12:10 DEBUG  TaskList: ### Running 

modify_bcd...
07-03 12:10 DEBUG  WindowsBackend: 

modify_bcd Drive(C: hd 238957.609375 mb free 

ntfs)
07-03 12:10 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

VistaBootDrive {069050d5-a58f-11e0-8a1b-

a476d05c20f6}
07-03 12:10 DEBUG  TaskList: ### Finished 

modify_bcd
07-03 12:10 DEBUG  TaskList: ## Finished 

modify_bootloader
07-03 12:10 DEBUG  TaskList: ## Running 

modify_grub_configuration...
07-03 12:10 DEBUG  TaskList: ## Finished 

modify_grub_configuration
07-03 12:10 DEBUG  TaskList: ## Running 

create_virtual_disks...
07-03 12:10 DEBUG  Virtualdisk:  Creating 

virtual disk C:\ubuntu\disks\root.disk of 

16744MB
07-03 12:10 DEBUG  Virtualdisk:  Creating 

virtual disk C:\ubuntu\disks\swap.disk of 

256MB
07-03 12:10 DEBUG  TaskList: ## Finished 

create_virtual_disks
07-03 12:10 DEBUG  TaskList: ## Running 

uncompress_files...
07-03 12:10 DEBUG  WindowsBackend: 

compact C:\ubuntu\install\boot /U /A /F
07-03 12:10 DEBUG  WindowsBackend: 

compact C:\ubuntu\install\boot\*.* /U /A /F
07-03 12:10 DEBUG  TaskList: ## Finished 

uncompress_files
07-03 12:10 DEBUG  TaskList: ## Running 

eject_cd...
07-03 12:10 DEBUG  TaskList: ## Finished 

eject_cd
07-03 12:10 DEBUG  TaskList: # Finished 

tasklist
07-03 12:10 INFO   root: Almost finished 

installing
07-03 12:10 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylFDAF.tmp

\translations, languages=['en_US', 'en']
07-03 12:18 INFO   root: Finished installation
07-03 12:18 INFO   root: Rebooting
07-03 12:18 DEBUG  TaskList: # Running 

tasklist...
07-03 12:18 DEBUG  TaskList: ## Running 

reboot...
07-03 12:18 DEBUG  TaskList: ## Finished 

reboot
07-03 12:18 DEBUG  TaskList: # Finished 

tasklist
07-03 12:18 DEBUG  root: application.quit
07-03 12:18 DEBUG  WindowsFrontend: 

frontend.quit
07-03 12:18 DEBUG  WindowsFrontend: 

frontend.on_quit
07-03 12:18 DEBUG  root: application.on_quit
07-03 12:18 INFO   root: sys.exit
07-28 15:15 INFO   root: === wubi 11.04 

rev211 ===
07-28 15:15 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-28 15:15 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\ubuntu\

\uninstall-wubi.exe"']
07-28 15:15 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\data
07-28 15:15 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp\bin\7z.exe
07-28 15:15 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-28 15:15 DEBUG  CommonBackend: 

Fetching basic info...
07-28 15:15 DEBUG  CommonBackend: 

original_exe=C:\ubuntu\uninstall-wubi.exe
07-28 15:15 DEBUG  CommonBackend: 

platform=win32
07-28 15:15 DEBUG  CommonBackend: 

osname=nt
07-28 15:15 DEBUG  CommonBackend: 

language=en_CA
07-28 15:15 DEBUG  CommonBackend: 

encoding=cp1252
07-28 15:15 DEBUG  WindowsBackend: 

arch=amd64
07-28 15:15 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylB07.tmp\data\isolist.ini
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-28 15:15 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-28 15:15 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-28 15:15 DEBUG  WindowsBackend: 

Fetching host info...
07-28 15:15 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-28 15:15 DEBUG  WindowsBackend: 

windows version=vista
07-28 15:15 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-28 15:15 DEBUG  WindowsBackend: 

windows_sp=None
07-28 15:15 DEBUG  WindowsBackend: 

windows_build=7600
07-28 15:15 DEBUG  WindowsBackend: 

gmt=-5
07-28 15:15 DEBUG  WindowsBackend: 

country=CA
07-28 15:15 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-28 15:15 DEBUG  WindowsBackend: 

windows_username=ARQ
07-28 15:15 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-28 15:15 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-28 15:15 DEBUG  WindowsBackend: 

windows_language_code=1033
07-28 15:15 DEBUG  WindowsBackend: 

windows_language=English
07-28 15:15 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-28 15:15 DEBUG  WindowsBackend: 

bootloader=vista
07-28 15:15 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 231561.828125 mb 

free ntfs)
07-28 15:15 DEBUG  WindowsBackend: 

drive=Drive(C: hd 231561.828125 mb free ntfs)
07-28 15:15 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-28 15:15 DEBUG  WindowsBackend: 

drive=Drive(E: removable 875.24609375 mb 

free fat32)
07-28 15:15 DEBUG  WindowsBackend: 

drive=Drive(G: hd 436020.394531 mb free ntfs)
07-28 15:15 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-28 15:15 DEBUG  WindowsBackend: 

uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-28 15:15 DEBUG  WindowsBackend: 

previous_target_dir=C:\ubuntu
07-28 15:15 DEBUG  WindowsBackend: 

previous_distro_name=Ubuntu
07-28 15:15 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-28 15:15 DEBUG  WindowsBackend: 

keyboard_layout=us
07-28 15:15 DEBUG  WindowsBackend: 

keyboard_variant=
07-28 15:15 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-28 15:15 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-28 15:15 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-28 15:15 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-28 15:15 DEBUG  CommonBackend: 

Searching for local CDs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Ubuntu Netbook CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylB07.tmp is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylB07.tmp\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu Netbook CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

D:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Ubuntu Netbook CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

E:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain E:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Ubuntu Netbook CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

G:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu Netbook CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Kubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Xubuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 DEBUG  Distro:   checking whether 

H:\ is a valid Mythbuntu CD
07-28 15:15 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:15 INFO   root: Running the 

uninstaller...
07-28 15:15 INFO   CommonBackend: This is 

the uninstaller running
07-28 15:15 DEBUG  WindowsFrontend: 

__init__...
07-28 15:15 DEBUG  WindowsFrontend: 

on_init...
07-28 15:15 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylB07.tmp

\translations, languages=['en_CA', 'en']
07-28 15:15 INFO   root: Received settings
07-28 15:15 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylB07.tmp

\translations, languages=['en_CA', 'en']
07-28 15:15 DEBUG  TaskList: # Running 

tasklist...
07-28 15:15 DEBUG  TaskList: ## Running 

Backup ISO...
07-28 15:15 DEBUG  TaskList: ## Finished 

Backup ISO
07-28 15:15 DEBUG  TaskList: ## Running 

Remove bootloader entry...
07-28 15:15 DEBUG  WindowsBackend: 

Removing bcd entry {069050d5-a58f-11e0-

8a1b-a476d05c20f6}
07-28 15:15 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

VistaBootDrive 
07-28 15:15 DEBUG  WindowsBackend: 

undo_bootini C:
07-28 15:15 DEBUG  WindowsBackend: 

undo_configsys Drive(C: hd 231561.828125 mb 

free ntfs)
07-28 15:15 DEBUG  WindowsBackend: 

undo_bootini E:
07-28 15:15 DEBUG  WindowsBackend: 

undo_configsys Drive(E: removable 

875.24609375 mb free fat32)
07-28 15:15 DEBUG  WindowsBackend: 

undo_bootini G:
07-28 15:15 DEBUG  WindowsBackend: 

undo_configsys Drive(G: hd 436020.394531 mb 

free ntfs)
07-28 15:15 DEBUG  TaskList: ## Finished 

Remove bootloader entry
07-28 15:15 DEBUG  TaskList: ## Running 

Remove target dir...
07-28 15:15 DEBUG  CommonBackend: 

Deleting C:\ubuntu
07-28 15:15 DEBUG  TaskList: ## Finished 

Remove target dir
07-28 15:15 DEBUG  TaskList: ## Running 

Remove registry key...
07-28 15:15 DEBUG  TaskList: ## Finished 

Remove registry key
07-28 15:15 DEBUG  TaskList: # Finished 

tasklist
07-28 15:15 INFO   root: Almost finished 

uninstalling
07-28 15:15 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylB07.tmp

\translations, languages=['en_CA', 'en']
07-28 15:15 INFO   root: Finished uninstallation
07-28 15:15 DEBUG  root: application.quit
07-28 15:15 DEBUG  WindowsFrontend: 

frontend.quit
07-28 15:15 DEBUG  WindowsFrontend: 

frontend.on_quit
07-28 15:15 DEBUG  root: application.on_quit
07-28 15:15 INFO   root: sys.exit
07-28 15:29 INFO   root: === wubi 11.04 

rev211 ===
07-28 15:29 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-28 15:29 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\Users\\ARQ\

\Desktop\\wubi.exe"']
07-28 15:29 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\data
07-28 15:29 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylC032.tmp\bin\7z.exe
07-28 15:29 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-28 15:29 DEBUG  CommonBackend: 

Fetching basic info...
07-28 15:29 DEBUG  CommonBackend: 

original_exe=C:\Users\ARQ\Desktop

\wubi.exe
07-28 15:29 DEBUG  CommonBackend: 

platform=win32
07-28 15:29 DEBUG  CommonBackend: 

osname=nt
07-28 15:29 DEBUG  CommonBackend: 

language=en_CA
07-28 15:29 DEBUG  CommonBackend: 

encoding=cp1252
07-28 15:29 DEBUG  WindowsBackend: 

arch=amd64
07-28 15:29 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylC032.tmp\data\isolist.ini
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-28 15:29 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-28 15:29 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-28 15:29 DEBUG  WindowsBackend: 

Fetching host info...
07-28 15:29 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-28 15:29 DEBUG  WindowsBackend: 

windows version=vista
07-28 15:29 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-28 15:29 DEBUG  WindowsBackend: 

windows_sp=None
07-28 15:29 DEBUG  WindowsBackend: 

windows_build=7600
07-28 15:29 DEBUG  WindowsBackend: 

gmt=-5
07-28 15:29 DEBUG  WindowsBackend: 

country=CA
07-28 15:29 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-28 15:29 DEBUG  WindowsBackend: 

windows_username=ARQ
07-28 15:29 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-28 15:29 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-28 15:29 DEBUG  WindowsBackend: 

windows_language_code=1033
07-28 15:29 DEBUG  WindowsBackend: 

windows_language=English
07-28 15:29 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-28 15:29 DEBUG  WindowsBackend: 

bootloader=vista
07-28 15:29 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 248974.371094 mb 

free ntfs)
07-28 15:29 DEBUG  WindowsBackend: 

drive=Drive(C: hd 248974.371094 mb free ntfs)
07-28 15:29 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-28 15:29 DEBUG  WindowsBackend: 

drive=Drive(G: hd 436020.394531 mb free ntfs)
07-28 15:29 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-28 15:29 DEBUG  WindowsBackend: 

uninstaller_path=None
07-28 15:29 DEBUG  WindowsBackend: 

previous_target_dir=None
07-28 15:29 DEBUG  WindowsBackend: 

previous_distro_name=None
07-28 15:29 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-28 15:29 DEBUG  WindowsBackend: 

keyboard_layout=us
07-28 15:29 DEBUG  WindowsBackend: 

keyboard_variant=
07-28 15:29 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-28 15:29 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-28 15:29 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-28 15:29 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-28 15:29 DEBUG  CommonBackend: 

Searching for local CDs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Ubuntu Netbook 

CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylC032.tmp\casper

\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Ubuntu Netbook CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether D:\ is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Ubuntu Netbook CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether G:\ is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain G:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Ubuntu Netbook CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Kubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Xubuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 DEBUG  Distro:   checking 

whether H:\ is a valid Mythbuntu CD
07-28 15:29 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 15:29 INFO   root: Running the 

installer...
07-28 15:29 DEBUG  WindowsFrontend: 

__init__...
07-28 15:29 DEBUG  WindowsFrontend: 

on_init...
07-28 15:29 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylC032.tmp

\translations, languages=['en_CA', 'en']
07-28 15:29 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylC032.tmp

\translations, languages=['en_CA', 'en']
07-28 15:29 INFO   WindowsFrontend: 

Operation cancelled
07-28 15:29 DEBUG  WindowsFrontend: 

frontend.quit
07-28 15:29 DEBUG  WindowsFrontend: 

frontend.on_quit
07-28 15:29 DEBUG  root: application.on_quit
07-28 15:29 INFO   root: sys.exit
07-28 16:47 INFO   root: === wubi 11.04 

rev211 ===
07-28 16:47 DEBUG  root: Logfile is c:\users

\arq\appdata\local\temp\wubi-11.04-

rev211.log
07-28 16:47 DEBUG  root: sys.argv = 

['main.pyo', '--exefile="C:\\Users\\ARQ\

\Desktop\\wubi.exe"']
07-28 16:47 DEBUG  CommonBackend: 

data_dir=C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\data
07-28 16:47 DEBUG  WindowsBackend: 

7z=C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp\bin\7z.exe
07-28 16:47 DEBUG  WindowsBackend: 

startup_folder=C:\ProgramData\Microsoft

\Windows\Start Menu\Programs\Startup
07-28 16:47 DEBUG  CommonBackend: 

Fetching basic info...
07-28 16:47 DEBUG  CommonBackend: 

original_exe=C:\Users\ARQ\Desktop

\wubi.exe
07-28 16:47 DEBUG  CommonBackend: 

platform=win32
07-28 16:47 DEBUG  CommonBackend: 

osname=nt
07-28 16:47 DEBUG  CommonBackend: 

language=en_CA
07-28 16:47 DEBUG  CommonBackend: 

encoding=cp1252
07-28 16:47 DEBUG  WindowsBackend: 

arch=amd64
07-28 16:47 DEBUG  CommonBackend: 

Parsing isolist=C:\Users\ARQ\AppData

\Local\Temp\pylD7D7.tmp\data\isolist.ini
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Xubuntu-i386
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Xubuntu-amd64
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Kubuntu-amd64
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Mythbuntu-i386
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Ubuntu-amd64
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Ubuntu-i386
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Mythbuntu-amd64
07-28 16:47 DEBUG  CommonBackend:   

Adding distro Kubuntu-i386
07-28 16:47 DEBUG  CommonBackend:   

Adding distro UbuntuNetbook-i386
07-28 16:47 DEBUG  WindowsBackend: 

Fetching host info...
07-28 16:47 DEBUG  WindowsBackend: 

registry_key=Software\Microsoft\Windows

\CurrentVersion\Uninstall\Wubi
07-28 16:47 DEBUG  WindowsBackend: 

windows version=vista
07-28 16:47 DEBUG  WindowsBackend: 

windows_version2=Windows 7 Home 

Premium
07-28 16:47 DEBUG  WindowsBackend: 

windows_sp=None
07-28 16:47 DEBUG  WindowsBackend: 

windows_build=7600
07-28 16:47 DEBUG  WindowsBackend: 

gmt=-5
07-28 16:47 DEBUG  WindowsBackend: 

country=CA
07-28 16:47 DEBUG  WindowsBackend: 

timezone=America/Montreal
07-28 16:47 DEBUG  WindowsBackend: 

windows_username=ARQ
07-28 16:47 DEBUG  WindowsBackend: 

user_full_name=ARQ
07-28 16:47 DEBUG  WindowsBackend: 

user_directory=C:\Users\ARQ
07-28 16:47 DEBUG  WindowsBackend: 

windows_language_code=1033
07-28 16:47 DEBUG  WindowsBackend: 

windows_language=English
07-28 16:47 DEBUG  WindowsBackend: 

processor_name=Intel(R) Core(TM) i3 CPU       

M 370  @ 2.40GHz
07-28 16:47 DEBUG  WindowsBackend: 

bootloader=vista
07-28 16:47 DEBUG  WindowsBackend: 

system_drive=Drive(C: hd 248283.183594 mb 

free ntfs)
07-28 16:47 DEBUG  WindowsBackend: 

drive=Drive(C: hd 248283.183594 mb free ntfs)
07-28 16:47 DEBUG  WindowsBackend: 

drive=Drive(D: cd 0.0 mb free )
07-28 16:47 DEBUG  WindowsBackend: 

drive=Drive(H: cd 0.0 mb free )
07-28 16:47 DEBUG  WindowsBackend: 

uninstaller_path=None
07-28 16:47 DEBUG  WindowsBackend: 

previous_target_dir=None
07-28 16:47 DEBUG  WindowsBackend: 

previous_distro_name=None
07-28 16:47 DEBUG  WindowsBackend: 

keyboard_id=67702793
07-28 16:47 DEBUG  WindowsBackend: 

keyboard_layout=us
07-28 16:47 DEBUG  WindowsBackend: 

keyboard_variant=
07-28 16:47 DEBUG  CommonBackend: 

python locale=('en_CA', 'cp1252')
07-28 16:47 DEBUG  CommonBackend: 

locale=en_CA.UTF-8
07-28 16:47 DEBUG  WindowsBackend: 

total_memory_mb=2934.68359375
07-28 16:47 DEBUG  CommonBackend: 

Searching ISOs on USB devices
07-28 16:47 DEBUG  CommonBackend: 

Searching for local CDs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Ubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Ubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Ubuntu Netbook CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Kubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Kubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Xubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Xubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Mythbuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Mythbuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Ubuntu Netbook CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Kubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Kubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Xubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Xubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Mythbuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

D:\ is a valid Mythbuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Ubuntu Netbook CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Kubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Kubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Xubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Xubuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Mythbuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 DEBUG  Distro:   checking whether 

H:\ is a valid Mythbuntu CD
07-28 16:47 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:47 INFO   root: Running the 

installer...
07-28 16:47 DEBUG  WindowsFrontend: 

__init__...
07-28 16:47 DEBUG  WindowsFrontend: 

on_init...
07-28 16:47 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylD7D7.tmp

\translations, languages=['en_CA', 'en']
07-28 16:47 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylD7D7.tmp

\translations, languages=['en_CA', 'en']
07-28 16:48 DEBUG  WinuiInstallationPage: 

target_drive=C:, installation_size=9000MB, 

distro_name=Xubuntu, language=en_US, 

locale=en_US.UTF-8, username=arqwarrior
07-28 16:48 INFO   root: Received settings
07-28 16:48 INFO   WinuiPage: 

appname=wubi, localedir=C:\Users\ARQ

\AppData\Local\Temp\pylD7D7.tmp

\translations, languages=['en_US', 'en']
07-28 16:48 DEBUG  TaskList: # Running 

tasklist...
07-28 16:48 DEBUG  TaskList: ## Running 

select_target_dir...
07-28 16:48 INFO   WindowsBackend: 

Installing into C:\ubuntu
07-28 16:48 DEBUG  TaskList: ## Finished 

select_target_dir
07-28 16:48 DEBUG  TaskList: ## Running 

create_dir_structure...
07-28 16:48 DEBUG  CommonBackend: 

Creating dir C:\ubuntu
07-28 16:48 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks
07-28 16:48 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install
07-28 16:48 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install\boot
07-28 16:48 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks\boot
07-28 16:48 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\disks\boot\grub
07-28 16:48 DEBUG  CommonBackend: 

Creating dir C:\ubuntu\install\boot\grub
07-28 16:48 DEBUG  TaskList: ## Finished 

create_dir_structure
07-28 16:48 DEBUG  TaskList: ## Running 

uncompress_target_dir...
07-28 16:48 DEBUG  TaskList: ## Finished 

uncompress_target_dir
07-28 16:48 DEBUG  TaskList: ## Running 

create_uninstaller...
07-28 16:48 DEBUG  WindowsBackend: 

Copying uninstaller C:\Users\ARQ\Desktop

\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

UninstallString C:\ubuntu\uninstall-wubi.exe
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

InstallationDir C:\ubuntu
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayName Xubuntu
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayIcon C:\ubuntu\Xubuntu.ico
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

DisplayVersion 11.04-rev211
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

Publisher Xubuntu
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

URLInfoAbout http://www.xubuntu.org
07-28 16:48 DEBUG  registry: Setting registry 

key -2147483646 Software\Microsoft

\Windows\CurrentVersion\Uninstall\Wubi 

HelpLink http://www.ubuntu.com/support
07-28 16:48 DEBUG  TaskList: ## Finished 

create_uninstaller
07-28 16:48 DEBUG  TaskList: ## Running 

copy_installation_files...
07-28 16:48 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\data\custom-installation 

-> C:\ubuntu\install\custom-installation
07-28 16:48 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\winboot -> C:\ubuntu

\winboot
07-28 16:48 DEBUG  WindowsBackend: 

Copying C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\data\images

\Xubuntu.ico -> C:\ubuntu\Xubuntu.ico
07-28 16:48 DEBUG  TaskList: ## Finished 

copy_installation_files
07-28 16:48 DEBUG  TaskList: ## Running 

get_iso...
07-28 16:48 DEBUG  CommonBackend: 

Searching for local CD
07-28 16:48 DEBUG  Distro:   checking whether 

C:\Users\ARQ\AppData\Local\Temp

\pylD7D7.tmp is a valid Xubuntu CD
07-28 16:48 DEBUG  Distro:     does not 

contain C:\Users\ARQ\AppData\Local

\Temp\pylD7D7.tmp\casper

\filesystem.squashfs
07-28 16:48 DEBUG  Distro:   checking whether 

D:\ is a valid Xubuntu CD
07-28 16:48 DEBUG  Distro:     does not 

contain D:\casper\filesystem.squashfs
07-28 16:48 DEBUG  Distro:   checking whether 

H:\ is a valid Xubuntu CD
07-28 16:48 DEBUG  Distro:     does not 

contain H:\casper\filesystem.squashfs
07-28 16:48 DEBUG  CommonBackend: 

Searching for local ISO
07-28 16:48 DEBUG  CommonBackend: Could 

not find any ISO or CD, downloading one now
07-28 16:48 DEBUG  TaskList: New task 

get_metalink
07-28 16:48 DEBUG  TaskList: ### Running 

get_metalink...
07-28 16:48 DEBUG  downloader: 

downloading 

http://cdimage.ubuntu.com/xubuntu/releases/

11.04/release/xubuntu-11.04-desktop-

amd64.metalink > C:\ubuntu\install
07-28 16:48 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\xubuntu-

11.04-desktop-amd64.metalink, 

url=http://cdimage.ubuntu.com/xubuntu/relea

ses/11.04/release/xubuntu-11.04-desktop-

amd64.metalink, basename=xubuntu-11.04-

desktop-amd64.metalink, length=1040, 

text=None
07-28 16:48 DEBUG  downloader: download 

finished (read 1040 bytes)
07-28 16:48 DEBUG  downloader: 

downloading 

http://cdimage.ubuntu.com/xubuntu/releases/

11.04/release/MD5SUMS-metalink > C:

\ubuntu\install
07-28 16:48 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\MD5SUMS-

metalink, 

url=http://cdimage.ubuntu.com/xubuntu/relea

ses/11.04/release/MD5SUMS-metalink, 

basename=MD5SUMS-metalink, length=286, 

text=None
07-28 16:48 DEBUG  downloader: download 

finished (read 286 bytes)
07-28 16:48 DEBUG  downloader: 

downloading 

http://cdimage.ubuntu.com/xubuntu/releases/

11.04/release/MD5SUMS-metalink.gpg > C:

\ubuntu\install
07-28 16:48 DEBUG  downloader: Download 

start filename=C:\ubuntu\install\MD5SUMS-

metalink.gpg, 

url=http://cdimage.ubuntu.com/xubuntu/relea

ses/11.04/release/MD5SUMS-metalink.gpg, 

basename=MD5SUMS-metalink.gpg, 

length=198, text=None
07-28 16:48 DEBUG  downloader: download 

finished (read 198 bytes)
07-28 16:48 INFO   saplog: Verified a signature 

from ID:'46181433FBB75451'.
07-28 16:48 INFO   saplog: Checking block 

bindings..
07-28 16:48 INFO   saplog: Key verified 

successfully.
07-28 16:48 DEBUG  CommonBackend: 

metalink md5sums:
56b218cb2663a9033967543185484826  

xubuntu-11.04-alternate-amd64.metalink
f18c34ad9065c3d2a9cd2ac1528d6b43  xubuntu-

11.04-alternate-i386.metalink
b148e30eec434e7a75e658ecb595cb37  xubuntu-

11.04-desktop-amd64.metalink
c9d2293b8d51dec0e4e50b275513deca  

xubuntu-11.04-desktop-i386.metalink

07-28 16:48 DEBUG  TaskList: ### Finished 

get_metalink
07-28 16:48 DEBUG  TaskList: New task 

download
07-28 16:48 DEBUG  TaskList: ### Running 

download...
07-28 16:48 DEBUG  btdownloader: 

downloading 

http://cdimage.ubuntu.com/xubuntu/releases/

11.04/release/xubuntu-11.04-desktop-

amd64.iso.torrent > C:\ubuntu\install

\xubuntu-11.04-desktop-amd64.iso
07-28 17:18 ERROR  TaskList: Traceback 

(most recent call last):
  File "\lib\bittorrent\RawServer.py", line 231, 

in listen_forever
  File "\lib\bittorrent\RawServer.py", line 183, 

in handle_events
  File "\lib\bittorrent\Encrypter.py", line 210, in 

data_came_in
  File "\lib\bittorrent\Encrypter.py", line 130, in 

data_came_in
  File "\lib\bittorrent\Encrypter.py", line 96, in 

read_message
  File "\lib\bittorrent\Connecter.py", line 219, 

in got_message
  File "\lib\bittorrent\Downloader.py", line 80, 

in got_piece
  File "\lib\bittorrent\StorageWrapper.py", line 

138, in piece_came_in
  File "\lib\bittorrent\StorageWrapper.py", line 

150, in _piece_came_in
  File "\lib\bittorrent\download.py", line 199, in 

failed
  File "\lib\wubi\backends\common

\btdownloader.py", line 70, in error_callback
DownloadError: data corrupted on disk - 

maybe you have two copies running?
Traceback (most recent call last):
  File "\lib\wubi\backends\common

\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common

\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, 

in download
  File "\lib\bittorrent\RawServer.py", line 256, 

in listen_forever
  File "\lib\wubi\backends\common

\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call 

last):
  File "\lib\bittorrent\RawServer.py", line 231, 

in listen_forever
  File "\lib\bittorrent\RawServer.py", line 183, 

in handle_events
  File "\lib\bittorrent\Encrypter.py", line 210, in 

data_came_in
  File "\lib\bittorrent\Encrypter.py", line 130, in 

data_came_in
  File "\lib\bittorrent\Encrypter.py", line 96, in 

read_message
  File "\lib\bittorrent\Connecter.py", line 219, 

in got_message
  File "\lib\bittorrent\Downloader.py", line 80, 

in got_piece
  File "\lib\bittorrent\StorageWrapper.py", line 

138, in piece_came_in
  File "\lib\bittorrent\StorageWrapper.py", line 

150, in _piece_came_in
  File "\lib\bittorrent\download.py", line 199, in 

failed
  File "\lib\wubi\backends\common

\btdownloader.py", line 70, in error_callback
DownloadError: data corrupted on disk - 

maybe you have two copies running?

07-28 17:18 ERROR  TaskList: Non fatal error 

Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 231, 

in listen_forever
  File "\lib\bittorrent\RawServer.py", line 183, 

in handle_events
  File "\lib\bittorrent\Encrypter.py", line 210, in 

data_came_in
  File "\lib\bittorrent\Encrypter.py", line 130, in 

data_came_in
  File "\lib\bittorrent\Encrypter.py", line 96, in 

read_message
  File "\lib\bittorrent\Connecter.py", line 219, 

in got_message
  File "\lib\bittorrent\Downloader.py", line 80, 

in got_piece
  File "\lib\bittorrent\StorageWrapper.py", line 

138, in piece_came_in
  File "\lib\bittorrent\StorageWrapper.py", line 

150, in _piece_came_in
  File "\lib\bittorrent\download.py", line 199, in 

failed
  File "\lib\wubi\backends\common

\btdownloader.py", line 70, in error_callback
DownloadError: data corrupted on disk - 

maybe you have two copies running?
 in task download
07-28 17:18 DEBUG  TaskList: ### Finished 

download
07-28 17:18 ERROR  TaskList: [Errno 13] 

Permission denied: u'C:\\ubuntu\\install\

\xubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common

\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common

\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common

\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\

\ubuntu\\install\\xubuntu-11.04-desktop-

amd64.iso'
07-28 17:18 DEBUG  TaskList: # Cancelling 

tasklist
07-28 17:18 DEBUG  TaskList: # Finished 

tasklist
07-28 17:18 ERROR  root: [Errno 13] 

Permission denied: u'C:\\ubuntu\\install\

\xubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in 

select_task
  File "\lib\wubi\application.py", line 157, in 

run_installer
  File "\lib\wubi\backends\common

\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common

\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common

\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\

\ubuntu\\install\\xubuntu-11.04-desktop-

amd64.iso'

```

---

### Post by bcbc on 2011-07-28
> \btdownloader.py", line 70, in error_callback
DownloadError: data corrupted on disk - maybe you have two copies running?

Why don't you run chkdsk, defragment and the try again. It looks like you have some problem downloading the xubuntu desktop CD ISO and it could be some ntfs corruption.

You can also download the ISO yourself from [http://www.xubuntu.org/get](http://www.xubuntu.org/get) and save it in the same folder as wubi.exe and then wubi will find it and use it.

(Personally, I'd run chkdsk anyway and probably the defragmenter as well)

---

### Post by WubiAR on 2011-07-28
I am a complete n00b with this; do you check disk by following the procedure like this for "chkdsk" in windows 7?
Click, Start>>>Computer>>>Highlight  Os/C>>>Right  click>>>Properties>>>Tools>>>Error Checking,  Click, Check now

If so, I did that but it says the disk in use...
When exactly can I check it? This is my home drive by the way.

---

### Post by fdrake on 2011-07-28
when you start wubi.exe befori installing there should be an option asking if you want to check the file.... at least that's how is on the live cd.

when you said > I deleted my Wubi-installed Ubuntu 11.04, 10.04 and used wubi.exe to install Xubuntu 11.04 you are suppose to uninstall ubuntu not delete the files...

---

### Post by WubiAR on 2011-07-28
> **fdrake said:**
> when you start wubi.exe befori installing there should be an option asking if you want to check the file.... at least that's how is on the live cd.

when you said  you are suppose to uninstall ubuntu not delete the files...

Sorry what I meant by that was I went to the Add/Remove programs version of Windows 7 and uninstalled both versions of Ubuntu.

---

### Post by bcbc on 2011-07-28
> **WubiAR said:**
> I am a complete n00b with this; do you check disk by following the procedure like this for "chkdsk" in windows 7?
Click, Start>>>Computer>>>Highlight  Os/C>>>Right  click>>>Properties>>>Tools>>>Error Checking,  Click, Check now

If so, I did that but it says the disk in use...
When exactly can I check it? This is my home drive by the way.

Yes - select check disk, check the box for fix automatically, then it will tell you it cannot run while in use, do you want to schedule for the next time you boot? Hit Yes, then reboot to complete.

---

### Post by WubiAR on 2011-07-28
Ok let me tell you EXACTLY what happened.

I was running 11.04 Ubuntu well, until some experiments with CompizConfig went horribly wrong; my desktop was crashing, and it left behind alot of black boxes. So then I backed up all my files and uninstalled 11.04 Ubuntu. Then, I tried to download and install Ubuntu 10.04 through my USB drive, little did I know that there was a Wubi client for it. I followed the intructions for a USB drive download, and then proceeded to boot up through the USB. I did so and finished installing Ubuntu 10.04 from there. It told me to perss "Enter" after you removed the CD (I assumed it was my USB stick), and so I did and it restarted.

But I didn't see a screen allowing me to choose which OS. It went directly to Windows 7. So then, I decided to check out what was actually in the flash drive. I found a "wubi.exe" in there and I opened it up, and selected the option as "Install Ubuntu inside windows". I did so, and followed the installation and finally, I got 10.04. But once I got 10.04, I was fed up with internet issues and an annoying drive icon on my desktop that when I ejected, it would crash the whole system.

So then I went back to Windows 7 and decided to uninstall that, and install Xubuntu 11.04 instead. I downloaded the Wubi client, chose Xubuntu and countinued with the installation, and that's what I ran into (as shown in the opening post).

Note: Ever since I installed Ubuntu, I got a "Recovery" drive on My Computer. What's going on with that?

---

### Post by WubiAR on 2011-07-28
> **bcbc said:**
> Yes - select check disk, check the box for fix automatically, then it will tell you it cannot run while in use, do you want to schedule for the next time you boot? Hit Yes, then reboot to complete.

I don't get the "do you want to schedule for the next time you boot?" either.

---

### Post by bcbc on 2011-07-28
You can use a windows repair disk to boot to a repair prompt and run chkdsk. Or maybe you can boot to a command prompt and do it. You shouldn't need to... not sure why windows is unable to do this.

---

### Post by fdrake on 2011-07-28
> **bcbc said:**
> You can use a windows repair disk to boot to a repair prompt and run chkdsk. Or maybe you can boot to a command prompt and do it. You shouldn't need to... not sure why windows is unable to do this.

windows 7 makes it a little harder now. 
[URL="http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/why-cant-i-run-chkdsk-from-a-start-menu-cmd-prompt/2cc803c7-ea8f-4578-b8f5-10f2c1c36885"]
see the link[/URL]

i whould just burn a cd and boot from there.

---

