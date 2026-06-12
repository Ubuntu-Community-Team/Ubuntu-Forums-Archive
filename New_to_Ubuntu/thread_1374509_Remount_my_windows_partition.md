---
title: "Remount my windows partition"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Qualia on 2010-01-06
Hey, I am using Ubuntu off a Live CD, and I just resized my windows partition earlier, but I had to unmount it. I want to remount it again. 

How do I do that? I see an application called Palimpset Disk Utility. Is that it? If so, how do I remount a partition?

 I don't really trust myself with the Terminal either, I almost typed a verry bad command with it... so I'd prefer using a GUI.

---

### Post by x33a on 2010-01-06
just right click the partition in nautilus (side panel), and click mount.

---

### Post by Qualia on 2010-01-06
hmm, this is weird, it claims its mounted, but whenever I boot into windows, it always trys to "verify volume". In can still acces my files from the windows partition in windows, but it always says it has trouble with the "volume". But I can still acces files...

 If it helps, I unmonuted my windows partition using Gparted from the version 8 Ubuntu Live CD, but I could not figure out how to install 8, so I am using a 9.10 Live CD right now.

I didn't screw up the hard disk did I? :|

---

### Post by adam814 on 2010-01-06
It's running chkdsk when you start Windows?  If Windows is starting afterward you're probably ok.  I'm guessing you didn't defragment your Windows drive before resizing it, so it may take a little while for Windows to "settle."

---

### Post by x33a on 2010-01-06
seems unlikely that you screwed up with a simple unmount.

first try running chkdsk in windows.

also, post the output of
```
sudo fdisk -l
df -h
```

---

### Post by mikewhatever on 2010-01-06
The partition has changed, since you resized it. That's why Windows wants to check it, and you should just let it have its way. That however has nothing to do with mounting it while running from cd, which x33a had covered earlier.

---

### Post by Qualia on 2010-01-06
Okay, x33a, here is my output to the command:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        4654    37335060    7  HPFS/NTFS
/dev/sda3            4655        9729    40764937+  83  Linux
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  497M   61M  436M  13% /
udev                  497M  268K  497M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  497M  100K  497M   1% /dev/shm
tmpfs                 497M   12K  497M   1% /tmp
none                  497M   88K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda2              36G   16G   20G  45% /media/1E2852C728529E19
/dev/sda3              39G  177M   37G   1% /media/9d74f252-9d63-41d7-9140-1e3b13b52887


(sda3 is an empty partiton in ext3, that I plan to use to install ubuntu on later, sda2 is nfts and is windows xp)

I can't really use chdsk right now, my Windows XP is infected by a nasty malware called Desktop Defender 2010 that has Winodws by the nads right now... (partly why I am choosing linux now!)

---

### Post by x33a on 2010-01-06
ok, you'll have to try command line now (don't be afraid :))

follow these steps to mount the partition using cli.

1. sudo mkdir /media/sda2
2. sudo mount -t ntfs /dev/sda2 /media/sda2
3. cd /media/sda2
4. ls -a

see if you can access the windows partition now.

---

### Post by Qualia on 2010-01-06
wait, I meant I can access and use the Windows partition, but because of the malware, I can't do much on it. But I can still access it and do some tasks, but with that malware, alot of basic tasks (word, mozilla, openoffice, etc) are not possible. But I can still read and write data on that partition. 

Do I still have to mount it? :/

---

### Post by Qualia on 2010-01-07
Well, I got it to work again! I just finsihed installing and have Ubuntu on my machine now!:D Thank you!

---

### Post by kekebay on 2010-01-07
just right click the partition in nautilus

---

