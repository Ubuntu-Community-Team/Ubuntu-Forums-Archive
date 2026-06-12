---
title: "resolv.conf keeps changing"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by suRoot on 2007-03-13
I'm not a networking newbie.  I do this stuff for a living, but this kind of has me :mad:.

I'm running a DHCP server here at home on my cisco Catalyst switch.  I know for a fact that the DHCP server is properly configured, as I've been using it for years. It's set to hand out a DNS server address of 192.168.12.3 (my internal DNS server).

What I've found is that after booting up & grabbing an IP, name resolution works properly for a period of time (varies - but generally start seeing the problem every 5 - 10 mins).  After booting or restarting networking (/etc/init.d/network restart) /etc/resolv.conf shows:

```
nameserver 192.168.12.3
```

which is correct.

However... eventually name resolution dies & a look at /etc/resolv.conf shows:

```

nameserver 192.168.12.101
nameserver 192.168.12.101

```

...which begs the question...  WTF is changing resolv.conf???

192.168.12.101 is a dead address.  I have nothing on that address & nothing has leased it.

I'm using the network manager applet, & I have a wireless card in the notebook (although I'm not connecting to a wireless network).  I suspect one of the two is to blame, but why or how I'm not sure.  Funny thing is that I use the exact setup at work (wired & wireless both enabled) & never see this happen.

Any ideas or suggestions?

---

### Post by lloyd_b on 2007-03-13
Could your wireless card be connecting to a neighbor's wireless router?  Just an idea.  Try disabling the wireless interface and see if the problem recurs.

Lloyd B.

---

### Post by Nikron on 2007-03-13
Some process run "resolvconf" which is resolving your nameserver wrong.  As it does to me too..  I'm trying to figure out how to fix it..

Okay figured out a quick fix, probably not the actual fix...   I'm on a server that I'm trying to configure a static IP, by the way.

I edited the following text file, and put in my name server... 

/etc/resolvconf/resolv.conf.d/base

---

