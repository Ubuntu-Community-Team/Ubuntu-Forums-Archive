---
title: "Why won't ubuntu recognize my usb flash drive?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by iamleaf on 2009-04-17
I've got a transcend 4GB usb drive. But Ubuntu doesn't even recognize it. It shows up on 'Computer' but when I click properties, it doesn't read it at all. I can't even mount it because it shows me an error message.
I've tried running lsusb and this is what I got:

Bus 004 Device 005: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash 110 USB 2.0 Flash Drive (2GB)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  


Someone please help :(

---

### Post by llamabr on 2009-04-17
plug it in and post the last 10 or so lines of dmesg.

Has this device recently been plugged into a windows box?

---

### Post by mikechant on 2009-04-17
Is this a new drive or have you already used it?
If it's new you may need to format it.
You can use gparted (found under system-->admin-->partition editor, install with synaptic etc. if not present) to look at what partitions are on the device if any, and what filesystems they are formatted as.

---

### Post by tarps87 on 2009-04-17
Do you have any other usb devices plugged in. Can you post the output of
```
fdisk -l
```
(l = lower case L)

This will give you the last 10 lines of dmesg
```
tail dmesg
```

It is possible it one of those 'silly' usb drives (I can't remember the name), they have a special program that makes windows think it is a cd. This program tends to mess up mounting in GNU/Linux

---

### Post by anjilslaire on 2009-04-17
> **tarps87 said:**
> It is possible it one of those 'silly' usb drives (I can't remember the name), they have a special program that makes windows think it is a cd. This program tends to mess up mounting in GNU/Linux

Yes, I have a SanDisk cruzer micro like that. Even zeroing the thing wouldn't remove it. I had to download their removal app & run it from a windows system to get it to behave as a plain usb stick.

---

### Post by iamleaf on 2009-04-17
> **llamabr said:**
> plug it in and post the last 10 or so lines of dmesg.

Has this device recently been plugged into a windows box?
```

[19364.188554] scsi 4:0:0:0: Direct-Access     JetFlash TS4GJFV30        8.07 PQ: 0 ANSI: 2
[19364.201433] sd 4:0:0:0: [sdc] 8028158 512-byte hardware sectors (4110 MB)
[19364.202273] sd 4:0:0:0: [sdc] Write Protect is off
[19364.202280] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[19364.202283] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[19364.207611] sd 4:0:0:0: [sdc] 8028158 512-byte hardware sectors (4110 MB)
[19364.208218] sd 4:0:0:0: [sdc] Write Protect is off
[19364.208224] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[19364.208227] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[19364.208237]  sdc: sdc1
[19364.209259] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[19364.209327] sd 4:0:0:0: Attached scsi generic sg3 type 0
```

Yeah, I've plugged it into a laptop that has Windows Vista recently.

fdisk -l doesn't return anything.

No its not a silly device. :P

And I couldn't find partition manager? :(

---

### Post by tarps87 on 2009-04-17
> **iamleaf said:**
> ```

[19364.188554] scsi 4:0:0:0: Direct-Access     JetFlash TS4GJFV30        8.07 PQ: 0 ANSI: 2
[19364.201433] sd 4:0:0:0: [sdc] 8028158 512-byte hardware sectors (4110 MB)
[19364.202273] sd 4:0:0:0: [sdc] Write Protect is off
[19364.202280] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[19364.202283] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[19364.207611] sd 4:0:0:0: [sdc] 8028158 512-byte hardware sectors (4110 MB)
[19364.208218] sd 4:0:0:0: [sdc] Write Protect is off
[19364.208224] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[19364.208227] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[19364.208237]  sdc: sdc1
[19364.209259] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[19364.209327] sd 4:0:0:0: Attached scsi generic sg3 type 0
```

Yeah, I've plugged it into a laptop that has Windows Vista recently.

fdisk -l doesn't return anything.

No its not a silly device. :P

And I couldn't find partition manager? :(

That's the silly thing 'U3 Launchpad'

try
```
sudo fdisk -l
```
without sudo it should have just listed the removable drives.
You will probably need to install the partitioner, it is called gparted.

Did you just plug the usb stick in? It appears to have seen it.
Also how many usb devices have you got connected or to be more precise to you have a 2GB stick plugged in?

Oh and it must be silly other wise Ubuntu would see it :tongue:

---

### Post by taurus on 2009-04-17
Or you can try to mount it from a terminal with

```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
df -h
```

---

### Post by iamleaf on 2009-04-17
Okay I got it to start working. I just formatted the thing from a Windows platform. I've tried using transferring data between ubuntu and windows and it works. I think the laptop that I used was infected or something. It had two folders which I just couldn't delete that kept popping up: 'New Folder' and 'regvsr' 

Thing is, I'll have to keep formatting it if I want to exchange data between this ubuntu and other windows platforms.

---

### Post by wsonar on 2009-04-17
If a drive is not cleanly unmounted in either OS and then inserted into the other OS it will not be recognized properly 

You have to always stop drives before removing them even usb sticks otherwise you can loose data

---

### Post by wsonar on 2009-04-17
> **iamleaf said:**
> 

Thing is, I'll have to keep formatting it if I want to exchange data between this ubuntu and other windows platforms.

If you properly stop the drive you can move it between OS's with no problem

---

### Post by wsonar on 2009-04-17
In ubuntu you can stop the drive by unmounting it 

file | unmount volume

in windows it's the icon by the time

---

### Post by anjilslaire on 2009-04-17
Yeah, I had the U3 Launchpad on my Sandisk. They had a removal app for it.

Looking through the Transcendusa website, it looks like they have a few tools for it. Maybe that will help?
[http://www.transcendusa.com/Support/DLCenter/index.asp?LangNo=0&ItemID=TS2GJF110&axn=SRH1_RLT&DLKeyWd=jetflash]("http://www.transcendusa.com/Support/DLCenter/index.asp?LangNo=0&ItemID=TS2GJF110&axn=SRH1_RLT&DLKeyWd=jetflash")

---

### Post by rustutzman on 2009-04-17
> **wsonar said:**
> In ubuntu you can stop the drive by unmounting it 

file | unmount volume

in windows it's the icon by the time


I think it's supposed to be umount not unmount

Russ

---

### Post by cbbnewbie on 2010-06-08
hi i have a similar problem, but idont use the usb to transfer data but a storage device i plug into a component so once i used in in the component and i want to add more songs i need to format it again??

this only happends in ubuntu but when im in lxde it is automounted once i insert it.

---

