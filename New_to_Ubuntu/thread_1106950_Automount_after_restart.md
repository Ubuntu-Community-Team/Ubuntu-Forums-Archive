---
title: "Automount after restart?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-26
Hi,
Upon accessing my hard drives, or external devices, Ubuntu mounts them and I can use them.

However after I restart, they are not mounted, and all shortcuts to folders on that drive won't work until I click on the drive to make ubuntu mount it, then access the shortcut.


How can I make ubuntu remember what I want permanently mounted?

---

### Post by billgoldberg on 2009-03-26
Normally this involves editing fstab but I just read that there is a program called "pysdm" in the Ubuntu repositories that will do this.

I have no experience with it.

I suggest you download it

sudo apt-get install pysdm

or use synaptic and then open it (alt+f2 and enter pysdm) and set your preferences.

Let us know if it works.

---

### Post by Gp. on 2009-03-30
Ok well I installed it.
Now what?
If it's supposed to work automatically it didnt.:(

---

### Post by kanikilu on 2009-03-30
Here's a basic guide:

[http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

---

### Post by Gp. on 2009-04-02
It still won't mount one of my drives.

It's the drive I have Windows installed on (I dual boot)

and that's the drive that has my music on it so it's most important that it's mounted by itself.

All this mounting is annoying. If Ubuntu is aiming to be more user friendly for those coming from Windows, it should act more like Windows (Even if it isn't!) when it comes to mounting a drive automatically.

---

### Post by taurus on 2009-04-02
Which drive is it?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

p.s.  If you don't shut down your windows cleanly, Ubuntu won't mount it unless you use the force option.

---

### Post by egalvan on 2009-04-02
I used Synaptic to install ntfs-config...

I had the external drive connected when I installed ntfs-config,
and it automatically set up the drive...

---

