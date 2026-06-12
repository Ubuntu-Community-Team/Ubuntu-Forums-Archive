---
title: "Static IP getting reset to dhcp intermittently"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by TCarr on 2007-11-30
We have Ubuntu Server 7.10 and we're losing our static IP address intermittently. Seems it keeps getting reset to dhcp even though the /etc/network/interfaces is set up as static. I can't seem to find out why.

Anyone have any idea where to look for problems and what can be done to fix it? Right now, every time we loose the static IP (which is like once a day), we have to initiate a /etc/init.d/networking restart to get the static IP working again.

---

### Post by TheWizzard on 2007-11-30
i'd check the router settings. 
do you have networkmanager installed? this can also mess up your connection.

---

### Post by TCarr on 2007-11-30
Thanks. we don't have the network manager installed, thankfully. Though I did pass on your advice to check router settings. I was wondering about that.

Another thing I found was the server was restarting every day at a certain time in the morning (exact same time each morning) and I couldn't find anything in the crontab that would trigger this. I think this is what is causing the reset of dhcp.

Though there seems to be a bug I don't know if this also applies to Ubuntu 7.10 or even 6.06.1 (which we're considering trying next).

Bug#406601: network: remote host disconnected for Debian 4 systems:
[http://lists.debian.org/debian-kernel/2007/01/msg00393.html](http://lists.debian.org/debian-kernel/2007/01/msg00393.html)

---

### Post by TheWizzard on 2007-12-01
this restarting is really odd. i'd check the logfiles if i were you.

---

### Post by TCarr on 2007-12-02
I did check the log files. It seems the connection just drops every day at that same time.

We reinstalled the server so I'll go see if that is still happening. I will see if another version was used on the new system. If it is still happening, I'll be at a loss as to why. I'll keep you posted.

---

### Post by TheWizzard on 2007-12-03
ok, good luck.

---

