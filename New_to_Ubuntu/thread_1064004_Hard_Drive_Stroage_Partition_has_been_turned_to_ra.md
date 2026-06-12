---
title: "Hard Drive Stroage Partition has been turned to raw?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-02-08
Alright, I am quad-booting Vista, XP, Ubuntu, and OSx86 on my pc, and when I installed ubuntu, I installed the grub bootloader on my 200gb storage partition, and when I booted into vista, it asked my to format the drive! In the disk management, it shows up as RAW. How do I fix this, and if so, for free?

---

### Post by Temposs on 2009-02-08
Try booting a GParted LiveCD, and you will be able to manipulate all your partitions and see all the information about them on there:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You should be able to see moreso what the problem is from there.

---

### Post by caljohnsmith on 2009-02-08
What do you mean when you say you installed Grub to the storage partition? Did you install Grub's boot files there, or did you install Grub to the boot sector of that partition? Is the storage partition NTFS? If it is, how about posting the output of:
```

sudo fdisk -lu
sudo xxd -s 128 -l 2 -p /dev/[COLOR="Blue"]sdaX[/COLOR]
```
And replace "sdaX" with your storage partition.

---

### Post by taylor102387 on 2009-02-08
This is what I get:

```
taylor@taylor-laptop:~$ sudo fdisk -lu
[sudo] password for taylor: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x155f155f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    52428862    26214400   af  Unknown
/dev/sda2        52436160   105113294    26338567+   7  HPFS/NTFS
/dev/sda3   *   105113295   157533389    26210047+   7  HPFS/NTFS
/dev/sda4       157533390   625137344   233801977+   5  Extended
**/dev/sda5       157549455   572717186   207583866    7  HPFS/NTFS**
/dev/sda6       617329818   625137344     3903763+  82  Linux swap / Solaris
/dev/sda7       572717313   617329754    22306221   83  Linux

Partition table entries are not in disk order
taylor@taylor-laptop:~$ sudo xxd -s 128 -l 2 -p /dev/sda5
5272
taylor@taylor-laptop:~$ 

```

SDA5 is the corrupt partition and yes, it's ntfs. I have used gparted for quad-booting but I'm afraid i'll format it.

---

### Post by caljohnsmith on 2009-02-08
Getting "5272" from that xxd command means you have Grub installed to the boot sector of the sda5 partition, so that's unfortunately why you can't mount/access that partition right now in Ubuntu or Windows. Do you have a Windows XP Install CD? If so, how about booting that, go to the "recovery console" and do:
```
map
```
That will give a list of your partitions and their drive letters, find the drive letter for the sda5 partition (I think it will be listed as the 3rd NTFS partition, but maybe not), and then do:
```
fixboot X:
```
But replace X with the sda5 drive letter. Please be careful to get it right, because if you run "fixboot" on your Vista partition, that will install an XP boot sector to your Vista partition and Vista won't boot. Let me know how it goes or if you run into problems.

---

### Post by taylor102387 on 2009-02-08
YOU ARE A LIFE SAVER. That partition had all my files for sharing between OS's. And, Ubuntu didn't even give me a mount error. :D

---

### Post by caljohnsmith on 2009-02-08
Glad to hear that worked OK; cheers and enjoy all your OSes. :)

---

