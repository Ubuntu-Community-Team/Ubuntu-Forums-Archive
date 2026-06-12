---
title: "Chroot walkthrough"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by McTwitch on 2010-08-11
I've had this explained a couple of times, but I can't seem to remember how to. I spend a lot of my time on my Ubuntu 10.04 live disk, making changes to my Ubuntu External Hard drive. Can someone please explain a simple way for me to chroot into my Ubuntu External, so that I can run commands on it?

---

### Post by bodhi.zazen on 2010-08-11
The basics are 

```
sudo chroot /mount/point /bin/bash
```From there it depends on what you are doing with the chroot.

Other common commands are (run these in the chroot):

```
mount -t proc none /proc[FONT=monospace]
[/FONT]mount -t sysfs none /sys[FONT=monospace]
[/FONT]mount -t devpts none /dev/pts
```be sure to unmount the proc, sysfs, and devpts when you are done w/ the chroot, then exit eth chroot

```
exit
```

---

### Post by McTwitch on 2010-08-11
Alright, then what is SSH, and is it possible to SSH into the external hard drive from the Livedisk?

---

### Post by Ozymandias_117 on 2010-08-11
The system has to be running to SSH to it.

---

### Post by McTwitch on 2010-08-11
Oh, well thanks for clearing that up then. I'm going to mark this as solved.

---

### Post by bodhi.zazen on 2010-08-11
> **McTwitch said:**
> Alright, then what is SSH, and is it possible to SSH into the external hard drive from the Livedisk?

As indicated, you may ssh into the chroot.

Depending on what you are wanting to do, you may wish to look at OpenVZ or Linux Containers (AKA LXC). Linux containers are in rapid development, and Openvz requires an OpenVZ kernel ...

Both options have a bit of a learning curve, but may have some advantages for you.

---

