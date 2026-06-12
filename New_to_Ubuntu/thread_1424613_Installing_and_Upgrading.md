---
title: "Installing and Upgrading"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Leoq on 2010-03-08
So I have had this problem for a little bit. I posted in the installation section... but I belong here.

First, I'm running  Ubuntu 9.10 Karmic Koala from a 4GB usb stick. I can save, so its not like the live cd. I was able to download stuff before but recently I re-installed the ubuntu onto the usb and now I can't install anything nor can I upgrade. 

I tried.

Sudo apt-get update - that works fine
Sudo apt-get upgrade - does not work

It asks me to continue, and I press 'y' and then in pre configures packages then gives me a wack of errors. 

I have tried this in both root and user. I have also tried the 'fixes' in both of these posts [872210]("http://ubuntuforums.org/http//ubuntuforums.org/showthread.php?t=872210") and [389997]("http://ubuntuforums.org/archive/index.php/t-389997.html") and this has not worked. 

I am at a bit of a loss. 

heres the error message. 

dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: input/output error
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: input/output error
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': input/output error
E: sub-process /usr/bin/dpkg returned an error code (2)

And thats all... does anyone know because the normal fixes don't seem to work.

---

### Post by inobe on 2010-03-08
is synaptic or software center opened ?

if yes' close them and run the commands again

---

### Post by Leoq on 2010-03-08
No there not. Thats whats odd about this. Is is possible that theres a background process that is running and stopping my access?

---

### Post by zeroseven0183 on 2010-03-08
Can you do an **fsck** to your USB stick?

---

### Post by inobe on 2010-03-08
i can't remember exactly, in synaptic click file sor something and hit "fix broken packages"

other than that i re-read your initial post and wondering if you used the entire drive when installing or if you had a separate home partition or something ?


bad repositories would also causer this type of error.

---

### Post by Leoq on 2010-03-08
You'll have to explain what that is... Because I don't know... but I probably can I don't have anything saved on it yet.

---

### Post by Leoq on 2010-03-08
I partitioned so I could save... but I used universal usb installer for windows it did it all for me... :)

---

### Post by Leoq on 2010-03-08
I 'fixed' the broken packages and it told me that it was successful but the upgrade still didn't work. 

I feel like I might need to re-install ubuntu onto the usb?

---

### Post by Leoq on 2010-03-08
I did the fsck and it says that

fsck from util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  29:f8/08, 30:10/00, 31:09/00, 71:44/4e, 72:65/4f, 73:6c/20, 74:6c/4e
  , 75:4d/41, 76:44/4d, 77:33/45, 78:70/20, 79:6c/20, 80:61/20, 81:79/20
  Not automatically fixing this.
/dev/sda5: 5090 files, 197827/521984 clusters

Does this mean anything?

---

