---
title: "webpages loading slowly or not at all"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by treesurf on 2008-10-15
Howdy all,

I'm staying in a hotel in Hong Kong for the next month and I'm connected to their wired broadband connection.  Unfortunately, this connection has some issues.  

First of all I should say that when I use my Windows partition the internet flies along at a normal pace.  However when using Ubuntu many webpages load either very slowly, or not at all.  Typically Firefox will get stuck "transferring data" forever.  Other pages are fine, for example this forum.  Also downloading updates from the local Ubuntu ftp mirror blazes at 9MB/s so I know that good speed is possible from this connection.

I have already tried disabling ipv6 everywhere possible, and using OpenDNS, but have had no improvement so far.  I have also tried some other Linux distros that don't use Network Manager to see if that is the problem but it's still the same.  It is especially frustrating because I have to boot into Windows to get to some websites for work and that really slows me down (or go the local Starbucks and use their wireless which works just fine).

If anyone has any suggestions on how to go about diagnosing this problem I'd appreciate it.  I figure if Windows can deal with this internet connection then Linux should be able to as well, but I just don't know much about networking at all, so hopefully one of you masters out there can give me a hand!

thanks

---

### Post by treesurf on 2008-10-15
bump :)

---

### Post by superprash2003 on 2008-10-15
try changing MTU values.. may work [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by treesurf on 2008-10-15
Thanks.

I tried to follow that tutorial but my /etc/network/interfaces only has the following two lines:

auto lo
iface lo inet loopback

So I'm not sure how to follow his directions.  Should I add "iface eth0 inet dhcp" and then add the mtu value that he suggests below that?

---

### Post by superprash2003 on 2008-10-16
right.. if you are getting an ip from your router via dhcp .. then yes..

---

