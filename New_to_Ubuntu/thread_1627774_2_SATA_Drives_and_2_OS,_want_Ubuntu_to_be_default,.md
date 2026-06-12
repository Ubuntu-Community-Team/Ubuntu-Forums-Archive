---
title: "2 SATA Drives and 2 OS, want Ubuntu to be default, but"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Toronto11 on 2010-11-21
want to be able to select the Windows drive on boot up, but it only recognizes the Ubuntu drive.  I previously had an old harddrive with Windows XP as the slave drive, but when I got a new harddrive and put Windows 7 on it, but now there is no option to run that harddrive.  BIOS does recognize the drive and if I disconnect the Ubuntu drive the Windows drive automatically boots up.

Am I missing something in BIOS?

Please help.

---

### Post by oldfred on 2010-11-21
Windows combines its boot into the first install. If you installed win7 second it converted the XP to a win7 boot and moved the boot files to win7 to the XP partition. As long as win7 is in a primary partition you should be able to repair it.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.


To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by lmarmisa on 2010-11-21
What Ubuntu version do you use?.

---

### Post by Toronto11 on 2010-11-21
I'm using Ubuntu 10.04 right now, but I've updated twice on the same drive.  I think I have Grub2 - it reads as version 1.98

I had Ubuntu installed first on a SATA and then added a whole new drive to replace my old XP drive.  The new drive is a SATA too and it was a clean install of Windows 7.  

I still have the option to boot my old XP drive at at start up, but that option does not recognize W7.  The Ubuntu drive is the default drive.  Basically I just want the option to choose the Windows OS if I need to and if I don't touch anything then Ubuntu boots.

Thanks for the previous post, but I got a little lost in the txt document...

---

### Post by Toronto11 on 2010-11-21
Does this help at all?

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38256   307291288+  83  Linux
/dev/sda2           38257       38913     5277352+   5  Extended
/dev/sda5           38257       38913     5277321   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb2eec764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdc: 8011 MB, 8011120640 bytes
16 heads, 32 sectors/track, 30560 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30560     7823344    c  W95 FAT32 (LBA)

---

### Post by lmarmisa on 2010-11-21
Try this command:

```

sudo update-grub2

```

If you do not get any success, you should follow the diagnosis procedure proposed by oldfred.

---

### Post by Toronto11 on 2010-11-21
oldfred's instructions are a little over my head - i'm a little new to this, so hopefully the grub 2 update will work.

thanks for all the help.

---

### Post by lmarmisa on 2010-11-21
Please, post the output of the update-grub2 command.

---

### Post by Toronto11 on 2010-11-21
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done

---

### Post by lmarmisa on 2010-11-21
I have no experience with Windows 7 but it seems that GRUB only detects its recovery partition (tiny partition of 102 Mbytes).

Are you able yo boot Windows 7 now?.

---

### Post by oldfred on 2010-11-21
If you install win7 to a new drive it creates a hidden 100MB boot/recovery partition to boot from, then the main install goes into the next partition. If there are multiple windows installs it moves all the boot files to one partition and update for XP the boot.ini or if win7 updates the BCD to boot all the versions of windows. Grub will only find one copy of windows because only one has boot files.

The boot script helps us understand what is installed where. You should be able to just download it and run it from the instructions in the link. 

The windows multiboot site is just for understanding how the windows handles booting. You can just review pictures if the detail is too much as the pictures explain it pretty well.:)

---

### Post by lmarmisa on 2010-11-22
Only a question, oldfred.

update-grub2 detects the hidden 100MB boot/recovery partition. Will grub be able to start Windows 7?.

---

### Post by oldfred on 2010-11-22
That should work and does for many if the rest of the windows installs are correct. When booting the one that is found it should from BCD present all the versions of windows installed and let you choose which windows to boot. Boot script lets us see if files are in correct locations.


The way to avoid it is to completely install a second windows to a primary partition and have the boot flag (active partition in windows) set on the partition for the new install. Then windows does not combine boots. Of course from windows you can only boot one, but you can move boot flag to boot the other from a windows boot loader.

---

### Post by amjjawad on 2010-11-22
> **lmarmisa said:**
> Only a question, oldfred.

update-grub2 detects the hidden 100MB boot/recovery partition. Will grub be able to start Windows 7?.

Just for the record:

**sudo update-grub** = *sudo update-grub2*  :)

---

### Post by amjjawad on 2010-11-22
> **Toronto11 said:**
> Does this help at all?

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38256   307291288+  83  Linux
/dev/sda2           38257       38913     5277352+   5  Extended
/dev/sda5           38257       38913     5277321   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb2eec764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdc: 8011 MB, 8011120640 bytes
16 heads, 32 sectors/track, 30560 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30560     7823344    c  W95 FAT32 (LBA)

So basically, you have 3 HDDs:
sda = Ubutnu
sdb = Windows 7
sdc = Windows XP

You could boot into Ubuntu and Windows 7 but you can't boot into XP, right?
You could boot into XP only when the other new HDDs are off from BIOS or you unplug the power cable, right?

---

