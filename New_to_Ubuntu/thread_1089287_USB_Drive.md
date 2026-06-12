---
title: "USB Drive"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-06
I am using 8.10.

When I plug in a USB Drive, I can see the drives in Places....but I cannot see what is in the drive...even when I go 

sudo nautilus

it does not show the drive?

I am sure that this worked before....what have I screwed up?

---

### Post by Ripose on 2009-03-07
Have you tried right clicking on the drive Icon?
If it says MOUNT click it and then browse the drive.

---

### Post by dunbrokin on 2009-03-07
> **Ripose said:**
> Have you tried right clicking on the drive Icon?
If it says MOUNT click it and then browse the drive.

No icon appears on  my desktop, I have tried clicking the icon that appears under Places...but nothing happens.

---

### Post by Ripose on 2009-03-07
What file system is on the USB, ext3 or NTFS etc..

Use *Administration --> System Monitor*, click the "File Systems" tab, it should show /dev/sda1  ext3 for your main drive and /dev/sdb1 ... etc. for every drive.

Also is your USB plugged into the Front panel?
Try switching to a back port.

You can also check the drives with *gparted*, just look though, don't change anything.

---

### Post by dunbrokin on 2009-03-07
Does not show up on any of those .....placed in a different port ....can still see in Places...but not clickable......weird or what!

---

### Post by dunbrokin on 2009-03-07
Has it anything to do with Virtualbox?....I installed that recently...but it is not running now.

---

### Post by adult swim on 2009-03-07
with the drive plugged in, what does```
sudo fdisk -l
```return?

---

### Post by dunbrokin on 2009-03-07
> **adult swim said:**
> with the drive plugged in, what does```
sudo fdisk -l
```return?

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df649

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123        1338     9767520   83  Linux
/dev/sda3            1339        9605    66404677+  83  Linux
/dev/sda4            9606        9729      996030   82  Linux swap / Solaris

Disk /dev/sdb: 521 MB, 521142272 bytes
32 heads, 32 sectors/track, 994 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         994      508911+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(992, 31, 32) logical=(993, 31, 31)

---

### Post by adult swim on 2009-03-07
see if you can mount it by opening a terminal and entering in ```
sudo mount /dev/sdb1 /mnt
``` then open up nautilus and browse to /mnt and see if your stuff is there.  
Partition 1 has different physical/logical endings:
phys=(992, 31, 32) logical=(993, 31, 31)
ive never seen this before, so im not sure if that will cause you problems or not.

---

### Post by dunbrokin on 2009-03-07
It appeared to mount....least no error was returned... but it did not show on Nautilus.

---

### Post by orethrius on 2009-03-07
Hey, here's a thought, what contents show up when you open Places > Computer?

---

### Post by malditonuke on 2009-03-07
> **dunbrokin said:**
> I am using 8.10.

When I plug in a USB Drive, I can see the drives in Places....but I cannot see what is in the drive...even when I go 

sudo nautilus

it does not show the drive?

I am sure that this worked before....what have I screwed up?


Have you edited the partitions on the drive?:

I was fooling around with one of my USB drives, deleted the partition, formated it, etc etc.  Eventually I could see it in my places as "8GB Media", but I couldn't mount it.  Nothing I could do in Ubuntu seemed to make it usable, so I went to Windows and reformatted it there, which worked.

I'm not suggesting you reformat it (especially if you have important data on it).  But if you were doing the same thing I was, that might be your problem.

---

### Post by dunbrokin on 2009-03-07
> **orethrius said:**
> Hey, here's a thought, what contents show up when you open Places > Computer?


It shows there...but when you click on it, it says it cannot mount file.

---

### Post by dunbrokin on 2009-03-07
[QUOTE=

I'm not suggesting you reformat it (especially if you have important data on it).  But if you were doing the same thing I was, that might be your problem.[/QUOTE]

That sounded like the answer....UNTIL...I plugged them into the other PC I have which is dual boot with the intention of reformatting them when I booted up the windows.....the other machine (idenical to this one: Intrepid, same hardware etc..except dual bood) picked the USB drive up instantly.

---

### Post by iamkrazee on 2009-03-07
```
mkdir ~/drv1
sudo mount /dev/sdb1 ~/drv1

```

---

### Post by dunbrokin on 2009-03-07
Some more info on the problem:

For some reason it is unable to mount....it should mount automatically as it does on the other PC...there must be a file missing or corrupted on this machine I guess.

In properties the "Open with" tab has nothing in it...

When I browse to "Open Folders" it appears to take it...but then when I click on the icon it says Open Folder file does not exist.

---

### Post by iamkrazee on 2009-03-07
Please try the above. I&#7743; guessing that it´s an issue with your permissions. 

Just be sure to unmount the device before using umount.

---

### Post by dunbrokin on 2009-03-07
Even when I right click to mount volume, it will not mount. I have 3 USB sticks and all of them are exhibiting the same problem.

---

### Post by iamkrazee on 2009-03-07
I´m quite sure of it now, that you´re mounting it into places where it should not be. 

Whenever you mount the USB sticks, do the following to confirm it : 

```
sudo su
ls /mnt

```

---

### Post by dunbrokin on 2009-03-07
> **iamkrazee said:**
> I´m quite sure of it now, that you´re mounting it into places where it should not be. 

Whenever you mount the USB sticks, do the following to confirm it : 

```
sudo su
ls /mnt

```

Tried that....now I can mount....but the error message is now that it cannot mount file!

---

### Post by iamkrazee on 2009-03-07
Ok now just let me go through this step by step.

Step 0 : Remove all drives, physically and logically.

Step 1 : Create a new folder, with any name, in your home folder. Use command line or nautilus or dolphin, whichever. We´ll call this folder ´drv1´ for now.

Step 2 : Fire up console and ```
sudo mount /dev/sdb1 /home/alok/drv1 -o gid=users
``` (replace with your home directory)

Step 3 : Open the folder in your Nautilus/Dolphin.

This absolutely *HAS* to work.

---

### Post by dunbrokin on 2009-03-07
:~$ sudo mount /dev/sdb1 /home/pj/drv1 -o gid=users
mount: special device /dev/sdb1 does not exist


Sorry....no change...still same problem.

---

### Post by Ripose on 2009-03-07
Did anyone mention that Linux will not recognize a USB HDD if it was previously mounted on a Windows OS, unless you use the Windows "Safely Remove Device" feature.

---

### Post by dunbrokin on 2009-03-07
> **Ripose said:**
> Did anyone mention that Linux will not recognize a USB HDD if it was previously mounted on a Windows OS, unless you use the Windows "Safely Remove Device" feature.

Nope...but then my PC did recognise these USB's before and my second PC which is a dual boot with XP, still recognises them when it is in Ubuntu mode.

---

### Post by dunbrokin on 2009-03-08
It now appears that not only are my USB Drives not recognised, my compact flash for my camera is also not seen or recognised.....something really weird is going on here.

---

### Post by Ripose on 2009-03-08
I'm still working on a similar issue myself (not fixed yet) but here is a [link to information]("http://www.usbman.com/Troubleshooter%20General.htm") that may be of use.

---

### Post by dunbrokin on 2009-03-08
OK, I have solved this problem....the problem was caused by the line below inserted in my fstab file on the recommendation of a Linux Magazine which suggested that this was a way to speed up your disk....it may do so...but it also screws up your USB disks.

#defaults,noatime,data=writeback

---

### Post by iamkrazee on 2009-03-10
> **dunbrokin said:**
> :~$ sudo mount /dev/sdb1 /home/pj/drv1 -o gid=users
mount: special device /dev/sdb1 does not exist


DOOD ! That was with the assumption that /dev/sdb1 is where it´s getting detected. Check where it gets detected at.

Check where it is by : ```
sudo fdisk -l
```

---

### Post by dunbrokin on 2009-03-10
Thanks, problem solved...see above.

---

### Post by orethrius on 2009-03-10
Apparently it was an issue in /etc/fstab.  
This should be noted for future reference.

:)

---

### Post by iamkrazee on 2009-07-17
Mods please lock this thread.

---

