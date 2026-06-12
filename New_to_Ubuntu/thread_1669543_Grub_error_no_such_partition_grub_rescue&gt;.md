---
title: "Grub error no such partition grub rescue&gt;"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Zayveeyer on 2011-01-17
Hello, I recently uninstalled a dual boot of ubuntu, as I did not use it a whole lot. Now, whenever I boot up my machine, this pops up:

error: no such partition

grub rescue>

I do not have a windows 7 installation/recovery disk, but I do have my ubuntu installation disk.

Is there anyway I can fix this?

Please and thank you.

---

### Post by drs305 on 2011-01-17
Zayveeyer,

Welcome to the Ubuntu forums.

Edit: I see you said you *uninstalled* Ubuntu:

From the LiveCD, if windows is on your first drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Just run those 2 commands. To open the terminal to run them , Applications, Accessories, Terminal.

If that doesn't fix it, read on.

We can probably fix your problem but we need a bit of information. If you will boot the LiveCD (Try) and use Firefox to go to the following site.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Read the instructions, download and run the boot info script, and then post the contents of the RESULTS.txt file.  This will give us a good idea of your boot status.

If you want to try to fix it on your own:

If it's a Wubi (inside Windows) installation, you can look at this guide by *Rubi1200*: 
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by Zayveeyer on 2011-01-17
This is what was in RESULTS.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   392,454,236   392,044,637   7 HPFS/NTFS
/dev/sda3         461,715,456   488,394,751    26,679,296   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        223CB14C3CB11C2B                       ntfs       SYSTEM                        
/dev/sda2        50C4E42FC4E4194C                       ntfs                                     
/dev/sda3        F6ECE79AECE75381                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
```

---

### Post by psusi on 2011-01-17
Run the two commands drs305 gave.

---

### Post by drs305 on 2011-01-17
Zayveeyer,

Your Windows installation is on sda, the boot files appear to be intact, and the boot flag is in place. 

Run the two lilo commands in the previous post. You will get some warnings about lilo not being fully installed. Disregard them, as you aren't really going to use lilo as your bootloader.

---

### Post by Zayveeyer on 2011-01-17
I ran the commands, and this is what came up:

```
Fatal: /dev/sda2 is not a master device with a primary parition table

```

---

### Post by drs305 on 2011-01-17
> **Zayveeyer said:**
> I ran the commands, and this is what came up:

```
Fatal: /dev/sda2 is not a master device with a primary parition table

```

Did you run the command with "sda" or did you add the partition number (sda2). It should be run by identifying only the drive - "sda".

If that wasn't the problem, when did the error message appear?

---

### Post by Zayveeyer on 2011-01-17
Sorry, I did sda2 instead of sda. And that fixed it! Thank you so much for all your help!

---

