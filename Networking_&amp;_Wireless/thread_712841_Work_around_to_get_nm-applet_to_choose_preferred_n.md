---
title: "Work around to get nm-applet to choose preferred network"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by beardiggin on 2008-03-02
I know this workaround works for the gnome desktop.  I am not sure about other flavors of Ubuntu.

Okay, this is really a work around until those in the Network Manager community give us a way of selecting a preferred network rather than choosing it for us.

go to  .gconf/system/networking/wireless/networks/

This folder contains a folder with the SSID name for every network you have ever connected to.
Delete every folder except the one(s) you use.

The next time your card tries to connect it will be to your network.

--edited--

Thanks for the note bluej744

---

### Post by buckeyered80 on 2008-03-02
Thanks Bear.  I'm going to give that a shot.  Because for some odd reason, after a few hours of inactivity, my kubuntu loses it's network settings.  It won't let me get them back again unless I reboot.  I had the same issue when I was using Ubuntu 7.10, but it never happens on my windows boot, same computer.  So, maybe that's it.  Maybe it's trying to connect to another network.  We'll see, good idea though!

---

### Post by beardiggin on 2008-03-03
Did it work for you?

---

### Post by buckeyered80 on 2008-03-07
No, it didn't.  I guess I didn't mention that mine is a wired network problem.  It's weird, because it only happens when the network is inactive.  Like, if I kept my system on for a few hours and had no internet apps. running, it will drop it's settings.  If I leave Kopete on, it won't.  So, for now, my solution is to keep some kind of internet application like Kopete running,and all is well.  Unless someone else has found a fix for this issue.

---

### Post by &amp;)ky#)^ on 2008-03-09
> **beardiggin said:**
> .gconfig/system/networking/wireless/networks/
Just a little correction.  It's **.gconf/system/networking/wireless/networks/**

Thanks for the great tip.

---

