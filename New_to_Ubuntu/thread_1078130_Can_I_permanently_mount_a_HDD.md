---
title: "Can I permanently mount a HDD?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by calderp on 2009-02-23
I am running Ubuntu on a computer that originally had Windows Vista. I shrunk the Vista partition and installed Ubuntu into a new partition, but most of my files etc are on the Windows partition. This is extremely annoying as every time I want to use a file from it, I have to mount the drive. Mainly this is a problem because when I'm using Amarok for my music, if I forget to open/mount the Windows drive before I open Amarok, it screws with all my library settings and I have to rescan everything. Is is possible to have this drive permanently mounted so I wouldn't have to deal with this? Or is there a solution through Amarok?
Thanks!

---

### Post by konqueror7 on 2009-02-23
yes you can, the easiest way is to download ntfs-config from the repos,
```
sudo apt-get install ntfs-config
```
it will then appear in your applications menu in the system section...

the other way is to add the drive during boot...
first install ntfs-3g if you still don't have,
```
sudo apt-get install ntfs-3g
```
then,
```
sudo fdisk -l
```
get the details from here to which drive you want to mount, now add it, in the terminal again,
```
sudo gedit /etc/fstab
```
then add the following lines,
```
[COLOR="Blue"]/dev/sda1[/COLOR] [COLOR="Red"]/media/Main[/COLOR] ntfs-3g defaults 0 0
```

just change the blue one with the results from the "fdisk -l" command, and the red with the mount folder...

---

### Post by Locke_99GS on 2009-02-23
NTFS support has worked (rw) out of the box since Hardy, I believe, and does so in Intrepid. If you're using one of these, don't worry about installing ntfs-3g. You can use *ntfs* as a fs type in fstab, rather than *ntfs-3g*.

A side note: If you find yourself moving your drives around often, as I somehow do, consider providing the drives UUID in fstab instead of it's device location. The UUID doesn't change when you move a drive, where it's path may. *blkid* will show you the UUID of your drives.

---

### Post by konqueror7 on 2009-02-23
> **Locke_99GS said:**
> NTFS support has worked (rw) out of the box since Hardy, I believe, and does so in Intrepid. If you're using one of these, don't worry about installing ntfs-3g. You can use *ntfs* as a fs type in fstab, rather than *ntfs-3g*.

i agree with him, only if you use 8.10...btw, what ubuntu version do you use?

---

### Post by shredder12 on 2009-02-23
this is a small tutorial to permanently mount a hard drive partition.. so that it gets mounted everytime computer is switched on..
[https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point](https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point)

hope this helps..

---

### Post by theozzlives on 2009-02-23
Try a modification of [this.]("http://ubuntuforums.org/showthread.php?t=1015834")

---

