---
title: "unbootable ubuntu usb"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by Boneymin on 2011-05-22
I am running Win7 and want to dual boot Ubuntu 11.04.

Using the "Universal USB installer" i copied 11.04 onto a 4GB stick.

I got it to boot into the install screen then, and then I got called away from the computer. 

I came back and the computer had restarted into Windows. So i rebooted but this time it said the media was not able to be booted from. 

I returned to Windows.

When I opened the USB key up, there is only one 1MB partition, when I try to reformat and remove the partitions it never works and only notices it as 1MB.

Ideas?

---

### Post by Linux_junkie on 2011-05-22
Sounds to me like your trying to view the usb memory stick in Windows.  Windows does not recognise Linux partitions.  Is why you cannot format the usb through Windows..  Also when trying to boot from memory stick you may have to press the F12 key when you first switch on computer to select the usb device to boot from.

Hope this helps.

---

### Post by Boneymin on 2011-05-22
Hm, So i have a VM with ubuntu 11.04 installed on it. Even in this I cannot see any extra partitions.

When booting the computer (not the above VM) I select through the BIOS to have the USB in first boot priority, I also select USB-HDD as the first boot device and then when I save and restart I use f12 to select USB-HDD to boot from.

---

### Post by sanderj on 2011-05-22
> **Boneymin said:**
> Hm, So i have a VM with ubuntu 11.04 installed on it. Even in this I cannot see any extra partitions.

When booting the computer (not the above VM) I select through the BIOS to have the USB in first boot priority, I also select USB-HDD as the first boot device and then when I save and restart I use f12 to select USB-HDD to boot from.

First things first: under Windows, plug in the USB stick, and look at it's contents. It should contain:


```

autorun.inf  
boot  
casper  
casper-rw  
dists  
install  
ldlinux.sys  
md5sum.txt  
pics  
pool  
preseed  
README.diskdefines  
syslinux  
usb-creator.exe  
wubi.exe
```


If not, it's not a bootable Ubuntu USB stick, and you can't boot off it. Sorry.

The most safe way to create a bootable Ubuntu USB stick:
download Ubuntu .ISO file, burn it to a CD, boot the CD, then start usb-creator-gtk to let write Ubuntu itself to a USB-stick. This will take ten minutes. Ubuntu will then offer to reboot from the USB-stick.

HTH

---

### Post by lmn. on 2011-05-22
errm.. reformat to ntfs and then back again to fat32?
also try unetbootin

---

### Post by Boneymin on 2011-05-22
No I don't have those files; I have what should be a 4GB stick that is showing 0.98MB. Hm, well it worked the first time, so something must have screwed it.

As far as formatting to NTFS, it is unable to complete the operation. 

That "Unetbootin" is the same kind of utility as the universal usb installer that the ubuntu.com site says to use? When I try the universal usb installer it tells me "not enough space" (obviously 1MB isnt enough).

So i cant even salvage my usb

---

### Post by sanderj on 2011-05-22
> **Boneymin said:**
> No I don't have those files; I have what should be a 4GB stick that is showing 0.98MB. Hm, well it worked the first time, so something must have screwed it.

As far as formatting to NTFS, it is unable to complete the operation. 

That "Unetbootin" is the same kind of utility as the universal usb installer that the ubuntu.com site says to use? When I try the universal usb installer it tells me "not enough space" (obviously 1MB isnt enough).

So i cant even salvage my usb

Just follow my advice, and everything will go automagically with a few mouseclicks.

---

### Post by Boneymin on 2011-05-22
I will follow your method.

As for my diminutive usb stick, any ideas on why it's so small and how I can recover it's rated capacity?

---

### Post by beew on 2011-05-22
> **Linux_junkie said:**
> Sounds to me like your trying to view the usb memory stick in Windows.  Windows does not recognise Linux partitions.  Is why you cannot format the usb through Windows..  Also when trying to boot from memory stick you may have to press the F12 key when you first switch on computer to select the usb device to boot from.

Hope this helps.

It is a live usb, not a Linux install, it should be formatted to FAT32. Windows should be able to see it.

---

### Post by beew on 2011-05-22
> **Boneymin said:**
> No I don't have those files; I have what should be a 4GB stick that is showing 0.98MB. Hm, well it worked the first time, so something must have screwed it.

As far as formatting to NTFS, it is unable to complete the operation. 

That "Unetbootin" is the same kind of utility as the universal usb installer that the ubuntu.com site says to use? When I try the universal usb installer it tells me "not enough space" (obviously 1MB isnt enough).

So i cant even salvage my usb

I don't know about Win7 but XP and Windows tools like Partition Magic are not able to partition usb drive, there is a hp tool you can download to do this.[http://en.kioskea.net/download/download-127-hp-usb-disk-storage-format-tool](http://en.kioskea.net/download/download-127-hp-usb-disk-storage-format-tool)

Unetbootin doesn't support persistence whereas the Universal Installer does, though if you are only using the usb for install that shouldn't matter.

---

### Post by Boneymin on 2011-05-22
After downloading that tool I tried again but it still doesn't recognise anything other than the 1MB partition on there.

When I run HPUSBF in the command line it shows me two lines: one with the ID of F: (what I can see in my computer) and another with the ID of HD1 - both have the description "Imation ImationFlashDriv PMAP". I though the "HD1" could be the hidden partition but when I attempted to format it threw an error saying 1MB is too small to partition.

---

### Post by beew on 2011-05-22
Well here is some bad news, apparently windows (XP) just can't do it.

[http://ubuntuforums.org/showthread.php?t=617769&page=2](http://ubuntuforums.org/showthread.php?t=617769&page=2)

BUT, in the last post there is a link. That link has a post that claims it can be done but the method may mess up Windows, which then links to a tutorial and here is the tutorial
[http://www.msfn.org/board/index.php?act=ST&f=82&t=69211&st=0#entry474505](http://www.msfn.org/board/index.php?act=ST&f=82&t=69211&st=0#entry474505) Sounds kind of complicated though.

Keep in mind these are all on XP. You may try to ask around on Windows forums.

EDITED: If you have another usb you can of course make another live usb, boot into it, attach the bad usb and use gparted in it to fix it (or just right click and "format"), but make sure the same thing doesn't happen again. If you don't have another usb you can try a live CD.

---

### Post by Boneymin on 2011-05-22
If it's a case of the partition being ext2/3 surely it would have shown up when I tried the usb in my Ubuntu VM using gparted?

---

### Post by beew on 2011-05-22
> **Boneymin said:**
> If it's a case of the partition being ext2/3 surely it would have shown up when I tried the usb in my Ubuntu VM using gparted?

Don't know what happened, maybe the usb drive just died. gparted can see anything, including Windows file systems like NTFS, it is just that Windows can't see Linux.

---

### Post by Boneymin on 2011-05-22
All right, I guess I'll head back to the store with the reciept and try that. Thanks for all your help, I'll use the livecd instead. 
Ubuntu FTW

---

