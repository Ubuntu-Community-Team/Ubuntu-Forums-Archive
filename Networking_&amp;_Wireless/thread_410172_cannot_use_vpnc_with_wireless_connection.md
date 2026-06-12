---
title: "cannot use vpnc with wireless connection"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by jiasheng on 2007-04-15
I used to use vpnc to connect to the school's vpn server.  Everything worked fine in edgy, however, I got "vpnc-connect: no response from target" in feisty with the same config file.  I found that this only happens when I connect to internet through wifi.  If I use a wired network, vpnc works fine again.  Any ideas?

btw. I'm using feisty beta + bcm 1390 (ndiswrapper)

---

### Post by jiasheng on 2007-04-15
seems to be a bug of the newly included vpn-0.4 in feisty.
I tried the deb package for edgy which is vpn-0.33+svn xxxx
it did the job.

---

### Post by pickled on 2007-04-23
Thanks for the help I had the same problem.
I'm using the released version of feisty.
You can find the package here:[http://packages.debian.org/stable/net/vpnc](http://packages.debian.org/stable/net/vpnc)

---

### Post by idoerg on 2007-05-12
I am using Kubuntu 7.04 and I am experiencing the same problem.

I tried downgrading to vpnc 0.33 but that didn't help. vpnc keeps killing my wireless.

---

### Post by gatdammit on 2007-06-08
Hi I'm having the same problem.  I just installed VPNC.  how do I know which version I have?  If I have to install the older version do I have  uninstall this one?  Everytime I connect it says it's fine but then it kills my WiFi to the internet.  I'm new to this so any help or detailed explanation is greatly appreciated.

---

