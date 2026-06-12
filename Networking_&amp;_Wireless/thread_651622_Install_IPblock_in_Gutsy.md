---
title: "Install IPblock in Gutsy?"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-12-27
I'm using Gutsy on a MacBook and am currently trying to install IPblock from [here]("http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html").
After making the propriate changes (feisty ->gutsy) in the packages to be installed, everything seemed to go fine as no error messages at all were received during the install.
However, although IPblock now appears in Applications>Internet, clicking on it does not cause the Protection/Lists/Settings box to open. In fact, absolutely nothing happens.
OK, so I tried to open IPblock from a terminal (with sudo and parameter -g to start IPblock GUI) and get this:
```
/usr/sbin/ipblock: 295: IPTABLES_LOG: parameter not set
```

Now the guide I used does say this:
> iplist requires a 2.6.14 kernel or later with the option CONFIG_NETFILTER_XT_TARGET_NFQUEUE enabled (module or build-in)
I will admit that I did not, and indeed don't know how to, do anything about the second of these requirements.

Can anybody help be get this straightened out?

Thanks
Paul

---

### Post by uljanow on 2007-12-27
Looks like you're using an old configuration file. Replacing the old one with the default  **/usr/share/doc/iplist/examples/ipblock.conf** should fix it.
```
sudo cp /usr/share/doc/iplist/examples/ipblock.conf /etc
```

---

### Post by PaulFXH on 2007-12-28
OK, thank you. That worked perfectly.
I tried to install IPblock a few days ago but got interupted which is presumably where the old ipblock.conf came from.
BTW, perhaps you could tell me whether there is, or indeed is not, any good reason to use Tor in conjunction with IPblock?
Thanks
Paul

---

