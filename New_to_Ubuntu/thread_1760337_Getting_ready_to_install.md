---
title: "Getting ready to install"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by larrypg on 2011-05-16
Hello all,

I have finally decided to install Xubuntu 11.04.  Windows XP is on drive sda and Xubuntu will be on sdb.

I have an old bios and can only boot the C: (sda) drive.  I do not have an option of booting either.  This means ( I am guessing ) that Grub2 will have to be written to the MBR of sda.  So obviously this will overwrite my Windows XP boot record.  

I only have a Dell Reinstallation CD and it does not look like it has a command line option (although I could be wrong) so /fixboot or /fixmbr might not be available.  So if any problems arise it will have to be fixed via Grub unless someone can tell me a way to fix any potential problem via some sort of recovery disk (not a Vista or Windows 7 recovery disk).  

Probably a dumb question but should Grub2 be written to both the / partition of sdb and the MBR of sda or just the MBR of sda.  I am not sure you can even do both at the same time.  

I will be partitioning sdb with three primary partitions which will be /, /home, and swap.  There will not be a /boot partition unless it is recommend that I have one because of my inability to boot from that drive.  Should I make / and /home ext4 before I install or wait for the installer to do it?  

I will be awaiting any responses before I make the final plunge.

---

### Post by mikewhatever on 2011-05-17
There are various ways to restore or fix the MBR: [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)
I'd suggest to make a backup of the current MBR following the steps on the above page, and restoring when needed.
As the fallback solutions for WindowsXP, there are MbrFix.exe and SuperGrub.

I'd also recommend the [MBR Section]("http://members.iinet.net.au/~herman546/p6.html") for understanding what MBR and bootloader are.

---

### Post by Bucky Ball on 2011-05-17
I'd suggest installing 10.04 LTS if you actually want to do some work unless you are one of the lucky ones that has 11.04 working perfectly out of the box. ;)

If you manually partition (rather than allow Ubuntu to install itself), the install should pick up your Windows install and organise the grub accordingly (without killing win). Good luck. ;)

As mentioned by Mikewhatever (hi Mike), Herman and supergrub will help if you get into trouble. Herman's dual-boot site is legendary!

---

### Post by Allavona on 2011-05-17
This may seem silly, but have you plugged in sdb and then booted into bios? Some bios, older ones that is, treat removable drives as an internal HDD, and will allow a boot from that by simply changing boot devices in your bios. Now for the kicker...It only works once, it defaults after each reboot. So you have to go through the process again. This works on most Phoenix and Onyx boards. Not certain about ASUS or others.

---

### Post by NCLI on 2011-05-17
Can't you simply move the jumpers, making the new drive master, and the old drive slave? 

If they are sata drives, you should be able to simply switch the cables. That way, you don't risk ruining the mbr.

---

