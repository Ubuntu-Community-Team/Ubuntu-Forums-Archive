---
title: "Internet: slow or no connection"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Robert Leithe on 2007-03-30
I have to computers connected to the same router. One Windows XP and one Ubuntu 6.10.
The Windows computer is not experiencinig any networking problems at all.

My Ubuntu machine however, has a slow connection or no connection at all to the internett.

Both computers receive their DHCP address, and function as such. But on my Ubuntu box I experience these symptoms:

1) Using KTorrent, my downloads are stalled
2) GAIM won't connect, or takes a looong time to do so
3) When retrieving my e-mail in Thunderbird it takes a looong time to connect, if it doesn't time out
4) Surfing the web with Firefox can be somewhat trying. Pages apparently load (judging from the messages on the statusbar) but the tabs show up blank. Or they can load normally and wait for me to follow a link before deciding not to comply (that is loading the link simply stops and I would have to click it again).

When I go to System|Administration|Firestarter and start this program, and then click "Stop" to shut down the firewall everything seems to function nicely. But for a period of time only. If I leave the machine on over night and continue my work the next day the problems (slow or no connection) is back. I reboot the computer, start Firestarter and shut it down and I'm back in business.

Being somewhat of a Linux newbie I am hoping someone can help me resolving this.

Sincerely

---

### Post by handaxe on 2007-03-30
There is a scattering of users who report such problems - either uniformly slow connects or connects that  degrade.

Usual recommendations are disabling ipv6 within Firefox AND Ubuntu (search the forums for instructions)

and using the Open DNS servers (again search the forums).

If those do not work, then it probably has no magic bullet fix but there are those better informed than me.

Good luck,

HA

---

### Post by Robert Leithe on 2007-03-30
I found some threads about disabling IPv6 and followed up on them. After doing so and rebooted I'm still having problems. Only worse than before.
Now neither KTorrent, GAIM or Thunderbird seems to connect. Only Firefox, but as before - several addresses I'm trying to visit turns up either blank or times out.

**EDIT: After another couple of reboots I appear to be back where I started. That is slow or now internet connection and a few blank pages in Firefox.**

---

### Post by teaker1s on 2007-03-30
stick ubuntu on static dns and insert your isp dns or
dhcp
[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns]("http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns")

---

### Post by handaxe on 2007-03-30
One sees strange things every now and then - like users struggling with wireless cards that elsewhere are smooth custard on ubuntu.  So, if possible borrow an usb or pci wireless device known to be compatible with linux and try that.  If it is good then you know it is a "card" quirk.

A PITA I know, but your type of trouble is tricky, if the forums are anything to go bu..

HA

PS If you have a laptop and try an usb device, remember to blacklist the driver of the internal wireless device

---

### Post by Mr. C. on 2007-03-30
There are three causes for what you are experiencing; make the changes below in order, leaving them changed until you obtain satisfactory performance:

1) Disable IPv6 completely : [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

2) Use your ISP's DNS servers, or OpenDNS.  Change nameserver line(s) in /etc/resolv.conf; you can have from 1 to 3 nameserver lines, place the fastest, most reliable one first.

3) Review and enable workarounds suggested here:
  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435)
  [http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/)
  [http://marc.info/?l=postfix-users&m=115739945701551](http://marc.info/?l=postfix-users&m=115739945701551)

MrC

---

### Post by handaxe on 2007-03-30
Thanks Mr C, 

Reading that lot was informative (and depressing).

What is Microsofts solution? (out of interest)

HA

---

### Post by Mr. C. on 2007-03-30
I'm not sure how it is being handled by Windows.  We can presume that they do not use the same mechanism or configuration as enabled in the 2.6.17 kernel.

MrC

---

### Post by handaxe on 2007-03-30
Indeed they would not...  I was referring to the stand in principle taken by Linux re stuffed routers. M'soft would simply not do that I bet.

HA

---

### Post by Mr. C. on 2007-03-30
Ah, I see.  You're right.  And Ubuntu took the stance to enable IPv6 for users, and this has caused all sorts of grief.  Still, it has to start somewhere, sometime, but perhaps in a more announced and supported manner.

MrC

---

### Post by handaxe on 2007-03-30
> **Mr. C. said:**
> ..... but perhaps in a more announced and supported manner.

MrC

Amen to that.

For Wondoze migrators, Linux is a bit like sending out someone with a long-term familiarity with automatic transmissions in a manual vehicle. Hilarious for everyone but the driver and those in the immediate vicinity.

---

### Post by InTheFlow on 2007-03-30
> **Mr. C. said:**
> There are three causes for what you are experiencing; make the changes below in order, leaving them changed until you obtain satisfactory performance:MrC

MrC...thanks so much for posting this. I was having the same issue and almost ready to go back to windows but your tip (and links) saved me! :guitar:

---

### Post by Ender Black on 2007-04-07
yep... another thanks to MrC.  It was editing the resolv.conf file that corrected the problem for me.  Thanks!

---

