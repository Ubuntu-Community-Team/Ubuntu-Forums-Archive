---
title: "Newbie with some questions?"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Sniper Man on 2010-08-09
Hey Guys I have been watching ubuntu for a while and have tried the newest version ot Ubuntu on an old XP desktop, but I can't decide on whether or not I should get it. On one had I like being different and I think Ubuntu will help me achieve that, but on the other had my whole family and friends use windows and I know if I get this I will be build myself a little room away from everyone else which is good except when I want to share files or they want to look at something on my laptop.
 
I am also woried about my current files on my computer because if I get Ubuntu I will lose all my files (which is mostly music and videos) and I really don't want to part with that. I also own a zune and I am aware that I may not be able to sync it with my computer if I download Ubuntu, but I have a family computer that I can sync with my zune if I cannot find a way to get it to work. One other thing I like to do is record video gameplay from my xbox to my computer, I have the dazzle DVD recorder (the white one), and have heard that hardware support for Ubuntu is not very good. 
 
Well guys there is my problem I also know I don't have to do a full system switch but I really don't want to run two operating systems on one computer I have had some experience with that and I know that it can really slow down your computer.
 
I want to make the switch on my HP Pavillion DV6000
 
Thanks,
Sniper Man
 
*EDIT*
I also have a printer I share over my network to all my computers on this network through a dektop that runs vista, will there be any problems trying to print off it?

---

### Post by kr651129 on 2010-08-09
> **Sniper Man said:**
> except when I want to share files or they want to look at something on my laptop.


This is verry easy to setup with windows there are a few diffrent ways to do this depending on your needs

> **Sniper Man said:**
>  
I am also woried about my current files on my computer because if I get Ubuntu I will lose all my files (which is mostly music and videos)
 

You can buy an external hdd to store these for under $50 at your local pc store

> **Sniper Man said:**
> I also own a zune and I am aware that I may not be able to sync it with my computer 


I know that there is GTKPod that syncs ipods not sure if it will for zune and I'm *fairly* sure that amarok will sync with zunes now too..which I recomend because it kicks any windows media players ***

> **Sniper Man said:**
> One other thing I like to do is record video gameplay from my xbox to my computer, I have the dazzle DVD recorder (the white one), and have heard that hardware support for Ubuntu is not very good. 


Hardware support has come leaps and bounds from the old days of lunux you just need to do a little foot work and make sure your hardware is compatible [here]("http://ubuntuforums.org/showthread.php?t=361236")

---

### Post by CharlesA on 2010-08-09
Best advice is to boot off a livecd and see if everything works as you want it to.

---

### Post by howefield on 2010-08-09
> **Sniper Man said:**
> which is good except when I want to share files or they want to look at something on my laptop.

Why would that be a problem ?

You can share files between Windows and Ubuntu machines.
 
> I am also woried about my current files on my computer because if I get Ubuntu I will lose all my files

Worried about what ? Playing them ?

That is unlikely to be a problem.

> I also own a zune and I am aware that I may not be able to sync it with my computer if I download Ubuntu, but I have a family computer that I can sync with my zune if I cannot find a way to get it to work. One other thing I like to do is record video gameplay from my xbox to my computer, I have the dazzle DVD recorder (the white one), and have heard that hardware support for Ubuntu is not very good.

Can't help you with any of that. 

> I really don't want to run two operating systems on one computer I have had some experience with that and I know that it can really slow down your computer.

Haven't seen that before, dual booting is a good way of keeping the familiar whilst you get your head around the new.

You either want to learn a new operating system or you don't. Being half hearted is probably not a good start to learning something new, you'll likely end up frustrated.

But if you do need help, just keep posting here. Someone is likely to be able to help.

---

### Post by howefield on 2010-08-09
Ooops... sorry.

Double post.

---

### Post by kr651129 on 2010-08-09
And if it comes down to it and you can't get your zune to work you can actually run xp inside of ubuntu for applications like that using VMWare

---

### Post by new__buntu on 2010-08-09
> **CharlesA said:**
> Best advice is to boot off a livecd and see if everything works as you want it to.

This, or perhaps a [wubi]("http://wubi-installer.org/") install. Either way a test drive certainly won't hurt.

---

### Post by anewguy on 2010-08-09
And, if I might suggest, after trying the LiveCD, why not install Ubuntu for dual-boot with Windows on the machine for now?  If you have done a wubi install (e.g., ubuntu from Windows), you should probably delete that first.  Then just repartition your hard drive (via the installation procedure when installing ubuntu) to add some space for Ubuntu - if you are just testing 10gb should be more than enough.  Remember that when you use the repartition/dual-boot method that (1) you shouldn't lose any data from your Windows side and (2) you'll be able to see the Windows partition and access it from within Ubuntu (I don't know about accessing Ubuntu from Windows).

If you do decide to try dual-boot, remember to defrag your hard disk under Windows 2 times or so, even though it might say it doesn't need it, BEFORE you go to installing ubuntu for dual-boot.

The option to dual-boot is very simple, and there are multiple posts and how-to's on the forums for that, however if you have any questions or concerns, or want to know more about doing so, just post back.

Dave ;)

---

### Post by Sniper Man on 2010-08-11
Ok so I tried to run the live CD off of my laptop and I just got a kind of messed up screen when if finally loaded up.  I want to know what I need to do to make it load right.  
 
Thanks,
Sniper Man

---

### Post by Devastator9 on 2010-08-11
I have the same laptop and everything works great, I will never ever go back to windoze as I do love my freedom.

---

### Post by Sniper Man on 2010-08-12
Hey guys I was trying to install Ubuntu to run side by side with windows but I got an error and it said to check one of my log files I will post it under this.
 
> 08-09 14:19 INFO   root: === wubi 10.04 rev189 ===
08-09 14:19 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-09 14:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
08-09 14:19 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\data
08-09 14:19 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\bin\7z.exe
08-09 14:19 DEBUG  CommonBackend: Fetching basic info...
08-09 14:19 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-09 14:19 DEBUG  CommonBackend: platform=win32
08-09 14:19 DEBUG  CommonBackend: osname=nt
08-09 14:19 DEBUG  CommonBackend: language=en_US
08-09 14:19 DEBUG  CommonBackend: encoding=cp1252
08-09 14:19 DEBUG  WindowsBackend: arch=amd64
08-09 14:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\data\isolist.ini
08-09 14:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-09 14:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-09 14:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-09 14:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-09 14:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-09 14:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-09 14:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-09 14:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-09 14:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-09 14:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-09 14:19 DEBUG  WindowsBackend: Fetching host info...
08-09 14:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-09 14:19 DEBUG  WindowsBackend: windows version=vista
08-09 14:19 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-09 14:19 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-09 14:19 DEBUG  WindowsBackend: windows_build=6002
08-09 14:19 DEBUG  WindowsBackend: gmt=-6
08-09 14:19 DEBUG  WindowsBackend: country=US
08-09 14:19 DEBUG  WindowsBackend: timezone=America/Chicago
08-09 14:19 DEBUG  WindowsBackend: windows_username=Jace
08-09 14:19 DEBUG  WindowsBackend: user_full_name=Jace
08-09 14:19 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-09 14:19 DEBUG  WindowsBackend: windows_language_code=1033
08-09 14:19 DEBUG  WindowsBackend: windows_language=English
08-09 14:19 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-09 14:19 DEBUG  WindowsBackend: bootloader=vista
08-09 14:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68591.0273438 mb free ntfs)
08-09 14:19 DEBUG  WindowsBackend: drive=Drive(C: hd 68591.0273438 mb free ntfs)
08-09 14:19 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-09 14:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-09 14:19 DEBUG  WindowsBackend: uninstaller_path=None
08-09 14:19 DEBUG  WindowsBackend: previous_target_dir=None
08-09 14:19 DEBUG  WindowsBackend: previous_distro_name=None
08-09 14:19 DEBUG  WindowsBackend: keyboard_id=67699721
08-09 14:19 DEBUG  WindowsBackend: keyboard_layout=us
08-09 14:19 DEBUG  WindowsBackend: keyboard_variant=
08-09 14:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-09 14:19 DEBUG  CommonBackend: locale=en_US.UTF-8
08-09 14:19 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-09 14:19 DEBUG  CommonBackend: Searching ISOs on USB devices
08-09 14:19 DEBUG  CommonBackend: Searching for local CDs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Ubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Ubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Ubuntu Netbook CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Kubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Kubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Kubuntu Netbook CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Xubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Xubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Mythbuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp is a valid Mythbuntu CD
08-09 14:19 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-09 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-09 14:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-09 14:19 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-09 14:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-09 14:19 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-09 14:19 INFO   root: Running the CD menu...
08-09 14:19 DEBUG  WindowsFrontend: __init__...
08-09 14:19 DEBUG  WindowsFrontend: on_init...
08-09 14:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\translations, languages=['en_US', 'en']
08-09 14:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl1554.tmp\translations, languages=['en_US', 'en']
08-09 14:20 INFO   WindowsFrontend: Operation cancelled
08-09 14:20 DEBUG  WindowsFrontend: frontend.quit
08-09 14:20 DEBUG  WindowsFrontend: frontend.on_quit
08-09 14:20 DEBUG  root: application.on_quit
08-09 14:20 INFO   root: sys.exit
08-10 15:55 INFO   root: === wubi 10.04 rev189 ===
08-10 15:55 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-10 15:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
08-10 15:55 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\data
08-10 15:55 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\bin\7z.exe
08-10 15:55 DEBUG  CommonBackend: Fetching basic info...
08-10 15:55 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-10 15:55 DEBUG  CommonBackend: platform=win32
08-10 15:55 DEBUG  CommonBackend: osname=nt
08-10 15:55 DEBUG  CommonBackend: language=en_US
08-10 15:55 DEBUG  CommonBackend: encoding=cp1252
08-10 15:55 DEBUG  WindowsBackend: arch=amd64
08-10 15:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\data\isolist.ini
08-10 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 15:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 15:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 15:55 DEBUG  WindowsBackend: Fetching host info...
08-10 15:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 15:55 DEBUG  WindowsBackend: windows version=vista
08-10 15:55 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 15:55 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 15:55 DEBUG  WindowsBackend: windows_build=6002
08-10 15:55 DEBUG  WindowsBackend: gmt=-6
08-10 15:55 DEBUG  WindowsBackend: country=US
08-10 15:55 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 15:55 DEBUG  WindowsBackend: windows_username=Jace
08-10 15:55 DEBUG  WindowsBackend: user_full_name=Jace
08-10 15:55 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 15:55 DEBUG  WindowsBackend: windows_language_code=1033
08-10 15:55 DEBUG  WindowsBackend: windows_language=English
08-10 15:55 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 15:55 DEBUG  WindowsBackend: bootloader=vista
08-10 15:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65728.0195313 mb free ntfs)
08-10 15:55 DEBUG  WindowsBackend: drive=Drive(C: hd 65728.0195313 mb free ntfs)
08-10 15:55 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 15:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 15:55 DEBUG  WindowsBackend: uninstaller_path=None
08-10 15:55 DEBUG  WindowsBackend: previous_target_dir=None
08-10 15:55 DEBUG  WindowsBackend: previous_distro_name=None
08-10 15:55 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 15:55 DEBUG  WindowsBackend: keyboard_layout=us
08-10 15:55 DEBUG  WindowsBackend: keyboard_variant=
08-10 15:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-10 15:55 DEBUG  CommonBackend: locale=en_US.UTF-8
08-10 15:55 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 15:55 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 15:55 DEBUG  CommonBackend: Searching for local CDs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Ubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Ubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Ubuntu Netbook CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Kubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Kubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Kubuntu Netbook CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Xubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Xubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Mythbuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp is a valid Mythbuntu CD
08-10 15:55 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 15:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-10 15:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-10 15:55 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 15:55 INFO   root: Running the CD menu...
08-10 15:55 DEBUG  WindowsFrontend: __init__...
08-10 15:55 DEBUG  WindowsFrontend: on_init...
08-10 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\translations, languages=['en_US', 'en']
08-10 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\translations, languages=['en_US', 'en']
08-10 15:56 INFO   root: CD menu finished
08-10 15:56 INFO   root: Running the CD boot helper...
08-10 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\translations, languages=['en_US', 'en']
08-10 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylE7CB.tmp\translations, languages=['en_US', 'en']
08-10 15:56 INFO   WindowsFrontend: Operation cancelled
08-10 15:56 DEBUG  WindowsFrontend: frontend.quit
08-10 15:56 DEBUG  WindowsFrontend: frontend.on_quit
08-10 15:56 DEBUG  root: application.on_quit
08-10 15:56 INFO   root: sys.exit
08-10 15:56 INFO   root: === wubi 10.04 rev189 ===
08-10 15:56 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-10 15:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
08-10 15:56 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\data
08-10 15:56 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\bin\7z.exe
08-10 15:56 DEBUG  CommonBackend: Fetching basic info...
08-10 15:56 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-10 15:56 DEBUG  CommonBackend: platform=win32
08-10 15:56 DEBUG  CommonBackend: osname=nt
08-10 15:56 DEBUG  CommonBackend: language=en_US
08-10 15:56 DEBUG  CommonBackend: encoding=cp1252
08-10 15:56 DEBUG  WindowsBackend: arch=amd64
08-10 15:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\data\isolist.ini
08-10 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 15:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 15:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 15:56 DEBUG  WindowsBackend: Fetching host info...
08-10 15:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 15:56 DEBUG  WindowsBackend: windows version=vista
08-10 15:56 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 15:56 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 15:56 DEBUG  WindowsBackend: windows_build=6002
08-10 15:56 DEBUG  WindowsBackend: gmt=-6
08-10 15:56 DEBUG  WindowsBackend: country=US
08-10 15:56 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 15:56 DEBUG  WindowsBackend: windows_username=Jace
08-10 15:56 DEBUG  WindowsBackend: user_full_name=Jace
08-10 15:56 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 15:56 DEBUG  WindowsBackend: windows_language_code=1033
08-10 15:56 DEBUG  WindowsBackend: windows_language=English
08-10 15:56 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 15:56 DEBUG  WindowsBackend: bootloader=vista
08-10 15:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65718.9257813 mb free ntfs)
08-10 15:56 DEBUG  WindowsBackend: drive=Drive(C: hd 65718.9257813 mb free ntfs)
08-10 15:56 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 15:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 15:56 DEBUG  WindowsBackend: uninstaller_path=None
08-10 15:56 DEBUG  WindowsBackend: previous_target_dir=None
08-10 15:56 DEBUG  WindowsBackend: previous_distro_name=None
08-10 15:56 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 15:56 DEBUG  WindowsBackend: keyboard_layout=us
08-10 15:56 DEBUG  WindowsBackend: keyboard_variant=
08-10 15:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-10 15:56 DEBUG  CommonBackend: locale=en_US.UTF-8
08-10 15:56 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 15:56 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 15:56 DEBUG  CommonBackend: Searching for local CDs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Ubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Ubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Ubuntu Netbook CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Kubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Kubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Kubuntu Netbook CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Xubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Xubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Mythbuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylB7.tmp is a valid Mythbuntu CD
08-10 15:56 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 15:56 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-10 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-10 15:56 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 15:56 INFO   root: Running the CD menu...
08-10 15:56 DEBUG  WindowsFrontend: __init__...
08-10 15:56 DEBUG  WindowsFrontend: on_init...
08-10 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\translations, languages=['en_US', 'en']
08-10 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylB7.tmp\translations, languages=['en_US', 'en']
08-10 15:56 INFO   root: CD menu finished
08-10 15:56 INFO   root: Rebooting
08-10 15:56 DEBUG  TaskList: # Running tasklist...
08-10 15:56 DEBUG  TaskList: ## Running reboot...
08-10 15:56 DEBUG  TaskList: ## Finished reboot
08-10 15:56 DEBUG  TaskList: # Finished tasklist
08-10 15:56 DEBUG  root: application.quit
08-10 15:56 DEBUG  WindowsFrontend: frontend.quit
08-10 15:56 DEBUG  WindowsFrontend: frontend.on_quit
08-10 15:56 DEBUG  root: application.on_quit
08-10 15:56 INFO   root: sys.exit
08-10 16:04 INFO   root: === wubi 10.04 rev189 ===
08-10 16:04 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-10 16:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
08-10 16:04 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\data
08-10 16:04 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\bin\7z.exe
08-10 16:04 DEBUG  CommonBackend: Fetching basic info...
08-10 16:04 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-10 16:04 DEBUG  CommonBackend: platform=win32
08-10 16:04 DEBUG  CommonBackend: osname=nt
08-10 16:04 DEBUG  CommonBackend: language=en_US
08-10 16:04 DEBUG  CommonBackend: encoding=cp1252
08-10 16:04 DEBUG  WindowsBackend: arch=amd64
08-10 16:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\data\isolist.ini
08-10 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 16:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 16:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 16:04 DEBUG  WindowsBackend: Fetching host info...
08-10 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 16:04 DEBUG  WindowsBackend: windows version=vista
08-10 16:04 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 16:04 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 16:04 DEBUG  WindowsBackend: windows_build=6002
08-10 16:04 DEBUG  WindowsBackend: gmt=-6
08-10 16:04 DEBUG  WindowsBackend: country=US
08-10 16:04 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 16:04 DEBUG  WindowsBackend: windows_username=Jace
08-10 16:04 DEBUG  WindowsBackend: user_full_name=Jace
08-10 16:04 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 16:04 DEBUG  WindowsBackend: windows_language_code=1033
08-10 16:04 DEBUG  WindowsBackend: windows_language=English
08-10 16:04 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 16:04 DEBUG  WindowsBackend: bootloader=vista
08-10 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65744.03125 mb free ntfs)
08-10 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 65744.03125 mb free ntfs)
08-10 16:04 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 16:04 DEBUG  WindowsBackend: uninstaller_path=None
08-10 16:04 DEBUG  WindowsBackend: previous_target_dir=None
08-10 16:04 DEBUG  WindowsBackend: previous_distro_name=None
08-10 16:04 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 16:04 DEBUG  WindowsBackend: keyboard_layout=us
08-10 16:04 DEBUG  WindowsBackend: keyboard_variant=
08-10 16:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-10 16:04 DEBUG  CommonBackend: locale=en_US.UTF-8
08-10 16:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 16:04 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 16:04 DEBUG  CommonBackend: Searching for local CDs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Ubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Ubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Ubuntu Netbook CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Kubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Kubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Kubuntu Netbook CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Xubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Xubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Mythbuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylC689.tmp is a valid Mythbuntu CD
08-10 16:04 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 16:04 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-10 16:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-10 16:04 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 16:04 INFO   root: Running the CD menu...
08-10 16:04 DEBUG  WindowsFrontend: __init__...
08-10 16:04 DEBUG  WindowsFrontend: on_init...
08-10 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\translations, languages=['en_US', 'en']
08-10 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\translations, languages=['en_US', 'en']
08-10 16:04 INFO   root: CD menu finished
08-10 16:04 INFO   root: Running the CD boot helper...
08-10 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\translations, languages=['en_US', 'en']
08-10 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\translations, languages=['en_US', 'en']
08-10 16:04 INFO   root: CD boot helper confirmed
08-10 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\translations, languages=['en_US', 'en']
08-10 16:04 DEBUG  TaskList: # Running tasklist...
08-10 16:04 DEBUG  TaskList: ## Running select_target_dir...
08-10 16:04 INFO   WindowsBackend: Installing into C:\ubuntu
08-10 16:04 DEBUG  TaskList: ## Finished select_target_dir
08-10 16:04 DEBUG  TaskList: ## Running create_dir_structure...
08-10 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-10 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-10 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-10 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-10 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-10 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-10 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-10 16:04 DEBUG  TaskList: ## Finished create_dir_structure
08-10 16:04 DEBUG  TaskList: ## Running uncompress_target_dir...
08-10 16:04 DEBUG  TaskList: ## Finished uncompress_target_dir
08-10 16:04 DEBUG  TaskList: ## Running create_uninstaller...
08-10 16:04 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-10 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-10 16:04 DEBUG  TaskList: ## Finished create_uninstaller
08-10 16:04 DEBUG  TaskList: ## Running copy_installation_files...
08-10 16:04 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-10 16:04 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\winboot -> C:\ubuntu\winboot
08-10 16:04 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pylC689.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-10 16:04 DEBUG  TaskList: ## Finished copy_installation_files
08-10 16:04 DEBUG  TaskList: ## Running use_cd...
08-10 16:04 DEBUG  TaskList: New task copy_file
08-10 16:04 DEBUG  TaskList: ### Running copy_file...
08-10 16:09 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
08-10 16:09 DEBUG  TaskList: # Cancelling tasklist
08-10 16:09 DEBUG  TaskList: New task check_iso
08-10 16:09 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
08-10 16:09 DEBUG  TaskList: ## Finished use_cd
08-10 16:09 DEBUG  TaskList: # Finished tasklist
08-10 16:28 INFO   root: === wubi 10.04 rev189 ===
08-10 16:28 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-10 16:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
08-10 16:28 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\data
08-10 16:28 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\bin\7z.exe
08-10 16:28 DEBUG  CommonBackend: Fetching basic info...
08-10 16:28 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-10 16:28 DEBUG  CommonBackend: platform=win32
08-10 16:28 DEBUG  CommonBackend: osname=nt
08-10 16:28 DEBUG  CommonBackend: language=en_US
08-10 16:28 DEBUG  CommonBackend: encoding=cp1252
08-10 16:28 DEBUG  WindowsBackend: arch=amd64
08-10 16:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\data\isolist.ini
08-10 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 16:28 DEBUG  WindowsBackend: Fetching host info...
08-10 16:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 16:28 DEBUG  WindowsBackend: windows version=vista
08-10 16:28 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 16:28 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 16:28 DEBUG  WindowsBackend: windows_build=6002
08-10 16:28 DEBUG  WindowsBackend: gmt=-6
08-10 16:28 DEBUG  WindowsBackend: country=US
08-10 16:28 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 16:28 DEBUG  WindowsBackend: windows_username=Jace
08-10 16:28 DEBUG  WindowsBackend: user_full_name=Jace
08-10 16:28 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 16:28 DEBUG  WindowsBackend: windows_language_code=1033
08-10 16:28 DEBUG  WindowsBackend: windows_language=English
08-10 16:28 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 16:28 DEBUG  WindowsBackend: bootloader=vista
08-10 16:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64949.1210938 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(C: hd 64949.1210938 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 16:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-10 16:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-10 16:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-10 16:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 16:28 DEBUG  WindowsBackend: keyboard_layout=us
08-10 16:28 DEBUG  WindowsBackend: keyboard_variant=
08-10 16:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-10 16:28 DEBUG  CommonBackend: locale=en_US.UTF-8
08-10 16:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 16:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 16:28 DEBUG  CommonBackend: Searching for local CDs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Ubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Kubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-10 16:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-10 16:28 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 16:28 INFO   root: Running the CD menu...
08-10 16:28 DEBUG  WindowsFrontend: __init__...
08-10 16:28 DEBUG  WindowsFrontend: on_init...
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\translations, languages=['en_US', 'en']
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\translations, languages=['en_US', 'en']
08-10 16:28 INFO   root: CD menu finished
08-10 16:28 INFO   root: Already installed, running the uninstaller...
08-10 16:28 INFO   root: Running the uninstaller...
08-10 16:28 INFO   CommonBackend: This is the uninstaller running
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\translations, languages=['en_US', 'en']
08-10 16:28 INFO   root: === wubi 10.04 rev189 ===
08-10 16:28 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-10 16:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
08-10 16:28 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\data
08-10 16:28 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\bin\7z.exe
08-10 16:28 DEBUG  CommonBackend: Fetching basic info...
08-10 16:28 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-10 16:28 DEBUG  CommonBackend: platform=win32
08-10 16:28 DEBUG  CommonBackend: osname=nt
08-10 16:28 DEBUG  CommonBackend: language=en_US
08-10 16:28 DEBUG  CommonBackend: encoding=cp1252
08-10 16:28 DEBUG  WindowsBackend: arch=amd64
08-10 16:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\data\isolist.ini
08-10 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 16:28 DEBUG  WindowsBackend: Fetching host info...
08-10 16:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 16:28 DEBUG  WindowsBackend: windows version=vista
08-10 16:28 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 16:28 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 16:28 DEBUG  WindowsBackend: windows_build=6002
08-10 16:28 DEBUG  WindowsBackend: gmt=-6
08-10 16:28 DEBUG  WindowsBackend: country=US
08-10 16:28 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 16:28 DEBUG  WindowsBackend: windows_username=Jace
08-10 16:28 DEBUG  WindowsBackend: user_full_name=Jace
08-10 16:28 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 16:28 DEBUG  WindowsBackend: windows_language_code=1033
08-10 16:28 DEBUG  WindowsBackend: windows_language=English
08-10 16:28 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 16:28 DEBUG  WindowsBackend: bootloader=vista
08-10 16:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64943.8046875 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(C: hd 64943.8046875 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 16:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-10 16:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-10 16:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-10 16:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 16:28 DEBUG  WindowsBackend: keyboard_layout=us
08-10 16:28 DEBUG  WindowsBackend: keyboard_variant=
08-10 16:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-10 16:28 DEBUG  CommonBackend: locale=en_US.UTF-8
08-10 16:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 16:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 16:28 DEBUG  CommonBackend: Searching for local CDs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Ubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Kubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-10 16:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-10 16:28 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 16:28 INFO   root: Running the CD menu...
08-10 16:28 DEBUG  WindowsFrontend: __init__...
08-10 16:28 DEBUG  WindowsFrontend: on_init...
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\translations, languages=['en_US', 'en']
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylE9E1.tmp\translations, languages=['en_US', 'en']
08-10 16:28 INFO   root: Received settings
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\translations, languages=['en_US', 'en']
08-10 16:28 DEBUG  TaskList: # Running tasklist...
08-10 16:28 DEBUG  TaskList: ## Running Backup ISO...
08-10 16:28 DEBUG  TaskList: ## Finished Backup ISO
08-10 16:28 DEBUG  TaskList: ## Running Remove bootloader entry...
08-10 16:28 DEBUG  WindowsBackend: Could not find bcd id
08-10 16:28 DEBUG  WindowsBackend: undo_bootini C:
08-10 16:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 64949.1210938 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: undo_bootini D:
08-10 16:28 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:28 DEBUG  TaskList: ## Finished Remove bootloader entry
08-10 16:28 DEBUG  TaskList: ## Running Remove target dir...
08-10 16:28 DEBUG  CommonBackend: Deleting C:\ubuntu
08-10 16:28 DEBUG  TaskList: ## Finished Remove target dir
08-10 16:28 DEBUG  TaskList: ## Running Remove registry key...
08-10 16:28 DEBUG  TaskList: ## Finished Remove registry key
08-10 16:28 DEBUG  TaskList: # Finished tasklist
08-10 16:28 INFO   root: Almost finished uninstalling
08-10 16:28 INFO   root: Finished uninstallation
08-10 16:28 DEBUG  CommonBackend: Fetching basic info...
08-10 16:28 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-10 16:28 DEBUG  CommonBackend: platform=win32
08-10 16:28 DEBUG  CommonBackend: osname=nt
08-10 16:28 DEBUG  WindowsBackend: arch=amd64
08-10 16:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\data\isolist.ini
08-10 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 16:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 16:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 16:28 DEBUG  WindowsBackend: Fetching host info...
08-10 16:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 16:28 DEBUG  WindowsBackend: windows version=vista
08-10 16:28 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 16:28 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 16:28 DEBUG  WindowsBackend: windows_build=6002
08-10 16:28 DEBUG  WindowsBackend: gmt=-6
08-10 16:28 DEBUG  WindowsBackend: country=US
08-10 16:28 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 16:28 DEBUG  WindowsBackend: windows_username=Jace
08-10 16:28 DEBUG  WindowsBackend: user_full_name=Jace
08-10 16:28 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 16:28 DEBUG  WindowsBackend: windows_language_code=1033
08-10 16:28 DEBUG  WindowsBackend: windows_language=English
08-10 16:28 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 16:28 DEBUG  WindowsBackend: bootloader=vista
08-10 16:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65637.2265625 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(C: hd 65637.2265625 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 16:28 DEBUG  WindowsBackend: uninstaller_path=None
08-10 16:28 DEBUG  WindowsBackend: previous_target_dir=None
08-10 16:28 DEBUG  WindowsBackend: previous_distro_name=None
08-10 16:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 16:28 DEBUG  WindowsBackend: keyboard_layout=us
08-10 16:28 DEBUG  WindowsBackend: keyboard_variant=
08-10 16:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 16:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 16:28 DEBUG  CommonBackend: Searching for local CDs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Ubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Kubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 16:28 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 16:28 INFO   root: Running the installer...
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\translations, languages=['en_US', 'en']
08-10 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\translations, languages=['en_US', 'en']
08-10 16:29 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jace
08-10 16:29 INFO   root: Received settings
08-10 16:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\translations, languages=['en_US', 'en']
08-10 16:29 DEBUG  TaskList: # Running tasklist...
08-10 16:29 DEBUG  TaskList: ## Running select_target_dir...
08-10 16:29 INFO   WindowsBackend: Installing into C:\ubuntu
08-10 16:29 DEBUG  TaskList: ## Finished select_target_dir
08-10 16:29 DEBUG  TaskList: ## Running create_dir_structure...
08-10 16:29 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-10 16:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-10 16:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-10 16:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-10 16:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-10 16:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-10 16:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-10 16:29 DEBUG  TaskList: ## Finished create_dir_structure
08-10 16:29 DEBUG  TaskList: ## Running uncompress_target_dir...
08-10 16:29 DEBUG  TaskList: ## Finished uncompress_target_dir
08-10 16:29 DEBUG  TaskList: ## Running create_uninstaller...
08-10 16:29 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-10 16:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-10 16:29 DEBUG  TaskList: ## Finished create_uninstaller
08-10 16:29 DEBUG  TaskList: ## Running copy_installation_files...
08-10 16:29 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-10 16:29 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\winboot -> C:\ubuntu\winboot
08-10 16:29 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pylDE6C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-10 16:29 DEBUG  TaskList: ## Finished copy_installation_files
08-10 16:29 DEBUG  TaskList: ## Running get_iso...
08-10 16:29 DEBUG  TaskList: New task copy_file
08-10 16:29 DEBUG  TaskList: ### Running copy_file...
08-10 16:29 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
08-10 16:29 DEBUG  TaskList: # Cancelling tasklist
08-10 16:29 DEBUG  TaskList: New task check_iso
08-10 16:29 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
08-10 16:29 DEBUG  CommonBackend: Searching for local ISO
08-10 16:29 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-10 16:29 DEBUG  TaskList: New task get_metalink
08-10 16:29 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-10 16:29 DEBUG  TaskList: # Cancelling tasklist
08-10 16:29 DEBUG  TaskList: # Finished tasklist
08-10 16:30 INFO   root: === wubi 10.04 rev189 ===
08-10 16:30 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-10 16:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
08-10 16:30 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\data
08-10 16:30 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\bin\7z.exe
08-10 16:30 DEBUG  CommonBackend: Fetching basic info...
08-10 16:30 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
08-10 16:30 DEBUG  CommonBackend: platform=win32
08-10 16:30 DEBUG  CommonBackend: osname=nt
08-10 16:30 DEBUG  CommonBackend: language=en_US
08-10 16:30 DEBUG  CommonBackend: encoding=cp1252
08-10 16:30 DEBUG  WindowsBackend: arch=amd64
08-10 16:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\data\isolist.ini
08-10 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 16:30 DEBUG  WindowsBackend: Fetching host info...
08-10 16:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 16:30 DEBUG  WindowsBackend: windows version=vista
08-10 16:30 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 16:30 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 16:30 DEBUG  WindowsBackend: windows_build=6002
08-10 16:30 DEBUG  WindowsBackend: gmt=-6
08-10 16:30 DEBUG  WindowsBackend: country=US
08-10 16:30 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 16:30 DEBUG  WindowsBackend: windows_username=Jace
08-10 16:30 DEBUG  WindowsBackend: user_full_name=Jace
08-10 16:30 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 16:30 DEBUG  WindowsBackend: windows_language_code=1033
08-10 16:30 DEBUG  WindowsBackend: windows_language=English
08-10 16:30 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 16:30 DEBUG  WindowsBackend: bootloader=vista
08-10 16:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65627.7382813 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: drive=Drive(C: hd 65627.7382813 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 16:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-10 16:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-10 16:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-10 16:30 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 16:30 DEBUG  WindowsBackend: keyboard_layout=us
08-10 16:30 DEBUG  WindowsBackend: keyboard_variant=
08-10 16:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-10 16:30 DEBUG  CommonBackend: locale=en_US.UTF-8
08-10 16:30 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 16:30 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 16:30 DEBUG  CommonBackend: Searching for local CDs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Ubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Kubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-10 16:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-10 16:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 16:30 INFO   root: Running the uninstaller...
08-10 16:30 INFO   CommonBackend: This is the uninstaller running
08-10 16:30 DEBUG  WindowsFrontend: __init__...
08-10 16:30 DEBUG  WindowsFrontend: on_init...
08-10 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\translations, languages=['en_US', 'en']
08-10 16:30 INFO   root: Received settings
08-10 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl57C.tmp\translations, languages=['en_US', 'en']
08-10 16:30 DEBUG  TaskList: # Running tasklist...
08-10 16:30 DEBUG  TaskList: ## Running Backup ISO...
08-10 16:30 DEBUG  TaskList: ## Finished Backup ISO
08-10 16:30 DEBUG  TaskList: ## Running Remove bootloader entry...
08-10 16:30 DEBUG  WindowsBackend: Could not find bcd id
08-10 16:30 DEBUG  WindowsBackend: undo_bootini C:
08-10 16:30 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 65627.7382813 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: undo_bootini D:
08-10 16:30 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:30 DEBUG  TaskList: ## Finished Remove bootloader entry
08-10 16:30 DEBUG  TaskList: ## Running Remove target dir...
08-10 16:30 DEBUG  CommonBackend: Deleting C:\ubuntu
08-10 16:30 ERROR  TaskList: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 644, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 317, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
08-10 16:30 DEBUG  TaskList: # Cancelling tasklist
08-10 16:30 DEBUG  TaskList: # Finished tasklist
08-10 16:30 ERROR  root: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 644, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 317, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
08-10 16:30 INFO   root: === wubi 10.04 rev189 ===
08-10 16:30 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-10 16:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
08-10 16:30 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\data
08-10 16:30 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\bin\7z.exe
08-10 16:30 DEBUG  CommonBackend: Fetching basic info...
08-10 16:30 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
08-10 16:30 DEBUG  CommonBackend: platform=win32
08-10 16:30 DEBUG  CommonBackend: osname=nt
08-10 16:30 DEBUG  CommonBackend: language=en_US
08-10 16:30 DEBUG  CommonBackend: encoding=cp1252
08-10 16:30 DEBUG  WindowsBackend: arch=amd64
08-10 16:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\data\isolist.ini
08-10 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-10 16:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-10 16:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-10 16:30 DEBUG  WindowsBackend: Fetching host info...
08-10 16:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-10 16:30 DEBUG  WindowsBackend: windows version=vista
08-10 16:30 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-10 16:30 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-10 16:30 DEBUG  WindowsBackend: windows_build=6002
08-10 16:30 DEBUG  WindowsBackend: gmt=-6
08-10 16:30 DEBUG  WindowsBackend: country=US
08-10 16:30 DEBUG  WindowsBackend: timezone=America/Chicago
08-10 16:30 DEBUG  WindowsBackend: windows_username=Jace
08-10 16:30 DEBUG  WindowsBackend: user_full_name=Jace
08-10 16:30 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-10 16:30 DEBUG  WindowsBackend: windows_language_code=1033
08-10 16:30 DEBUG  WindowsBackend: windows_language=English
08-10 16:30 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-10 16:30 DEBUG  WindowsBackend: bootloader=vista
08-10 16:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65626.9726563 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: drive=Drive(C: hd 65626.9726563 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-10 16:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-10 16:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-10 16:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-10 16:30 DEBUG  WindowsBackend: keyboard_id=67699721
08-10 16:30 DEBUG  WindowsBackend: keyboard_layout=us
08-10 16:30 DEBUG  WindowsBackend: keyboard_variant=
08-10 16:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-10 16:30 DEBUG  CommonBackend: locale=en_US.UTF-8
08-10 16:30 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-10 16:30 DEBUG  CommonBackend: Searching ISOs on USB devices
08-10 16:30 DEBUG  CommonBackend: Searching for local CDs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Ubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Kubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-10 16:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-10 16:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-10 16:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-10 16:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-10 16:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-10 16:30 INFO   root: Running the uninstaller...
08-10 16:30 INFO   CommonBackend: This is the uninstaller running
08-10 16:30 DEBUG  WindowsFrontend: __init__...
08-10 16:30 DEBUG  WindowsFrontend: on_init...
08-10 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\translations, languages=['en_US', 'en']
08-10 16:30 INFO   root: Received settings
08-10 16:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl5031.tmp\translations, languages=['en_US', 'en']
08-10 16:30 DEBUG  TaskList: # Running tasklist...
08-10 16:30 DEBUG  TaskList: ## Running Backup ISO...
08-10 16:30 DEBUG  TaskList: ## Finished Backup ISO
08-10 16:30 DEBUG  TaskList: ## Running Remove bootloader entry...
08-10 16:30 DEBUG  WindowsBackend: Could not find bcd id
08-10 16:30 DEBUG  WindowsBackend: undo_bootini C:
08-10 16:30 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 65626.9726563 mb free ntfs)
08-10 16:30 DEBUG  WindowsBackend: undo_bootini D:
08-10 16:30 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 11934.9570313 mb free ntfs)
08-10 16:30 DEBUG  TaskList: ## Finished Remove bootloader entry
08-10 16:30 DEBUG  TaskList: ## Running Remove target dir...
08-10 16:30 DEBUG  CommonBackend: Deleting C:\ubuntu
08-10 16:30 ERROR  TaskList: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 644, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 317, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
08-10 16:30 DEBUG  TaskList: # Cancelling tasklist
08-10 16:30 DEBUG  TaskList: # Finished tasklist
08-10 16:30 ERROR  root: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 644, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 317, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
08-10 16:31 DEBUG  WindowsFrontend: frontend.on_quit
08-10 16:31 DEBUG  root: application.on_quit
08-10 16:31 INFO   root: sys.exit
08-11 23:32 INFO   root: === wubi 10.04 rev189 ===
08-11 23:32 DEBUG  root: Logfile is c:\users\jace\appdata\local\temp\wubi-10.04-rev189.log
08-11 23:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
08-11 23:32 DEBUG  CommonBackend: data_dir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\data
08-11 23:32 DEBUG  WindowsBackend: 7z=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\bin\7z.exe
08-11 23:32 DEBUG  CommonBackend: Fetching basic info...
08-11 23:32 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-11 23:32 DEBUG  CommonBackend: platform=win32
08-11 23:32 DEBUG  CommonBackend: osname=nt
08-11 23:32 DEBUG  CommonBackend: language=en_US
08-11 23:32 DEBUG  CommonBackend: encoding=cp1252
08-11 23:32 DEBUG  WindowsBackend: arch=amd64
08-11 23:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\data\isolist.ini
08-11 23:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-11 23:32 DEBUG  WindowsBackend: Fetching host info...
08-11 23:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-11 23:32 DEBUG  WindowsBackend: windows version=vista
08-11 23:32 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-11 23:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-11 23:32 DEBUG  WindowsBackend: windows_build=6002
08-11 23:32 DEBUG  WindowsBackend: gmt=-6
08-11 23:32 DEBUG  WindowsBackend: country=US
08-11 23:32 DEBUG  WindowsBackend: timezone=America/Chicago
08-11 23:32 DEBUG  WindowsBackend: windows_username=Jace
08-11 23:32 DEBUG  WindowsBackend: user_full_name=Jace
08-11 23:32 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-11 23:32 DEBUG  WindowsBackend: windows_language_code=1033
08-11 23:32 DEBUG  WindowsBackend: windows_language=English
08-11 23:32 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-11 23:32 DEBUG  WindowsBackend: bootloader=vista
08-11 23:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59592.6015625 mb free ntfs)
08-11 23:32 DEBUG  WindowsBackend: drive=Drive(C: hd 59592.6015625 mb free ntfs)
08-11 23:32 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-11 23:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-11 23:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-11 23:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-11 23:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-11 23:32 DEBUG  WindowsBackend: keyboard_id=67699721
08-11 23:32 DEBUG  WindowsBackend: keyboard_layout=us
08-11 23:32 DEBUG  WindowsBackend: keyboard_variant=
08-11 23:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-11 23:32 DEBUG  CommonBackend: locale=en_US.UTF-8
08-11 23:32 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-11 23:32 DEBUG  CommonBackend: Searching ISOs on USB devices
08-11 23:32 DEBUG  CommonBackend: Searching for local CDs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Ubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Kubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-11 23:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-11 23:32 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-11 23:32 INFO   root: Running the CD menu...
08-11 23:32 DEBUG  WindowsFrontend: __init__...
08-11 23:32 DEBUG  WindowsFrontend: on_init...
08-11 23:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\translations, languages=['en_US', 'en']
08-11 23:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\translations, languages=['en_US', 'en']
08-11 23:32 INFO   root: CD menu finished
08-11 23:32 INFO   root: Already installed, running the uninstaller...
08-11 23:32 INFO   root: Running the uninstaller...
08-11 23:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\translations, languages=['en_US', 'en']
08-11 23:32 INFO   root: Received settings
08-11 23:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\translations, languages=['en_US', 'en']
08-11 23:32 DEBUG  TaskList: # Running tasklist...
08-11 23:32 DEBUG  TaskList: ## Running Backup ISO...
08-11 23:32 DEBUG  TaskList: ## Finished Backup ISO
08-11 23:32 DEBUG  TaskList: ## Running Remove bootloader entry...
08-11 23:32 DEBUG  WindowsBackend: Could not find bcd id
08-11 23:32 DEBUG  WindowsBackend: undo_bootini C:
08-11 23:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 59592.6015625 mb free ntfs)
08-11 23:32 DEBUG  WindowsBackend: undo_bootini D:
08-11 23:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 11934.9570313 mb free ntfs)
08-11 23:32 DEBUG  TaskList: ## Finished Remove bootloader entry
08-11 23:32 DEBUG  TaskList: ## Running Remove target dir...
08-11 23:32 DEBUG  CommonBackend: Deleting C:\ubuntu
08-11 23:32 DEBUG  TaskList: ## Finished Remove target dir
08-11 23:32 DEBUG  TaskList: ## Running Remove registry key...
08-11 23:32 DEBUG  TaskList: ## Finished Remove registry key
08-11 23:32 DEBUG  TaskList: # Finished tasklist
08-11 23:32 INFO   root: Almost finished uninstalling
08-11 23:32 INFO   root: Finished uninstallation
08-11 23:32 DEBUG  CommonBackend: Fetching basic info...
08-11 23:32 DEBUG  CommonBackend: original_exe=E:\wubi.exe
08-11 23:32 DEBUG  CommonBackend: platform=win32
08-11 23:32 DEBUG  CommonBackend: osname=nt
08-11 23:32 DEBUG  WindowsBackend: arch=amd64
08-11 23:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\data\isolist.ini
08-11 23:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-11 23:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-11 23:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-11 23:32 DEBUG  WindowsBackend: Fetching host info...
08-11 23:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-11 23:32 DEBUG  WindowsBackend: windows version=vista
08-11 23:32 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-11 23:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-11 23:32 DEBUG  WindowsBackend: windows_build=6002
08-11 23:32 DEBUG  WindowsBackend: gmt=-6
08-11 23:32 DEBUG  WindowsBackend: country=US
08-11 23:32 DEBUG  WindowsBackend: timezone=America/Chicago
08-11 23:32 DEBUG  WindowsBackend: windows_username=Jace
08-11 23:32 DEBUG  WindowsBackend: user_full_name=Jace
08-11 23:32 DEBUG  WindowsBackend: user_directory=C:\Users\Jace
08-11 23:32 DEBUG  WindowsBackend: windows_language_code=1033
08-11 23:32 DEBUG  WindowsBackend: windows_language=English
08-11 23:32 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-11 23:32 DEBUG  WindowsBackend: bootloader=vista
08-11 23:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59592.5078125 mb free ntfs)
08-11 23:32 DEBUG  WindowsBackend: drive=Drive(C: hd 59592.5078125 mb free ntfs)
08-11 23:32 DEBUG  WindowsBackend: drive=Drive(D: hd 11934.9570313 mb free ntfs)
08-11 23:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
08-11 23:32 DEBUG  WindowsBackend: uninstaller_path=None
08-11 23:32 DEBUG  WindowsBackend: previous_target_dir=None
08-11 23:32 DEBUG  WindowsBackend: previous_distro_name=None
08-11 23:32 DEBUG  WindowsBackend: keyboard_id=67699721
08-11 23:32 DEBUG  WindowsBackend: keyboard_layout=us
08-11 23:32 DEBUG  WindowsBackend: keyboard_variant=
08-11 23:32 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-11 23:32 DEBUG  CommonBackend: Searching ISOs on USB devices
08-11 23:32 DEBUG  CommonBackend: Searching for local CDs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Ubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Kubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-11 23:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-11 23:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-11 23:32 INFO   Distro: Found a valid CD for Ubuntu: E:\
08-11 23:32 INFO   root: Running the installer...
08-11 23:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\translations, languages=['en_US', 'en']
08-11 23:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\translations, languages=['en_US', 'en']
08-11 23:32 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jace
08-11 23:32 INFO   root: Received settings
08-11 23:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\translations, languages=['en_US', 'en']
08-11 23:32 DEBUG  TaskList: # Running tasklist...
08-11 23:32 DEBUG  TaskList: ## Running select_target_dir...
08-11 23:32 INFO   WindowsBackend: Installing into C:\ubuntu
08-11 23:32 DEBUG  TaskList: ## Finished select_target_dir
08-11 23:32 DEBUG  TaskList: ## Running create_dir_structure...
08-11 23:32 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-11 23:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-11 23:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-11 23:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-11 23:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-11 23:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-11 23:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-11 23:33 DEBUG  TaskList: ## Finished create_dir_structure
08-11 23:33 DEBUG  TaskList: ## Running uncompress_target_dir...
08-11 23:33 DEBUG  TaskList: ## Finished uncompress_target_dir
08-11 23:33 DEBUG  TaskList: ## Running create_uninstaller...
08-11 23:33 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-11 23:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-11 23:33 DEBUG  TaskList: ## Finished create_uninstaller
08-11 23:33 DEBUG  TaskList: ## Running copy_installation_files...
08-11 23:33 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-11 23:33 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\winboot -> C:\ubuntu\winboot
08-11 23:33 DEBUG  WindowsBackend: Copying C:\Users\Jace\AppData\Local\Temp\pyl7628.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-11 23:33 DEBUG  TaskList: ## Finished copy_installation_files
08-11 23:33 DEBUG  TaskList: ## Running get_iso...
08-11 23:33 DEBUG  TaskList: New task copy_file
08-11 23:33 DEBUG  TaskList: ### Running copy_file...
08-11 23:37 DEBUG  TaskList: ### Finished copy_file
08-11 23:37 DEBUG  TaskList: New task check_iso
08-11 23:37 DEBUG  TaskList: ### Running check_iso...
08-11 23:37 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
08-11 23:37 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
08-11 23:37 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
08-11 23:37 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
08-11 23:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-11 23:37 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
08-11 23:37 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
08-11 23:37 DEBUG  TaskList: New task get_metalink
08-11 23:37 DEBUG  TaskList: #### Running get_metalink...
08-11 23:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > C:\ubuntu\install
08-11 23:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
08-11 23:37 DEBUG  downloader: download finished (read 7420 bytes)
08-11 23:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > C:\ubuntu\install
08-11 23:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
08-11 23:37 DEBUG  downloader: download finished (read 639 bytes)
08-11 23:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
08-11 23:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
08-11 23:37 DEBUG  downloader: download finished (read 189 bytes)
08-11 23:37 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
08-11 23:37 INFO   saplog: Checking block bindings..
08-11 23:37 INFO   saplog: Key verified successfully.
08-11 23:37 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink
08-11 23:37 DEBUG  TaskList: #### Finished get_metalink
08-11 23:37 DEBUG  TaskList: New task get_file_md5
08-11 23:37 DEBUG  TaskList: #### Running get_file_md5...
08-11 23:37 DEBUG  TaskList: #### Finished get_file_md5
08-11 23:37 DEBUG  TaskList: ### Finished check_iso
08-11 23:37 DEBUG  TaskList: ## Finished get_iso
08-11 23:37 DEBUG  TaskList: ## Running extract_kernel...
08-11 23:37 DEBUG  CommonBackend: Copying files from CD E:\
08-11 23:38 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 509, in extract_kernel
  File "\lib\shutil.py", line 72, in copy
  File "\lib\shutil.py", line 40, in copyfile
  File "\lib\shutil.py", line 22, in copyfileobj
IOError: [Errno 13] Permission denied
08-11 23:38 DEBUG  TaskList: # Cancelling tasklist
08-11 23:38 DEBUG  TaskList: # Finished tasklist
08-11 23:38 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 509, in extract_kernel
  File "\lib\shutil.py", line 72, in copy
  File "\lib\shutil.py", line 40, in copyfile
  File "\lib\shutil.py", line 22, in copyfileobj
IOError: [Errno 13] Permission denied


---

### Post by bcbc on 2010-08-12
> **Sniper Man said:**
> Hey guys I was trying to install Ubuntu to run side by side with windows but I got an error and it said to check one of my log files I will post it under this.

Could be a bad burn on the CD. Try booting from the CD - press any key when you see the keyboard icon on the bottom - and then select check cd for defects. You can also 'Try without installing'. This is a good idea anyway before installing (if you haven't already).

You can also install wubi by copying the installation .iso and wubi.exe into the same folder, and running it from there. Make sure you run wubi.exe as Administrator (it looks like you're on Vista/Win7).


edit: you're getting > OSError: [Errno 13] Permission denied removing C:\ubuntu\install\installation.iso
Try deleting that manually first.

---

### Post by 3rdalbum on 2010-08-12
Don't use Wubi. It's only really for trying out Ubuntu before taking the plunge and doing a real installation. If something happens to Windows and it won't boot, then it also prevents Ubuntu from booting. You're also limited in space for Ubuntu.

Instead, defragment your hard disk and boot up Ubuntu from the CD, then run the installer. Tell it to resize your existing Windows partition; you won't lose any files (although I'd recommend a backup before any partitioning operations) and you'll have a real dual-boot system with no limitations.

You mentioned that "dual-booting makes the computer slow" - this is not the case. Only one operating system is actually running at a time. A dual-boot Ubuntu system is exactly as fast as an identical single-boot Ubuntu system.

---

### Post by bcbc on 2010-08-12
If you decide to install direct to partition, do not use the ubuntu installer to split your windows partition (since you're running Vista/7). Windows vista/7 has a disk manager that can shrink the volume - otherwise you risk damaging windows.

---

