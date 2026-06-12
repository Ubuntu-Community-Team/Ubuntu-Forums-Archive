---
title: "&quot;Dual&quot; boot?"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by timclev on 2010-06-24
I have Windows 7 installed on the main drive (64 bit) on my laptop and would like to install Ubuntu 10.04 to an 285 Gb external drive. Any suggestions? I'm mostly concerned with the Grub process.

---

### Post by oldfred on 2010-06-24
You just want to make sure you install grub2 to the external also. Then you can set BIOS to boot external first and if it is there grub will give you a choice of what to boot. Without the external the windows bootloader in sda will still boot you into windows.

On the last partition screen you must use the advanced button to choose which drive to install grub to, otherwise it will install to sda.
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by S.R on 2010-06-24
I have this exact setup. If you would like to leave your internal hard drive alone. You can either use all of the external HDD for Ubuntu or in my situation I made 2 partitions on my external. One NTFS and EXT4 so I could back up files from Windows. 

Then just do a standard install of Ubuntu on the external. Go to the BIOS and set the boot order to look for a USB for your external and then look for your internal. This away if your external is not plugged in it will boot straight to your Windows and if your external is plugged in it will Boot to the GRUB menu and you can still choose between loading Ubuntu or Windows.

It has worked out great so far.

---

### Post by Nightstrike2009 on 2010-06-24
hello timclev:

I recently answered a similar post [http://ubuntuforums.org/showthread.php?t=1517060]("http://ubuntuforums.org/showthread.php?t=1517060") check that out and ignore the drive installation & jumper set up parts and you should be fine :-)

Or just read this below it's quicker ;-)

> **By Nightstrike2009:**
I am a Dual booter too, you need to install Windows on the 1st hard disk first then install Ubuntu on the 2nd hard disk afterwards (Ubuntu will format this itself), other wise you will not be able to boot Windows. 

I use two internal drives on SATA (Windows 7) and one IDE (Ubuntu 10.04) but should be the same for an external drive, I guess (as long has you have it plugged in at boot up, obviously) :-)

---

### Post by eriktheblu on 2010-06-24
It's pretty easy to mess up the master boot record (MBR) of your internal disk with any OS install. If possible, disconnect your internal drive during the install to avoid problems.

---

### Post by Ebere on 2010-06-24
> **timclev said:**
> I have Windows 7 installed on the main drive (64 bit) on my laptop and would like to install Ubuntu 10.04 to an 285 Gb external drive. Any suggestions? I'm mostly concerned with the Grub process.

I have two internal drives.

I don't worry about grub.

If I want to boot to Ubuntu, I set bios to boot to that drive. If I want to boot to Linux Mint, I set the bios to boot to that drive.

Once you have done it a couple times, it becomes old hat. And only adds maybe ten seconds to the boot process, if you decide to boot to the other drive.

BTW: When I installed Ubuntu to one HD, I had the other disconnected.

Then when I installed Mint to the other, I had the first drive disconnected.

Now both are connected, and if I decide to switch, it goes as above.

---

### Post by cuberts on 2010-06-24
> **timclev said:**
> I have Windows 7 installed on the main drive (64 bit) on my laptop and would like to install Ubuntu 10.04 to an 285 Gb external drive. Any suggestions? I'm mostly concerned with the Grub process.The easiest way to do it would be to install it from a live CD, so you can just boot from that and follow the installation steps. However if you do not have that then you will have to download it from the internet, but in this step you will have to have the knowledge of compiling an ISO image.

---

