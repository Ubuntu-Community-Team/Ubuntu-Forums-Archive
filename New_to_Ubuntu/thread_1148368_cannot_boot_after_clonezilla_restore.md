---
title: "cannot boot after clonezilla restore"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by hit1mn on 2009-05-04
hi all, 
 
I completed a restore yesterday of Ubuntu 9.04 server that I made a few weeks ago and am sitting at a blinking cursor. I have removed a usb flash and usb wifi since the restore and still nothing.  

The restore process went as expected and did not see any errors except I'm not sure how to access the logs.  
 
Clonezilla ver is a dl from yesterday and the restore is ext2/ext3 
 
I assumed grub was the issue and can access if running the server rescue cd but get a file not found error when running find /boot/grub/stage1 

Then ran root (sda,4) and get error 23 error while parsing number
 
At that point I dl supergrub iso and ran the mbr repair with no luck. 
 
I'm still figuring a mbr issue because clonezilla sees all the internal hd's.  
 
Decided to run the restore again and made sure restore mbr was checked and watched for any errors....nogo             
 
MB BIOSTAR TFORCE TA790GX 128M RT 
CPU AMD|PH X4 9950 BLK2.6G 65N R 
MEM 2Gx4|OCZ OCZ2G8008GQ R (8GB total) 
WinTV-HVR-1800 (CX23385/7 driver) 
SATA HD 1T|WD 32M WD10EADS (2ea)(Green) 
SATA HD 500GB WD (1ea) Blue 
DVD BURN SAMSUNG|SH-S223Q LS 
2.6.28-11-server w/GUI 

thanks!

---

### Post by hit1mn on 2009-05-04
I restored the image again with the clonezillalivejaunty iso and have the same result. 
 
I did notice after the image restore was complete and proceeding to reboot that it threw some errors but it flashes by too fast to see exactly what it says.  
 
the error was something to the effect of cannot read superblock

---

### Post by jerrrys on 2009-05-04
hi hit1mn:

i use clonezilla on multiple hdd's without issue. i dont remember the exact wording of it, but at the start you have the option to copy image or copy hdd to hdd. i use the second choice. also it gives you the option to copy boot/grub (once again i dont remember the exact words used). are you doing this? just a couple of simple ideas, hope it helps...

---

### Post by hit1mn on 2009-05-04
hi jerrys

Yes, the default option in clonezilla to reload grub is checked off.

I am simply trying to restore from a clonezilla image dump to hd.

After some trial and error I am able to see this via ubuntulive

grub> find /grub/stage1
 (hd0,4)

grub> root  (hd0,4)

grub> setup  (hd0,4)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
  Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
  Running "install /grub/stage1 (hd0,4) /grub/stage2 p /grub/menu.lst "... succe
eded
Done.

grub>

Quit and reboot, seems to go as expected: no errors. 

Still sitting @ blinking cursor

---

