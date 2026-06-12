---
title: "Repair USB installation"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Peter W on 2011-07-15
I have installed Ubuntu 10.10 on USB drive and have been happily running it daily for over one month.

Suddenly I got the problem that after booting regularly the OS hangs the moment when the desktop appears.... so I suppose something got corrupted on the USB.

Is there a way to "Repair" the USB installation preserving the data on the drive?
There are many filed I downloaded and are on the USB, and also the Firefox bookmarks I would like to save.

Eventually, how to recover the downloaded files from the USB drive?

---

### Post by frankbooth on 2011-07-15
Have you tied booting into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode")?

---

### Post by C.S.Cameron on 2011-07-15
Is it a persistent, (Live) install or a Full install.
If a persistent install, is your casper-rw file full?

You can mount it to delete or recover files

```
sudo mkdir /media/casper
```

```
sudo mount -o loop casper-rw /media/casper/
```

---

### Post by Peter W on 2011-07-16
Unfortunately there isn't any "recovery mode" at boot. At boot the screen shows:

Installer boot menu:
-Run Ubuntu from this USB
-Install Ubuntu on Hard Disk
-Test Memory
-Boot from first hard disk
-Advanced options >     (empty!)
-Help

The installation is "persistent".

Mounting the USB drive on another Linux PC there is CASPER folder as well as CASPER-RW file on it.

Cameron, I am now figuring out now how to mount the casper-rw file using your codes... but until now I could not make it  :(

What do you mean by the casper-rw file being full?

---

### Post by Peter W on 2011-07-16
Yeah! Finally I applied my brain a littel bit and I managed to mount casper-rw.

I just had to add

cd /media/UBUNTU1010/

between the 2 above mentioned codes given by Cameron... yes I am an absolute beginner and most of things might be obvious but not for me. 

Does anyone know where to find the Firefox bookmarks?

---

### Post by C.S.Cameron on 2011-07-16
> **Peter W said:**
> 

What do you mean by the casper-rw file being full?

When the casper-rw file gets full of persistent stuff the drive stops working.

---

