---
title: "Cannot connect to internet from recovery mode"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by subtex on 2008-04-26
I'm having the same problem as the people in this thread: [http://ubuntuforums.org/showthread.php?t=765616&highlight=b43-phy0](http://ubuntuforums.org/showthread.php?t=765616&highlight=b43-phy0)

where my averatec 3200 laptop will never boot into X, it just gives the error looping forever.

So I went into recovery mode and tried to install b43-fwcutter off the hardy cd, but part of that install is downloading the correct firmware from the site.

I have my laptop wired via ethernet right now, but even a simple ping to any host fails.

the only thing that shows up when I do "ifconfig" is the "lo" local loopback.

From another thread someone had asked to see what was in /etc/network/interfaces.  I have:
```
auto lo
iface lo inet loopback
```

and

```
auto eth0
#iface eht0 inet dhcp
```

I also tried running ```
ifup eth0
``` as was suggested in another thread on how to get internet up in recivery mode, but when I do that I get the message ```
Ignoring unknown interface eth0=eth0.
```

Any help? :confused:

---

### Post by ogger on 2009-02-22
i have the same prob

---

### Post by Yashiro on 2009-02-22
Run
> sudo nano /etc/network/interfaces
Change
> #iface eht0 inet dhcp
to
> iface eth0 inet dhcp
Press Crtl+O to save. Then Ctrl+X to Quit.

---

### Post by ogger on 2009-02-23
Indeed. With this I got it working. Thanks. I also found this guide: [http://kubuntuforums.net/forums/inde...opic=3100052.0](http://kubuntuforums.net/forums/inde...opic=3100052.0)

---

