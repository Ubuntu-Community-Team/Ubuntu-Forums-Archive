---
title: "DVD drive error"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by zach33 on 2010-11-07
OK, I am trying to burn things to a DVD-R but the problem is I cannot mount the disc to burn anything to it. I get this error when i try to mount the disc.

Unable to mount location

Error mounting: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


It might be the drive permissions, but if it is, I haven't figured out a way to change them. I am still fairly new but do know how to do some command line work.

---

### Post by SuaSwe on 2010-11-07
Did you try the dmesg command suggested in the error message? It will provide debugging info that might help diagnose the problem. If you're not sure how, just open Applications > Accessories > Terminal and type in:

```

sudo dmesg | tail 

```

Paste the output here if it's unclear to you. :)

---

### Post by zach33 on 2010-11-08
OK, here is the output.


[  239.608196] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.608198] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.608201] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.608204] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.608206] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.608209] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.608212] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  239.608214] 
[  239.608218] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
[  239.608222] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID

I have done this before but from this, I don't see anything that would suggest that there is an error with the DVD drive.But that is probably because the error has to do with mounting/permissions and not with if it actually works.

---

### Post by zach33 on 2010-11-09
Anyone else have any ideas?

---

### Post by SuaSwe on 2010-11-09
I'm out of ideas personally, and Google isn't of much help! How exactly are you going about mounting the drive? Have you tried mounting the drive using sudo, or gksu if you're using Nautilus (not that I think this should be necessary, but guess it doesn't hurt to try!)?

---

### Post by ezsit on 2010-11-09
Why are you trying to mount a DVD-R prior to burning? Burning can only be done to unmounted media. Once you mount a disc, you cannot burn to it. Also, if you attempt to mount a blank disc, the error you are getting seems normal. A blank disc will not have any formatting and hence it will be unmountable.

Also, any software you use to burn DVDs and CDs will automatically unmount a disc if you are doing multisession burning or re-writing to RW media.

---

### Post by Nightstrike2009 on 2010-11-10
Are you using Brasero?

I have had problems burning with Brasero and use K3b instead this sorted out my drive problems (mine wouldn't complete burning everytime i used it), brasero has problems with some DVD drives apparently.

K3b is a KDE project but it can still be installed in gnome and used as normal (I also use gnome)

Also if your not comfortable with terminal type (In terminal ironically):
> gksudo nautilus


WARNING: Be extremely careful what you do with this command it opens a GUI root access nautilus, as it has root permissions it can do a lot of damage if you delete or modify the wrong items, but its also handy to know and could make life easier for you. :-)

---

### Post by zach33 on 2010-11-10
Thank you guys for your help. It turns out it was a bad disc and for some reason I never thought to try a different disc.

---

