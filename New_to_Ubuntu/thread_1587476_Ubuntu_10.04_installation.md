---
title: "Ubuntu 10.04 installation"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by taiChip on 2010-10-03
First time i´m installing Ubuntu,
i started in Win XP from a cd, chose "Demo and full installation".
After rebooting and a few minutes of installation it freezes with a message:

Process:259: G-Lib Warning **: getpwuid_r(): failed due to unknown user id(0)

Any ideas how to fix it?

Thanks,
Peter

---

### Post by Hippytaff on 2010-10-03
is it a wubi install?

---

### Post by taiChip on 2010-10-03
Yes it is.
ubuntu-10.04.1-desktop-i386.iso

---

### Post by Hippytaff on 2010-10-03
have you tried a livecd/usb?

---

### Post by tacobeans1234 on 2010-10-03
> **Hippytaff said:**
> have you tried a livecd/usb?

Stole the words right from my mouth. 
I hardly ever use wubi when I'm installing ubuntu for someone. 
Livecd/Usb is the way to go.

---

### Post by Hippytaff on 2010-10-03
just to check that everything is ok compatability wise and then do an install :-)

---

### Post by taiChip on 2010-10-03
sorry, it´s the livecd version i´m using.

---

### Post by Hippytaff on 2010-10-03
did you download and burn the iso yourself?

if so check the md5sum to see if the file got corrupted en-route. if it's ok burn in again at the slowest speed

---

### Post by taiChip on 2010-10-03
yes i downloaded the .iso earlier today 
and burned it with Nero.
 i´ll try to burn a new copy now.

---

### Post by Hippytaff on 2010-10-03
check the md5sum first - rather than waste discs if it's corrupt

CD to the directory where it is and

```

md5sum ubuntu-8.10-desktop-i386.iso

```check the output against the correct version-
0b0e0d36050d9980ec995262eb9f2e6b *ubuntu-10.04-netbook-armel+dove.img 
9e0d6ac7b69bb7912d49369a6807e39d *ubuntu-10.04-netbook-armel+imx51.img 
712277c7868ab374c4d3c73cff1d95cb *ubuntu-10.04-netbook-i386.iso 
f3da7da6931e3160738b3067d79e346a *ubuntu-10.04.1-alternate-amd64.iso 
1c77abb717e7c1ad28611fd81510c758 *ubuntu-10.04.1-alternate-i386.iso 
b4faa186c2419dc26e522e5f82e268a1 *ubuntu-10.04.1-desktop-amd64.iso 
9a95ed6f6ec38fb58c446dba1add6a08 *ubuntu-10.04.1-desktop-i386.iso 
142aaaa77e7da94ae62d7ee2f39d8b3b *ubuntu-10.04.1-server-amd64.iso 
01f72c846845e4e19aec8a45912e5dda *ubuntu-10.04.1-server-i386.iso 
5c976b1d655b10df3b10811e77b09a25 *wubi.exe

---

### Post by taiChip on 2010-10-03
ok, but i´m using a rw-cd so it doesn´t matter

---

### Post by Hippytaff on 2010-10-03
ok....maybe worth checking the iso on the disc to see if that is corrupt

```

md5sum /dev/cdrom


```

---

### Post by taiChip on 2010-10-03
all the files seem to be ok
tried to install again but with the same result
now i´m reading following thread

[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

and a bug-report at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279)

they mention that this could be an issue with some cd/dvd-drives?

---

### Post by taiChip on 2010-10-04
i give up,
now downloading ubuntu 9.10
hope it works better :-\
thanks guys!

---

### Post by Hippytaff on 2010-10-04
10.10 will be out soon :-D (on the 10th)

---

### Post by mastablasta on 2010-10-04
Have you tried alternate installer?
 
Here is some info on this message, but i guess you already saw this: 
[https://answers.launchpad.net/ubuntu/+question/111396](https://answers.launchpad.net/ubuntu/+question/111396)
 
you didn't provide much information on your system and such... have a look at this thread for guidance:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by taiChip on 2010-10-04
the 10th of october it is
(but i´ll try to install the Karmic Koala version tonight)

thx for the manuals link!

my sys is btw:

Computer	
Operating System		Microsoft Windows XP Professional
OS Service Pack		Service Pack 2
DirectX			4.09.00.0904 (DirectX 9.0c)
Computer Name		-----
User Name		user28
	
Motherboard	
CPU Type		Intel Pentium 4, 2800 MHz (14 x 200)
Motherboard Name	Hewlett-Packard HP d530 SFF(DF377T)
Motherboard Chipset	Intel Springdale-G i865G
System Memory		503 MB  (PC3200 DDR SDRAM)
BIOS Type		Compaq (08/10/04)
Communication Port	Kommunikationsport (COM1)
Communication Port	ECP-skrivarport (LPT1)
	
Display	
Video Adapter		Intel(R) 82865G Graphics Controller  (96 MB)
3D Accelerator		Intel Extreme Graphics 2
	
Multimedia	
Audio Adapter		Intel 82801EB ICH5 - AC'97 Audio Controller [A-2/A-3]
	
Storage	
IDE Controller		Intel(R) 82801EB Ultra ATA Storage Controllers
IDE Controller		Intel(R) 82801EB Ultra ATA Storage Controllers
Floppy Drive		Diskettenhet
Disk Drive		IC25N030ATCS04-0  (30 GB, 4200 RPM, Ultra-ATA/100)
Optical Drive		HL-DT-ST DVD-ROM GDR8162B  (16x/48x DVD-ROM)
SMART Hard Disks Status	OK
	
Partitions	
C: (FAT32)		19584 MB (7594 MB free)
E: (FAT32)		9012 MB (9011 MB free)
Total Size		27.9 GB (16.2 GB free)
	
Input	
Keyboard			Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Mouse			PS/2-kompatibel mus
	
Network	
Network Adapter		Broadcom NetXtreme Gigabit Ethernet for hp  (192.168.1.55)

---

### Post by amjjawad on 2010-10-04
Check my signature, there's a useful guide that might help you.

My advice to you from my own experience with installation of Ubuntu, try to install Ubuntu on a separate partition. Of course, you need to try Ubuntu before installing it.

I guess you can find all what you need in that guide. If not, let us know!

---

### Post by mastablasta on 2010-10-05
> **taiChip said:**
> 
Display    
Video Adapter        Intel(R) 82865G Graphics Controller (96 MB)
3D Accelerator        Intel Extreme Graphics 2

 
This could be your problem. Intel is not known for great Linux support especially with some of their older cards. Try to search arround for any solutions (use google as it has a better search engine than the forums.
 
Anyway i would suggest (1) alternate install and (2) to do a propper dual boot (create & use separate partition to install)

---

### Post by taiChip on 2010-10-08
i´m doing a dual boot installation on a separate partition and
the 9.10 verson froze just like the 10.04 but after reading
the help-menu (F1) i saw them mention IBM several times
and my hdd being a IBM Travelstar 40GN i chose in the F6 menu
acpi=off and everything worked just fine :-D

Thanks all!

---

### Post by Hippytaff on 2010-10-08
Excellent news - remember to mark the thread as solved in the thread tools at the top of the page :-D

---

