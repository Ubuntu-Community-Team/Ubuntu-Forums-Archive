---
title: "Grub 2  and boot times"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by candtalan on 2009-12-01
I have installed Ubuntu 9.10 and it is dual booting on a machine with earlier Ubuntu versions. I cannot help noticing that grub 2 (from the 9.10 install) takes a lot longer before it comes to display the menu.lst, in fact about twice as long, about 30 seconds whereas the earlier grub showed a menu in about 15 seconds.

Grub 2 just shows the text 'Grub loading' on an otherwise blank screen, which is rather boring as well as a bit frustrating, while awaiting the menu.

Is this particular to my machine in some way? Is it faster for other users?

---

### Post by QIII on 2009-12-01
Just a bit on terminology:  GRUB2 doesn't use menu.lst anymore...

Yes.  There is some discussion that GRUB2 is a bit slower.  It is a beta last I checked, thus it is a work in progress.

If you want to spice up the menu when it gets there, you can add a grub splash image.

---

### Post by ranch hand on 2009-12-01
This seems t obe hardware related.  On my box the time is about the same.

There is a lot of bad information out there about grub2 from people that have little (or no) experience with it.  Check the link in my sig.  It is simple.  The links in it, particularly the first 3, are in depth and excellent.

We all started playing with grub2 at the time of Karmic Alpha2 when grub2 was introduced, or in hermans case, earlier.

As QIII said, the /boot/grub/menu.lst is gone.  Your menu screen comes from /boot/grub/grub.cfg.

Everything is script driven and this, I believe, is the reason that on some boxes it is just slow.  We are using 1.97beta4.  There should be an update sometime fairly soon as 1.97 is out and Debian testing has a 1.97 package.

Some folks are using the Debian package.  I am not as I have grub2 pretty much sitting up and begging for me.

I do recommend playing with it.  It is what everyone is going to be using.  Grub 0.97 (grub-legacy) is no longer supported.

I do not know if it makes you any happier but grub-legacy had a kind of rough start when it came out.  It was about as popular as a turd in the punch bowl.

---

### Post by candtalan on 2009-12-01
Thanks for the responses, much appreciated. 
Ah, grub.cfg, ok thanks. 

I am lost in admiration of the developments. It is sometimes hard to keep up just as an interested user (and advocate).

I don't have a problem with the longer times, particlularly after the suggestion about future progress, which I half expected as a possibilty, but I have missed out on that discussion, so I began to wonder. 

I mainly had been aware of quoted objectives of making versions boot faster, which it/they may do (excepting grub2) and it is useful to have a clearer understanding.

---

### Post by oldfred on 2009-12-01
If you have a multidrive configuration and you boot from one drive but your install is on another it is a known bug, but there is a work around that helps. It worked for me.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

---

