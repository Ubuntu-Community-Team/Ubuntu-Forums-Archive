---
title: "cant create liveUSB on cruzer 8gb"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-23
i bought sandisk cruzer 8gig last week hoping to make it my ultimate linux companion, with multiple ubuntus and all. but alas!.. it just wont work!. i tried with xubuntu, ubuntu, linux mint and even windows vista, it boots but ends with an error. but when i use my cheap coby 8gb it works just fine. is it something with cruzers that make them unusable as a linux live usb?

---

### Post by ST3ALTHPSYCH0 on 2010-08-23
ItWorksForMe&#8482;
In all seriousness, I have 2 8Gb cruzers and 1 2 Gb Data traveler, all live environments. I just used Unetbootin. Wish I could give you more assistance than that.

---

### Post by wilee-nilee on 2010-08-23
I had a sandisk 4 gig thumb and it worked okay after reformatting it with gparted. It had a program on it called U3 that can be removed. This is the problem program on the USB.
[http://www.mydigitallife.info/2006/09/11/disable-remove-and-uninstall-u3-launchpad/](http://www.mydigitallife.info/2006/09/11/disable-remove-and-uninstall-u3-launchpad/)

---

### Post by fremantle on 2010-08-23
i know about u3...so annoyin!!

but i formatted it to ntfs from xubuntu, and then tried to install my vista iso. it booted successfully and took me to the installation setup. but then i got the error that i need to install drivers for my disk drive. so i had to quit. then again i formatted it to fat32 from my windows dextop and flashed it with unetbootin, but it was unable to boot successfully in my netbook.

---

### Post by oldfred on 2010-08-23
If it is more than 1GB flash, may I suggest using grub2 to loopmount the iso directly. You then can put multiple isos on one flash drive.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

Auto version:
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)

---

