---
title: "Installation Error Messages - 'see log file...' and 'failed while handling...'"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by zero01011 on 2010-12-21
I&#8217;m trying to install UBUNTU-10.10-desktop-i386.iso on a IBM Think Pad, Pentium III; 55GB HDD (which has 48GB free and 7GB used), CPU 1200MHz, AT compatible, 523,184 RAM, O/S Windows 2000 Professional.

If I try to install while I am in Windows it starts to install and then I get the following message and the installation stops.
```
permission denied &#8211; for more info, please see the log file: c:\temp\wubi-10.10rev 197.log
```

If I try and Boot from the UBUNTU CD, I get the following message after the Ubuntu Logo appears -

```
BUSYBOX v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash) 
Enter &#8216;help&#8217; for a list of built-in commands.
(initramfs) mount: mounting/dev/loop0 on //filesystem.squashfs failed : Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
udevd[77]: worker [190] unexpectedly returned with status 0x0100
udevd[77]: worker [190] failed while handling &#8216;/devices/virtual/block/loop0&#8217;
```

I've downloaded UBUNTU twice and I got the same result each time.
What can I try as another option to install UBUNTU?

---

### Post by bcbc on 2010-12-21
Look in that log file (it's in the %temp% directory). See if it complained about the md5 checksum. (Search on md5). 

It seems like that would be a likely reason it would fail in both cases.

You can also boot from CD, as soon as you see the little keyboard and person icon (bottom middle) press a key. That will lead you to the advanced menu where you can select "Check disk for errors".

---

### Post by zero01011 on 2010-12-22
[FONT=Calibri][SIZE=3]Accessed Advanced Menu. When I checked for disc defects  - the screen changed to UBUNTO Logo screen and it looked like it was cycling through as it had when it was trying to install - same as when I originally booted from CD. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]In the end I got the same error message &#8216;BUSYBOX  v1.15.3...&#8217;[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I also tried to Install from the Advanced Menu &#8211; same error message.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Used the Memory Test from Advanced Menu &#8211; pass complete no errors.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I looked through c:\temp\wubi-10.10rev 197.log &#8211; saw no reference to &#8216;check sum&#8217; or &#8217;md5&#8217;.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The log reads as follows - [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Code:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]_____________________________________________________________________[/SIZE][/FONT] 
**[SIZE=3][FONT=Calibri]c:\temp\wubi-10.10rev 197.log[/FONT][/SIZE]**
[FONT=Calibri]12-18 21:43 INFO   root: === wubi 10.10 rev197 ===[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  root: Logfile is c:\temp\wubi-10.10-rev197.log[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"'][/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: data_dir=C:\Temp\pyl4.tmp\data[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: 7z=C:\Temp\pyl4.tmp\bin\7z.exe[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: Fetching basic info...[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: original_exe=D:\wubi.exe[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: platform=win32[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: osname=nt[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: language=en_US[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: encoding=cp1252[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: arch=i386[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: Parsing isolist=C:\Temp\pyl4.tmp\data\isolist.ini[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: Fetching host info...[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: windows version=2000[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: windows_sp=Service Pack 4[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: windows_build=2195[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: gmt=-5[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: country=US[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: timezone=America/New_York[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: windows_username=x[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: user_full_name=x[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: user_directory=C:\[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: windows_language_code=1033[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: windows_language=English[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) III Mobile CPU      1200MHz[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: bootloader=xp[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 49283.3754883 mb free ntfs)[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: drive=Drive(C: hd 49283.3754883 mb free ntfs)[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: keyboard_id=67699721[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: keyboard_layout=us[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: keyboard_variant=[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: locale=en_US.UTF-8[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsBackend: total_memory_mb=510.921875[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: Searching ISOs on USB devices[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  CommonBackend: Searching for local CDs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Ubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Ubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Ubuntu Netbook CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Kubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Kubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Kubuntu Netbook CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Xubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Xubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Mythbuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Mythbuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro: wrong arch: i386 != amd64[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD[/FONT]
[FONT=Calibri]12-18 21:43 INFO   Distro: Found a valid CD for Ubuntu: D:\[/FONT]
[FONT=Calibri]12-18 21:43 INFO   root: Running the CD menu...[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsFrontend: __init__...[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsFrontend: on_init...[/FONT]
[FONT=Calibri]12-18 21:43 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl4.tmp\translations, languages=['en_US', 'en'][/FONT]
[FONT=Calibri]12-18 21:43 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl4.tmp\translations, languages=['en_US', 'en'][/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  root: application.quit[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsFrontend: frontend.quit[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  WindowsFrontend: frontend.on_quit[/FONT]
[FONT=Calibri]12-18 21:43 DEBUG  root: application.on_quit[/FONT]
[FONT=Calibri]12-18 21:43 INFO   root: sys.exit[/FONT]

---

### Post by bcbc on 2010-12-22
That appears to be a selection from the log file. Is there any more?

---

### Post by zero01011 on 2010-12-22
There was more, but it was only a repeat of the same info (as above) for each time that I tried the install.

---

### Post by bcbc on 2010-12-23
> **zero01011 said:**
> There was more, but it was only a repeat of the same info (as above) for each time that I tried the install.

It might look the same to you, but I can assure you it is not. Somewhere there is something related to that message - otherwise, instructing you to look in the log file would be pretty pointless.

---

