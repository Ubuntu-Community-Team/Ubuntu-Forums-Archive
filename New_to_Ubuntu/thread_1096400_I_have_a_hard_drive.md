---
title: "I have a hard drive"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-03-14
with Ubuntu 8.10 already loaded.  It is 80 Gig, in an E Machine  T2984, and I want to put it in a HP Pavillion a1125c.  Do I have to wipe it or can I just install and boot up?

---

### Post by bumanie on 2009-03-14
I have read that ubuntu should auto-detect the different architecture and load drivers etc accordingly, but I don't have personal experience trying this, so can't be 100% certain.

---

### Post by SuperSonic4 on 2009-03-14
You should be able to install and boot up as though it was on the T2984

---

### Post by abn91c on 2009-03-14
you probably run into video card issues if they are totally different cards, like ATI vs Nvdia or intel
Post the Specs of both systems, you will get better advice then

---

### Post by Iowan on 2009-03-14
If you're committed to a re-install anyway, try it... If it doesn't work, you *should* still be able to reformat/install via boot CD.

---

### Post by RetchingRabbit on 2009-03-14
> **Yed Ied said:**
> with Ubuntu 8.10 already loaded.  It is 80 Gig, in an E Machine  T2984, and I want to put it in a HP Pavillion a1125c.  Do I have to wipe it or can I just install and boot up?

You can probably just boot up. As previously noted, you may have video issues that prevent using the GUI, but the actual operating system almost always works across different machines, unlike Windows.

---

### Post by steve101101 on 2009-03-14
different video cards will be a slight issue but can be fixed once you boot.

---

### Post by Yed Ied on 2009-03-15
I just opened the HP and saw that when my ex tech guy replaced my old HD, he installed a SATA 180 Gig, replacing the old Pata ribbon.  No connector available.  Should I acquire a SATA 80 Gig to install?  Looking for Options.
Don't get me wrong I like my new HD, and think better about my ex now.  If I do this, there is 4 connections for this purpose red, yellow, black, and white, he installed in the black, should there be a preference here?

---

### Post by theozzlives on 2009-03-15
Just buy a new cable.

---

### Post by Yed Ied on 2009-03-15
Much Thanks.

---

### Post by ugm6hr on 2009-03-15
> **Yed Ied said:**
> Do I have to wipe it or can I just install and boot up?

When you install it (with a correct cable), just boot into recovery mode:
```
dpkg-reconfigure -phigh xserver-xorg
```

Then reboot again.

That should sort out the video driver issues.

If you have blacklisted necessary drivers for your new computer, you'll need to edit them again in /etc/modprobe.d/blacklist.  Same with /etc/modules (if you have manually added anything there).

---

