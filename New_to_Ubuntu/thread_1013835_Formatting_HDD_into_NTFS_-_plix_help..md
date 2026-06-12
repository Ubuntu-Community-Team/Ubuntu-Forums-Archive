---
title: "Formatting HDD into NTFS - plix help."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by CasperBjoern on 2008-12-17
Hi everybody.

First post in ubuntu forums, but far from first hassle with working my way around this new OS.. ;)

Ive got Kubuntu 8.10 installed for a while now, as the only OS, and its giving me a headache that the only OS i have on my computer is one i suck at using. So far ofc. 

I want to install windows, and then make a partition for Kubuntu afterwards. i'd like the capability of playing my games, and doing my usual stuff, while i can spend time learning Linux, without it being the only thing i can use my computer for, u know?

I have no files i want to save on my current HDD, so i pretty much just wanna do a clean format, and change the file format to NTFS, so i can install my Vista ultimate, and then work my way from there. But i don't know how.

Is there a command to do, cuss i cant find anything GUI-wise, that has anything to do with formatting HDD's?

peace

CasperBjoern

---

### Post by Michael.Godawski on 2008-12-17
> I have no files i want to save on my current HDD, so i pretty much just wanna do a clean format, and change the file format to NTFS, so i can install my Vista ultimate, and then work my way from there. But i don't know how.

Is there a command to do, cuss i cant find anything GUI-wise, that has anything to do with formatting HDD's?

If you don't have any files and want to do a fresh install on a blank drive than just pop in the vista cd (dvd). During the installation process Vista will partition the drive to the needed type.

For the next steps see this dual boot guide:

[LIST]
[*][http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[/LIST]

---

### Post by bumanie on 2008-12-17
Why not use the live cd to format the hard drive to ntfs with gparted? Boot live cd > sudo apt-get install gpartedGo to System --> Administration --> Partition editor. Click on presentpartition and choose to format it to ntfs. Alternatively use command in terminal from live cd > sudo mkfs -t ntfs /dev/sda (substitute /dev/sda for your hard drive name if it's different).

---

### Post by CasperBjoern on 2008-12-17
Thx for ur quick reply! :)

Prbly shouldve said that i tried popping the vista cd, and that it was unable to install on my HDD.. My thought was, that the HDD spoke in something else than NTFS, since i was unable to install. (doesnt linux use sumtin else? This used to be a gentoo computer, but i wiped that off, with Kubuntu) So i concluded that it was necessary to format and make sure that NTFS indeed was the fileformat. 

Thx for the link, itl surely come in handy!

---

### Post by pshootr on 2008-12-17
Or you could download a iso of Gparted, then burn it to cd It will be bootable). Then boot from the Gparted cd and format your whole drive NTFS. Then install windows. Then boot from a live-cd and install ubuntu. The live cd will allow you to setup dual boot.

---

### Post by CasperBjoern on 2008-12-17
> **pshootr said:**
> Or you could download a iso of Gparted, then burn it to cd It will be bootable). Then boot from the Gparted cd and format your whole drive NTFS. Then install windows. Then boot from a live-cd and install ubuntu. The live cd will allow you to setup dual boot.

That is the sort of solution im able to understand! nice and simple. D'you have a link for that .iso? 

Is it realy just booting from the cd with gparted.iso, and then doing what ever with that program, to format into NTFS, then rebooting, now with the vista cd. And bam bam... There i go?

Sounds like pie :)

---

### Post by Michael.Godawski on 2008-12-17
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
bam

---

### Post by theozzlives on 2008-12-17
you could have Vista in a [VirtualBox]("http://www.virtualbox.com/")

---

### Post by CasperBjoern on 2008-12-17
Thx alot! Ill try this. Sounds doable. Ill prbly return, when i mess something up. haha.

Thanks alot for your fast replies.

Peace

---

### Post by pshootr on 2008-12-17
> **CasperBjoern said:**
> That is the sort of solution im able to understand! nice and simple. D'you have a link for that .iso? 

Is it realy just booting from the cd with gparted.iso, and then doing what ever with that program, to format into NTFS, then rebooting, now with the vista cd. And bam bam... There i go?

Sounds like pie :)

yeah pretty much. Just remember to set your bios so that you can boot from cd and you should be set.

---

### Post by oilchangeguy on 2008-12-17
> **CasperBjoern said:**
> Thx for ur quick reply! :)

Prbly shouldve said that i tried popping the vista cd, and that it was unable to install on my HDD.. My thought was, that the HDD spoke in something else than NTFS, since i was unable to install. (doesnt linux use sumtin else? This used to be a gentoo computer, but i wiped that off, with Kubuntu) So i concluded that it was necessary to format and make sure that NTFS indeed was the fileformat. 

Thx for the link, itl surely come in handy!

the format of the hard drive does not matter. what do you think would happen when you buy a new hard drive with no format? most likely your computer is not set to boot from the cd drive first. i've seen computers with no floppy drive still set to boot from the floppy first in the bios.

---

