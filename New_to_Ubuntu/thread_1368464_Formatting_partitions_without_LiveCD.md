---
title: "Formatting partitions without LiveCD"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by dustoashes on 2009-12-30
Hi,
I've just setup Ubuntu 9.10 on a computer that is running Win XP. I've used the installation process for installing from USB stick - but I didn't boot from USB, since I had a problem so I ended up running wubi.exe from the USB and it installed.

But now I want to format the space that's taken by Win XP. I know that it's possible by using GParted and LiveCD, but how is it if your CD isn't working or you don't have a CD drive? Is it possible to partition?

---

### Post by benfindlay on 2009-12-30
You can install gparted into your current ubuntu install either through synaptic or with terminal using ```
sudo apt-get install gparted
```Then you should be able to achieve what you are trying do.

---

### Post by Merk42 on 2009-12-30
I'm 99% sure that WUBI lives inside Windows.  Format Windows and you lose Ubuntu as well.

---

### Post by benfindlay on 2009-12-30
> **Merk42 said:**
> I'm 99% sure that WUBI lives inside Windows.  Format Windows and you lose Ubuntu as well.

Indeed, it looks like you are correct. It seems WUBI creates a hard drive container within a single file on the windows partition, that the computer treats as an actual hard disc partition. This means that a full blown reinstall will be required, unless WUBI itself has some kind of volume migration facility, or their website has instructions on this.

---

### Post by audiomick on 2009-12-30
As far as I know, a fresh install will be neccesary.

---

