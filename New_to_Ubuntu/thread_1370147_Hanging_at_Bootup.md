---
title: "Hanging at Bootup"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by cloystreng on 2010-01-01
I installed Ubuntu 9.10 in addition to Windows7 this morning and proceeded to somehow mess it up. Last thing I did was try to install a driver, I believe for Broadcom, which I think is my wireless card, but I am not sure. I couldn't tell you exactly what it was that I did. However, the computer froze and I was forced to manually shut down. 

When I start up the computer in normal Ubuntu, it goes black where it would normally show the login screen. I have waited for 10 minutes and nothing happened. Windows7 still runs fine thankfully.

I can run recovery mode fine, but I have no idea what to do, and researching into the problem only confuses me. 

Any help would be appreciated.

EDIT:

I know what happened now, but still not how to fix it. When I tried to download and install a certain Broadcom driver (STA something), the computer froze and the caps lock key started blinking. I pressed ctrl alt F1 and  alt F2 because I heard that might do something but no luck.

---

### Post by Max_Mackie on 2010-01-01
Give this a try.
Try (from GRUB) selected the recovery shell.

```
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure gnome-session
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
```

This is my standard way of preceding when I can't boot into an existing user.

---

### Post by cloystreng on 2010-01-02
I will give this a try, thanks. Afterward, is this expected to allow me to now run normal mode without problems or is this just a diagnostic tool?

---

### Post by drs305 on 2010-01-02
> **cloystreng said:**
> I will give this a try, thanks. Afterward, is this expected to allow me to now run normal mode without problems or is this just a diagnostic tool?

The commands given by Max_Mackie in the previous post would reconfigure the settings. If it works that should be the end of it.

By the way, welcome to the Ubuntu forums.  :-)

---

### Post by cloystreng on 2010-01-02
Nope, no such luck. They all seemed to work except the gnome-desktop-data....oh wait, I had written that down as gnome-desktop-date...could that have been an issue. 

Anyway, I gave  that a try and it did not work when I tried normal mode. I will do the gnome-desktop-data command again and maybe that will work.


EDIT:

I tried again, and the new, correct command did not do help (although the command itself worked this time). The computer still hangs at startup. 


Here is my new idea. I know that this isn't ideal, but since I still have the disc, how can I re-install ubuntu over my previous version while keeping partitions as they are? If I do it the recommeneded way by the disk, then I will have 2 versions of ubuntu 9.10 and one windows 7 on my harddrive which is dumb.

Basically, if I do the 'set your own partition size', and just delete the old ubuntu partition, how can I make it so that the new time I install it, it just uses that partition. Also, what settings do I need for the partition if I set it myself.

---

### Post by charlier653 on 2010-01-02
I may be a little different, in the fact that I have several drives on my desktop box.

What I did was to put my /home on a separate drive.

I have had to reinstall 9.10 a couple of times due to my own messing with the wrong thing. By having my /home on a separate drive all my settings etc are preserved. I would assume that this would work on multiple partitions on the same drive, however, YMMV.

If you do it this way, be sure to write down the partition order, and just repeat the install in the exact same way, making sure to set your root, /home and all the same way. that way only the actual OS partition gets overwritten.

Good luck!

---

### Post by cloystreng on 2010-01-04
Thanks for the info. I will try this out and see if I can manage to do it.

---

