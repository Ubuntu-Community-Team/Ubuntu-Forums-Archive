---
title: "Unable to mount second NTFS drive, first one works"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by rpete on 2008-12-10
Hi, I managed to mount one NTFS drive, but haven't been able to mount my Seagate Free Agent Go 320gb NTFS drive.  When I attach it to the computer using the USB connection, it's icon doesn't appear on my desktop but I get the message "can't mount volume". The drive was first used on a Windows pc and has data on it I would like to access. I connected and disconnected it to a Windows pc the other day, because a thread in the forum suggested it hadn't been closed properly.  This did not change the cannot mount message. 

When I use the force option in terminal I get what I call a lesson on mounting which explains "note that one does not really mount a device, one mounts a file system."  The first line of the output is "unclean shutdown."  I don't know how to copy the entire output. I double click on a word and press control shift c to copy but this only copies the one word.

---

### Post by taurus on 2008-12-10
So, did you use the Safely Remove Hardware to unmount it first before you unplugged it the last time you used that drive in windows?

Otherwise, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by mikechant on 2008-12-10
I'd suggest plugging the drive in under windows and then from the command line doing a
chkdsk d:
Where d: is the relevant drive letter.

If you get any errors, you need to try
chkdsk /F d:
to fix them.
(You may need to use /X to force the operation - type help chkdsk at the command prompt for more info).

Assuming you can then get a clean chkdsk, then as Taurus says above, you need to make sure you use the 'safely remove hardware' option before unplugging the drive.

---

### Post by rpete on 2008-12-10
> **taurus said:**
> So, did you use the Safely Remove Hardware to unmount it first before you unplugged it the last time you used that drive in windows?

Otherwise, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```
Hi, No I did not use the safely remove hardware in windows.  Sudo fdisk -l shows  three devices in the output, the computer's hard drive, a Western Digital MyBook external drive and the Seagate drive. Could you do me a favor and tell me how to cut and past the output from terminal to this message?

---

### Post by rpete on 2008-12-10
> **mikechant said:**
> I'd suggest plugging the drive in under windows and then from the command line doing a
chkdsk d:
Where d: is the relevant drive letter.

If you get any errors, you need to try
chkdsk /F d:
to fix them.
(You may need to use /X to force the operation - type help chkdsk at the command prompt for more info).

Assuming you can then get a clean chkdsk, then as Taurus says above, you need to make sure you use the 'safely remove hardware' option before unplugging the drive.
Thanks for the suggestion, but I don't have a Windows pc handy. I took the drive to school the other day.

---

### Post by Michael.Godawski on 2008-12-10
hey, 

just mark it with your mouse, and then post it with your middle mouse button if you have one.

Or copy with ctrl+shift+c

---

### Post by Zack McCool on 2008-12-10
> **rpete said:**
> 
When I use the force option in terminal I get what I call a lesson on mounting which explains "note that one does not really mount a device, one mounts a file system."  The first line of the output is "unclean shutdown."  I don't know how to copy the entire output. I double click on a word and press control shift c to copy but this only copies the one word.

This error would indicate that you missed a character when trying to manually mount.  Looks like you tried to mount /dev/sdc (or whatever the drive is) which cannot be done.  You need to mount /dev/sdc1 (the first partition on sdc, change the c to the appropriate letter).

Also, make sure you are using ntfs-3g rather than just ntfs to mount it.  The force option should clear the ntfs journal, allowing it to mount even if it wasn't cleanly unmounted from Windows.

---

### Post by rpete on 2008-12-10
> **Michael.Godawski said:**
> hey, 

just mark it with your mouse, and then post it with your middle mouse button if you have one.

Or copy with ctrl+shift+c
Hi.  I'm still having a problem with this. In terminal I move the cursor up to the beginning of the output, to the first word on the left.  I double tap the middle button and press control shift c then control shift v but it only copies that first word to the command prompt.  How do I paste to this thread?

---

### Post by taurus on 2008-12-10
You can highlight the text that you want to copy with the left button.  Then, paste what you have highlighted with the middle scroll bar.

Otherwise, just take a screenshot of the terminal with the output, System -> Accessories -> Take Screenshot, and post it here.

---

### Post by rpete on 2008-12-10
> **taurus said:**
> You can highlight the text that you want to copy with the left button.  Then, paste what you have highlighted with the middle scroll bar.

Otherwise, just take a screenshot of the terminal with the output, System -> Accessories -> Take Screenshot, and post it here.
Thanks for the instructions. Here is the output of sudo fdisk -l and df -h

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13         404     3148740    b  W95 FAT32
/dev/sda3   *         405       38472   305781210   83  Linux
/dev/sda4           38473       38913     3542332+   5  Extended
/dev/sda5           38473       38913     3542301   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
richard@dell-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             290G   16G  259G   6% /
varrun                1.8G  112K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   76K  1.8G   1% /dev
devshm                1.8G   12K  1.8G   1% /dev/shm
lrm                   1.8G   39M  1.7G   3% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon      290G   16G  259G   6% /home/richard/.gvfs
/dev/sdc1             466G   22G  445G   5% /media/My Book
richard@dell-desktop:~$

---

### Post by az on 2008-12-10
> **Zack McCool said:**
> This error would indicate that you missed a character when trying to manually mount.  Looks like you tried to mount /dev/sdc (or whatever the drive is) which cannot be done.  You need to mount /dev/sdc1 (the first partition on sdc, change the c to the appropriate letter).

Also, make sure you are using ntfs-3g rather than just ntfs to mount it.  The force option should clear the ntfs journal, allowing it to mount even if it wasn't cleanly unmounted from Windows.

I think that if you tried to mount the whole device, you would get a "bad superblock" error rather than "unlean shutdown".

To fix an NTFS filesystem unclean shutdown, use ntfsfix.  Install the ntfsprogs package and run
sudo ntfsfix /dev/sdd1 (or whatever the correct partition is).

Run
cat /proc/partitions

or 
sudo lshw -C disk -short

to see what drives are available and what their device names are.

---

### Post by rpete on 2008-12-10
Hi, I went to synaptics manager and found I had already installed ntfsfix I ran the command and the drive mounted.  Thanks very much for the help!

---

