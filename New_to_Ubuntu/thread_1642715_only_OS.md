---
title: "only OS"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by jackwilson on 2010-12-10
I have ubuntu 10.04 and windows xp on dual boot. I want ubuntu as my only OS. my pc will not boot from my ubuntu cd. I think it is 64 and my pc is 32, so i need to know if there is a way to install ubuntu from my download file and have it be the only OS on my pc?
What the best way to end up where I want to beeeeeee? I do not have any other blank cds nor money to get one. unetbootin does not see my flash drive when I try their method of making a boot from flash drive. It says i need to format it FAT 32. I have it formated linux FAT. I'm running out of try this ideas.:D
jackwilson

---

### Post by cariboo on 2010-12-11
If your doesn't system doesn't have a 64-bit cpu, and you try to boot a 64-bit version, there will be a  message on screen telling you why it won't run. 

You can format your usb device to fat 32 using either gparted, if you have it installed, or you can go to System->Administration->Disk Utility.

---

### Post by BugBuster on 2010-12-11
If you already have Ubuntu installed you could just delete the windows xp partition and merge that space with ubuntu or use that partition for some other purpose.
So that people can help you better could you paste the output of the following command here?
```
sudo fdisk -l
```

---

### Post by ronnielsen1 on 2010-12-11
> What the best way to end up where I want to beeeeeee? I do not have any  other blank cds nor money to get one. unetbootin does not see my flash  drive when I try their method of making a boot from flash drive. It says  i need to format it FAT 32. I have it formated linux FAT. I'm running  out of try this ideas

You could try gparted to reformat your flash drive to fat 32 or if you want to wait you could try shipit [https://login.launchpad.net/BtTZTkDfRHwsjlGL/+decide](https://login.launchpad.net/BtTZTkDfRHwsjlGL/+decide)

---

### Post by jackwilson on 2010-12-11
bunnyg@ubuntu:~$ sudo fdisk -l
[sudo] password for bunnyg: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27bb91bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 2000 MB, 2000748032 bytes
62 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008ce5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1016     1952721    c  W95 FAT32 (LBA)
bunnyg@ubuntu:~$

I also went to ubuntu web site and followed the directions to download Ubuntu 10.10 OS and boot it with my flash drive. Then I did system>administration>start up disk creator and followed the directions. screen said now you can use this devise to run ubuntu on any pc. When I restart and boot from my flash drive it says: unknown keyword in configuration file boot: _ but I am not able to type anything onto the screen.
how would I remove the windows partition and use the ubuntu that is installed now?

---

### Post by rosehipzero on 2010-12-11
Use the LiveCD to boot gpart. In Gpart, delete the Windows Partition and merge the empty partition and the ubuntu partition

---

### Post by e79 on 2010-12-11
> **jackwilson said:**
> 
I also went to ubuntu web site and followed the directions to download Ubuntu 10.10 OS and boot it with my flash drive. Then I did system>administration>start up disk creator and followed the directions. screen said now you can use this devise to run ubuntu on any pc. When I restart and boot from my flash drive it says: unknown keyword in configuration file boot: _ but I am not able to type anything onto the screen.

Since you still have your Windows partition, and you appear to have difficulties making a bootable thumdrive, just follow these steps, they never failed for me :

1. Boot in your Windows and insert your USB stick
2. Go to [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) and download this universal installer
3. Now having a working copy of Ubuntu (32 or 64 bit depending on your hardware), start the program and choose your USB stick as a destination target and give the path to your downloaded Ubuntu CD , click on 'format drive as FAT32 and then click on Start (you don't need persistence here so just ignore it) and let the software do its job  :P  (you can refer to the screenshot I included if you want).

Once finished, you shouldn't have problems rebooting into the stick to reinstall Ubuntu on any PC !

P.S : If you plan on reinstalling, make sure you have a good and valid backup of your Data of both operating system (if applicable).

Hope this helps

---

### Post by karthick87 on 2010-12-11
Boot using a live ubuntu cd..Open Gparted from System>>Administration>>Gparted

[IMG]http://imgur.com/R1H8Y.png[/IMG]

Right click on your windows partition and then select Delete.Goto Edit and select Apply all operations.Now in terminal type the following yo update your grub..
```
sudo update-grub
```

---

### Post by jackwilson on 2010-12-12
Thanks,
got my flash drive to make my PC ubuntu only.

New problems though. When I had Ubuntu 10.04 I could make a audio call on empathy, now with Ubuntu 10.10 these items are not available on the drop down menue. Audio Call,Video Call, or I should say that chat is the only one that I can click on.  Any remedies to this problem? All of my contacts have voice IM options on their end.
The other thing that has gone wrong is my flash drive is not recognised when I plug it into a usb port now

---

