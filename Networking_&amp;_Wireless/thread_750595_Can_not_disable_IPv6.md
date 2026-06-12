---
title: "Can not disable IPv6?"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by matty4467 on 2008-04-09
i have try the three following things to disable IPv6 but none have worked:
Changing the /etc/modprobe.d/aliases file.
blacklisting IPv6.
And the last post on this thread [http://ubuntuforums.org/showthread.php?t=19206](http://ubuntuforums.org/showthread.php?t=19206) 
Please please help?
could anyone recommend any other way of disabling IPv6?
thanks in advance.

---

### Post by stream303 on 2008-04-12
Let's change the file which we do the blacklist from:
[B]
/etc/modprobe.d/blacklist[/B]

In the "blacklist" file, just add "blacklist ipv6"  .  Note that there is no hyphen and don't use quotes in the file.
```
sudo nano -w /etc/modprobe.d/blacklist
```

or for a graphical way:
```
gksudo gedit /etc/modprobe.d/blacklist
```

Put
```
blacklist ipv6
```
at the end, save file,  and restart networking, or reboot.

---

### Post by matty4467 on 2008-04-14
thanks for trying but no, didn't work. this is my 2nd time trying this and still nothing? please help?

---

### Post by kevdog on 2008-04-14
Try this:
**[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)**

---

