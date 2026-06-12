---
title: "GParted Problem"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by nnolund on 2009-11-13
I am trying to increase my partition size for Linux because I went with a minimal size when I installed ubuntu, just to get it up and running. My problem now is that I have no room to get anything installed. 

I was thinking about removing Windows completely, as I don't use it, but this isn't my laptop, so that would likely not be a good idea (I don't want to wipe away the data on here from the actual owner). So, I decided just to increase my partition size, as I still have some room in my HDD.

However, when I went into GParted to unmount the partition, it said I wasn't allowed to. 

I am likely doing something wrong, as Ive never used GParted before, but I have no idea how to increase my partition size.

---

### Post by coldReactive on 2009-11-13
No you aren't doing anything wrong. You can't unmount the system hdd, since you're using it.

---

### Post by sledge73 on 2009-11-13
Try using Gparted from the live cd not from the running os & that should work. I cant stress enough backup everything.

---

### Post by nnolund on 2009-11-13
Well that leads to another problem. My CD drive doesn't work, and I used wubi to install ubuntu on my laptop. 

Is there another way for me to resize my partition, or am I going to have to figure out how to get LiveCD on my USB thumbdrive?

---

### Post by Anarci on 2009-11-13
Ubuntu comes with a usb startup disc creator, you can use that to create a gparted startup usb drive

---

### Post by utnubuuser on 2009-11-13
uSB-startup disk creator

Get an .iso of ubuntu live or maybe even just gParted live, use Ubuntu's "USB-Creator" to make a bootable USB-stick.

---

### Post by louieb on 2009-11-13
> **nnolund said:**
> My CD drive doesn't work, and I used wubi to install ubuntu on my laptop. 

Gparted can't resize a WUBI (inside windows) install.
Use LVPM [WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

---

