---
title: "Network trouble"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by toLa` on 2006-09-21
Hi guys,

After about a year of using (K)Ubuntu as my main OS with WinXP installed within a virtual machine in VMWare Workstation I formatted/re-installed my laptop (Fujitsu Siemens Amilo 1667G (AMD64 3700+, 1gb DDR 400, 80gb IDE, 128Mb ATi x700) with Ubuntu 6.06 (not for the first time), however after a few days of use, im having a few Internet/network problemos.

Last night after finishing work, I switched on my laptop, and when trying to access the Internet via Firefox, I couldn't access ANY web pages (including my router control panel webpage (even though I can ping the router)), so after enabling/disabling/rebooting a few times I still couldn't get anything.

So, I thought 'meh, may as well format/re-install', however, I had to back some data up, so I switched my laptop back on, and low and behold - Internet worked straight off.

After finishing work 2nite, I switched laptop on, and again, nothing, so I fired up XP within VMWare, and the Internet worked fine through Internet Explorer .... hmmmmm?

Turned off laptop after reading a few things on this forum using my Powerbook G4, and when I turned it back on the networking manager by the clock (GNOME) informed me there was no network, even after enabling/disabling eth0. Turned laptop off again and back on, and it worked again first time ... how annoying is this?

I'm quite happy to format/re-install, but if there is a quick fix then awesome. I've read a few things about editing host files, but the threads seem to get a bit sidetracked with arguments about IPv4/IPv6 syntax.

Cheers in advance, and apologies for the long post :D

---

### Post by spd106 on 2006-09-22
Are all of the problems related to Firefox? From reading your post it sounds like other that ff your connection is ok. Do you have any weird extensions installed? Have you tried another browser? Konqueror, Epiphany, Dillo, lynx etc.

---

### Post by acefreely on 2006-09-22
It could be just name resolution issues, especially if your VM works fine and your host doesn't.  Next time it happens verify if IP is working my pinging your gateway.  Most likely IP is working fine and you are having name resolution issues (/etc/resolv.conf).

---

### Post by toLa` on 2006-09-23
Hi,

Sorry for the delay in replying, got jumped by some scumbags in town so heads a bit all over the place...

Basically I have also got Opera browser installed on my machine, and that has the same problem.

Acefreely, could you elaborate a bit more on the problem? Pinging the gateway does work ok (192.168.0.1) but accessing it via the net to view its control panel doesn't :(

cheers for ur help guys

---

### Post by spd106 on 2006-09-23
If it's a DNS name resolution problem then you should still be able to access web pages via their ip address ie [http://212.58.224.114/](http://212.58.224.114/) brings up the bbc homepage, or [http://128.30.52.45](http://128.30.52.45) for w3c.org.

If this doesn't work could you try the router again with either **telnet 192.168.0.1 80**, then press enter or **w3m 192.168.0.1** (press q to exit) from a terminal. You should get at least some output from one of these or the router is having trouble with it's web server.

---

