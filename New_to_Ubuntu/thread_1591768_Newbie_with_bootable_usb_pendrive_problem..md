---
title: "Newbie with bootable usb pendrive problem."
date: 2010-10-09
forum: New to Ubuntu
---

### Post by Nigelinoz on 2010-10-09
[I]For problems in general regarding USB boot on the [dc7700 ]("http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12775075&viewfull=1#post12775075")here's some new advice.

Mörgæs 2013-09-02
[/I]= = = = =


Hi everyone,
  I&#8217;m a newbie here and I have a problem that I hope someone may be able to help me fix,I&#8217;ll give as much detail as I can.
  Firstly I should say that I have recently become a convert to Linux after many years
  Using Windows,a friend installed Linux Mint on his machine and convinced me to give it a try ,I played with his machine for a few days and was quickly hooked and
  Decided to install it on a PC which I bought from an online site a few weeks ago.
  It&#8217;s a HP dc7700 sff with 1024 meg of ram and a 160gb SATA HDD,it has integrated
  Graphics.
  Ok,so I downloaded the latest version of Mint from the net and created a bootable usb 
  Pendrive and that&#8217;s when the problem started,I had a completely blank hard drive and 
  Adjusted the BIOS to boot from the usb device,however when I tried to boot I got a 
  Flashing cursor with a blank screen,I tried to boot using compatability mode and that
  Worked except that I get the following error.
  &#8220;Ubuntu is running in low-graphics mode
The following error was encountered. You may ned to update your configuration to solve this.

(EE) VESA: Kernel Modesetting driver in use, refusing to load
(EE) No devices detected
   
  I&#8217;ve done a search of various sites and  found this forum and this thread seems to relate to the issue I am having-http://ubuntuforums.org/showthread.php?t=1497063,
apparently there may be an issue with a 
  xorg.conf file but my problem is I know absolutely zilch about Linux so how
  do I find this file in order to rename it?
  I really like the look of Linux Mint ,it's easy to use,and best of all it's free! I  would love to convert my friends to this great
  OS but I need to fix this problem a.s.a.p.
  I would really appreciate help.:)
  Cheers
  Nigelinoz

---

### Post by kroq-gar78 on 2010-10-09
what's wrong with a bootable cd?

---

### Post by MattBD on 2010-10-09
What method did you use to create the bootable USB? Was it UNetbootin, or USB creator, or something else?

---

### Post by C.S.Cameron on 2010-10-09
I understand that HP computers are Linux friendly.
Suggest that you first check the MD5SUM of your downloaded iso.
There are a few different methods to make a bootable "disk image" Ubuntu flash drive.
UNetbootin works well on a Windows machine.

---

### Post by Nigelinoz on 2010-10-09
> **MattBD said:**
> What method did you use to create the bootable USB? Was it UNetbootin, or USB creator, or something else?
Hi Matt,
I saved the ISO to my downloads folder on my Windows machine and used Universal USB Installer Version 1.8.0.2 to create the bootable installation on my 2GB USB pendrive.
Cheers
Nigelinoz

---

### Post by 5hadow5un on 2010-10-09
I used my 2GB GPX mp3 player and used the Universal USB installer and the .iso (saved in my WinXP Prof partition) earlier this morning and for the most part went smoothly.  The only thing that was odd was that I had to wait a moment for my laptop (Dell Latitude D600: Pentium M 1.5GHz, 1GB DDR, 60GBHD) to recognize the mp3 player as a "normal" usb storage device.  It even partitioned my HD almost in half, formatted the new partition as ext4, then installed Ubuntu 10.04 on it...piece of cake.:P

---

### Post by Zero++ on 2010-10-09
I would try making a bootable CD if possible to test the ISO. Next try an different usb installer. I use unetbootin and have had very good success with it. If that doesn't work wait till tomorrow and get 10.10 and see if the new version helps.

---

### Post by JustinR on 2010-10-09
Hi,

When the computer starts to load the flash drive, when the screen hits the keyboard and accessibility icon with the purple background press 'Enter'. It should ask you to select your language, then press 'F6' and try the option 'NoModeSet', then press 'ESC' and select whatever you want to do, eg. Try Ubuntu first or Install.

---

### Post by Nigelinoz on 2010-10-10
Thanks to everyone who has replied so far,I will try some of the suggestions and report back.
thanks again,this sure is a great resource for information about Linux.:)
Cheers
N'oz

---

### Post by Nigelinoz on 2010-10-13
Well guys I have solved this problem,I decided to try a different installer so I formatted the pendrive,uninstalled the Universal USB installer and instead downloaded unetbootin and started the process again,that fixed the problem,Linux Mint is now installed happily on the PC and I'm having great fun getting to know this great OS.
Thanks to everyone who replied to my question,your help has been much appreciated and I will be a regular visitor to the forums.:)
Cheers
N'oz

---

