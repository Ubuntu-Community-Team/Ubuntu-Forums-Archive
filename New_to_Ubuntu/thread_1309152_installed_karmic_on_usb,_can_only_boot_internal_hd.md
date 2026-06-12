---
title: "installed karmic on usb, can only boot internal hd if stick is connected"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by tpjk on 2009-11-01
hey everyone,

yesterday i installed karmic on a 16gb usb stick (permanent installation, not the live cd version) which worked fine: it boots, and i have no problem getting into the systems on my internal hd - AS LONG AS THE STICK IS PLUGGED IN.

if it isn't, i immediately get this:

GRUB loading.
error: no such disk
grub rescue>

so essentially, my situation is the same as [THIS PERSON'S]("http://ubuntuforums.org/showthread.php?t=1280329"). 

but, since on my internal hd i am dual booting win xp (boot partition) and intrepid i would like to know if i can still fix it the same way the person describes in the thread i linked to (i.e. by running grub-install /dev/sda from the live cd).

this is the output of sudo fdisk -l:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc51bc51b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2       486287550   488392064     1052257+   c  W95 FAT32 (LBA)
/dev/sda3        81915435   183574754    50829660    5  Extended
/dev/sda4       183574755   486287549   151356397+   b  W95 FAT32
/dev/sda5        81915498   179670959    48877731   83  Linux
/dev/sda6       179671023   183574754     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.0 GB, 16028794368 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31306239 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00021b0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          52    31283909    15641929   83  Linux
```
any help will be greatly appreciated.

cheers!

---

### Post by ZankerH on 2009-11-01
You installed the GRUB bootloader on the USB stick. Which is OK if you want to boot it off any other PC, but in your case, the better decision would probably have been to install it on the HD's MBR.

---

### Post by 0cton on 2009-11-01
Looks like you will have to reconfigure grub and root it to /dev/sda
There should be plenty of guides on google even in this forum about it.
I don't remember it by heart, sorry.
basically you run grub as root
and you root(/dev/sda)
than configure(/dev/sda) /Ithink...

---

### Post by QLee on 2009-11-01
[QUOTE=tpjk]yesterday i installed karmic on a 16gb usb stick (permanent installation, not the live cd version) which worked fine: it boots, and i have no problem getting into the systems on my internal hd - AS LONG AS THE STICK IS PLUGGED IN.

if it isn't, i immediately get this:

GRUB loading.
error: no such disk
grub rescue>

any help will be greatly appreciated.[/QUOTE]

I will explain what you did.

You installed to the removeable drive but you chose to overwrite  the MBR of the internal drive, telling it to look for your /boot on the removeable drive (which is no longer plugged in). 

Since this was a Karmic install you probably also now are using GRUB2 while the others were probably installed with legacy GRUB.

If you rewrite the MBR on the internal drive to point to the /boot on it, you will restore the booting for those two os but you won't have Karmic because the menu which includes karmic is on the removeable drive. (You could probably put in a new stanza and chainload)

I assume that when you finished installing Karmic, upon booting, you had menu stanzas for all three OS. If that's the case and it were me, I would copy exactly the /boot from the removeable (note exactly, I would use rsync but there are other ways) to the /boot on the internal and then use Karmic GRUB2 to overwrite the Internal Drive MBR pointing to the /boot on it. If everything works correctly, then this would let you boot the two OS on the internal and you'd error if the removable wasn't attached and you selected that OS.

Don't try anything unless you understand all steps fully. There are ways to error and make things worse.

Usually I don't suggest reinstalling, however, reinstalling Karmic choosing your /boot on the internal as boot partition and then proceeding just as you did previously would probably be fastest and safest way to get what you want.

---

### Post by tpjk on 2009-11-01
> **QLee said:**
> I assume that when you finished installing Karmic, upon booting, you had menu stanzas for all three OS.

yes, that's what happened.

> If that's the case and it were me, I would copy exactly the /boot from the removeable (note exactly, I would use rsync but there are other ways) to the /boot on the internal and then use Karmic GRUB2 to overwrite the Internal Drive MBR pointing to the /boot on it. If everything works correctly, then this would let you boot the two OS on the internal and you'd error if the removable wasn't attached and you selected that OS.

Usually I don't suggest reinstalling, however, reinstalling Karmic choosing your /boot on the internal as boot partition and then proceeding just as you did previously would probably be fastest and safest way to get what you want.

thank you for your reply. i do understand the steps of the first method you mentioned but i think i would probably need a few more details on each one of them as i've never had to mess with grub before.
so for now i'll just go with the second method. just to make sure i know exactly what you were getting at - is this what i would have to do:

1) boot from the karmic live cd
2) plug in the usb stick
3) start the installation process
4) tell the installer to format the stick and install ubuntu to it
5) click the 'advanced' button during step 7 (that's the one that gives you a recap of all the changes that are going to be made to your partition right before the installation process starts)
6) choose /boot on the internal hd as boot partition
7) start the actual installation process

again, thank you for your help!

---

### Post by tpjk on 2009-11-01
ok so i went through the installation process up until the point where you can go into 'advanced options'.

'install bootloader' is checked. i'm not sure which entry i should choose from the drop down menu 'device for bootloader installation' though since there's an entry both for the entire internal hd (dev/sda) and one for my win xp partition (dev/sda1) which is flagged as boot in gparted.

any suggestions?

---

### Post by tpjk on 2010-03-25
ok so in case anyone ever runs into the same problem - i fixed it by following the instructions in this thread:

[thread=224351]how to restore grub from the live cd[/thread]

took like SEVEN minutes. and that includes getting to the desktop on the intrepid live cd. :popcorn:

---

