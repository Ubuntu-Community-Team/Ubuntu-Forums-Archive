---
title: "[SOLVED] USB-disks do not automount at reboot"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by granit on 2009-01-05
Hi!

I am pretty new to ubuntu (8.10) and have a problem where my three usb-disks do not mount at startup. 

It is possible to manually mount them in terminal using sudo mount /dev/sdb1 /media/FOTO etc, but not automatically.

Two of my USB-disks are NTFS and one is ext3.

Ive tried to add the following to my fstab.

# /dev/sdb1
# 189GB ext3
UUID=29e16303-6c2a-4f6e-8065-0cb18bd8309b /media/macups ext3 defaults 0 0

# /dev/sdc1
# 500GB ntfs - 1st partition
UUID=84B05EBCB05EB480 /media/MEDIA-500GB ntfs-3g auto,users,uid=1000,gid=501,utf8,dmask=027,fmask=1 37 0 0

# /dev/sdc2
# 500GB ntfs - 2nd partition
UUID=E4B88744B8871468 /media/Progr-500GB ntfs-3g auto,users,uid=1000,gid=501,utf8,dmask=027,fmask=1 37 0 0

# /dev/sdd1
# 300GB hd. ntfs
UUID=76DC9AE7DC9AA0C3 /media/FOTO ntfs-3g auto,users,uid=1000,gid=501,utf8,dmask=027,fmask=1 37 0 0

Any help is highly appreciated!
Simon

---

### Post by taurus on 2009-01-05
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by granit on 2009-01-06
Hi,

the output of sudo fdisk -l

comments: the sda-disk still has some windows partitions that I do not want to mount (and that obviously are a bit corrupt). After restart the devicenames have been changed, the sdb-disk was sdc, the sdc-disk was sdd and the sdd-disk was sdb, I don't know why this happens. 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x474d6a2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40952488+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            5100        8923    30716280    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8924       14593    45544275    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            8924       11473    20482843+   7  HPFS/NTFS
/dev/sda6           11474       12748    10241406    7  HPFS/NTFS
/dev/sda7           12749       14350    12868033+  83  Linux
/dev/sda8           14351       14593     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ce912ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       50993   409601241    7  HPFS/NTFS
/dev/sdb2           50994       60801    78782760    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2cea6ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003ea5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24792   199141708+  83  Linux

Thanks!
Simon

---

### Post by logos34 on 2009-01-06
What does 

ls -l /media

show?

You could try commenting out the ntfs entries you manually added and run [ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron)") to generate new ones.  

Or:

Assign them volume labels, comment out the fstab entries and allow the system to automount them (they should do so by label in /media), e.g.:

sudo ntfslabel /dev/sdc1 label

sudo tune2fs -L label /dev/sdb1

---

### Post by granit on 2009-01-06
ls -l /media shows:

simon@addisoncentral:~$ ls -l /media
total 86
lrwxrwxrwx 1 root  root     6 2009-01-04 00:02 cdrom -> cdrom0
dr-xr-xr-x 1 root  root  2048 2006-11-01 00:33 cdrom0
drwxrwxrwx 1 root  root  8192 2009-01-01 10:42 FOTO
drwxr-xr-x 4 simon root  4096 2009-01-04 22:09 macups
drwxrwxrwx 1 root  root 16384 2009-01-02 13:09 MEDIA-500GB
drwxrwxrwx 1 root  root 57344 2009-01-03 13:28 Progr-500GB

The problem is that the usbdisks do not show up at reboot (neither with nor without changes in fstab). These directories (exkluding cdroms) have been manually created be me, I will try to delete the directories, comment out changes in fstab and reboot. I will also try the ntfs-config tip. 

Regards,
Simon

---

### Post by granit on 2009-01-06
Tried to delete directories, comment out changes in fstab and reboot, but still no automounting. :(

/simon

---

### Post by granit on 2009-01-06
Not my lucky day. ntfs-config recognises my old windows partitions, that is /dev/sda1, sda2, sda5 and sda6 but none of my usb disks. But I can still mount manually, ie sudo mkdir /media/FOTO, sudo mount /dev/sdd1 /media/FOTO

/simon

---

### Post by granit on 2009-01-06
OK. 

I opened gparted and the ntfs disks seemed to be without labels (although are visible in nautilus). I ran tune2fs to set a label of my ext3-drive, installed ntfsprogs and ran ntfslabel to set labels on the ntfspartitions. Thereafter I restarted my computer - but... still no automounting and the disks still do not show up in ntfs-config.:confused:

any help is wanted! :D

/simon

---

### Post by vanadium on 2009-01-06
To troubleshoot your /etc/fstab, look at the output of the command

```

sudo mount -a

```
This command only produces output when there is an error. For your ntfs drives, you have "fmask=1 37" in your line. The space between 1 and 3 should not be there.

That said, USB drives normally should automount automatically without any line in /etc/fstab. A frequent problem with ntfs is that the volume was not properly shut down, in which case Ubuntu won't automount it. However, this seems not the issue for you because you can manually mount and you also have the issue with an ext3 drive.

---

### Post by granit on 2009-01-06
Thanks. I'll try to edit the fstab, but now I have commented all manually added lines. If I unmount my drives and type sudo mount -a I get no error, but none of the drives are mounted.

Does my manually added directories in /media has anything to do with the problem? BTW the disks were automounted the first time when I installed Ubuntu and thereafter they have been attached to the same computer.

/simon

---

### Post by logos34 on 2009-01-06
/media mounts look ok

and the Bios obviosuly sees them, otw you wouldn't be able to manually mount them

As for automounting, check Nautilus file browser>edit>prefs>media tab.  Is the 'Browse media when inserted' checked (default iirc)?

Or Menu panel>syatem>prefs>removable drives>storage>'Mount removable drives when hotplugged' and 'Mount removable media when inserted' 

> **vanadium said:**
> A frequent problem with ntfs is that the volume was not properly shut down, in which case Ubuntu won't automount it. However, this seems not the issue for you because you can manually mount and you also have the issue with an ext3 drive.

+1

---

### Post by granit on 2009-01-06
Hi! 

Reg Nautilus file browser>edit>prefs>media tab. "Browse media" is checked.

I can't find Menu panel>syatem>prefs>removable drives, I have system>prefs>Remote Desktop and next is SCIM input... I might miss something here, ubuntu is still quite new to me.

/simon

---

### Post by logos34 on 2009-01-06
hmmm...

---

### Post by granit on 2009-01-08
Still no solution... If anybody experience the same problem or has at tip please advice.

Regards,
Simon

---

### Post by granit on 2009-01-12
By accident found a solution. I had a power outage and my usb disks shut down while my lap top used its battery. When the power came back ubuntu automounted my disks as for example _FOTO (that is _LABEL). I came up with the idea to change LABELs on the disks (I wrote labels in gparted to the disks before, but the same labels). So I changed Labels on all three disks in gparted, rebooted and VOILA the disks automounted. Probably my fstab should work now as well, but for the moment I do not want to fix anything that is not broken...

Simon

---

### Post by granit on 2009-01-12
More troubles. Changing labels was part of the solution but not the whole. The main problem is that my usb-disks start up slowly at reboot. They also start up in different orders - that is, my FOTOUSB is one time /dev/sdb1 and the other /dev/sdb2. Therefore I had to use UUIDs in the fstab.
1. find out the devicenames of the partitions
sudo fdisk -l
2. find out the UUIDs of the partitions
sudo vol_id -u device
3. open fstab
sudo gedit /etc/fstab
4. add lines#/dev/sda1
UUID=12102C02C0210EB83 /media/MEDIA-500GB ntfs-3g defaults 0 0

save.

Now it is possible to mount all drives through sudo mount -a

But the problem at reboot remained and I think the problem was that my disks starts slowly and are not ready to be mounted at boot. To solve this I created at script

1. sudo gedit mountdisks.sh
Add
#!/bin/bash
sudo mount -a
2. save 
3. change attributes to executable
sudo chmod +x mountdisks.sh
4. copy to init.d
sudo cp mountdisks.sh /etc/init.d
5. make the script to start up at a later stage of the start up process
sudo update-rc.d -f mountdisks.sh start 99 2 3 4 5 .

Reboot and everything works fine.

Not really simple - if anybody finds a better solution please advice!

Simon

---

