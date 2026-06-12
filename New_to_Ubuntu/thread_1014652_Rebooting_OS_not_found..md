---
title: "Rebooting OS not found. ????"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by trigity on 2008-12-18
[COLOR="DarkGreen"]I have to wait at the acer slash screen for like 5-10 mins then I get something like this...

Blah blah blah!!!!!

OS not found [/COLOR]

Any ideas? this has been happening since the install around a month ago, it's making me a little :mad:now 

Thanks in advance...

output as follows

YUKON PXE v.6.15.1.3 (20070328)
PXE-E61 MEDIA TEST FAILURE, CHK CABLE
PXE-M0F EXT PXE ROM 
OPERATING SYSTEM NOT FOUND

HELPPPPPPPPPP MEEEEEEEEEE  PLEEEEEAAASSEEE

---

### Post by theozzlives on 2008-12-18
sounds like a hard drive problem

---

### Post by trigity on 2008-12-18
I have to physically turn off/then ON will that damage anything.?

---

### Post by trigity on 2008-12-18
What? I don't understand is it.. Fixable?****

---

### Post by bumanie on 2008-12-18
Boot a live cd (if you can) and post the output of > sudo fdisk -lu

---

### Post by theozzlives on 2008-12-18
If the HD is bad, then it has to be replaced. It sounds like it's looking for the HD and not finding it.

---

### Post by trigity on 2008-12-18
this is what I got
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b383b37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031306752 bytes
32 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

This is all greek to me still but I'm getting better...

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         999     1006870+   6  FAT16

---

### Post by trigity on 2008-12-18
> **bumanie said:**
> Boot a live cd (if you can) and post the output of

I posted the output did you see it?

---

### Post by trigity on 2008-12-18
> **bumanie said:**
> Boot a live cd (if you can) and post the output of
Did you see my outputs for my delema

---

### Post by bumanie on 2008-12-18
sda has linux on it ;sdb looks like a usb thumb-drive. The output of sudo fdsik -l looks OK, one has to suspect that there is an issue either with your hardware or the filesystem itself has something wrong. Try a > sudo fsck /dev/sda in terminal and see if it can find and fix any errors in the filesystem (if there are any). If not, go to your hard drive manufacturers website and download their tools for inspecting hard drives faults - most of the manufacturers have them available - they tools are a .iso that can be burned into a bootable cd.

---

