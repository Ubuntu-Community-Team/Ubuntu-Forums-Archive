---
title: "Network settings - why need for reset?"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by xadder on 2008-06-29
There are two annoying things with network usage: 

I am using a notebook (IBM T43) with cable broadband/DHCP, mainly without problems. However, the first attempt to reach the net frequently doesn't work. I them have to open System/Network Settings, unlock it with the root password), then delete old IP numbers, and click "Wired connection" box on and off, sometimes a few times. It all seems quite random, takes time, and shouldn't I be able to connect to the network without superuser access being required each time. 

Is there any way I can just have the system start afresh each time, so I don't need to delete old numbers and restart (or whatever the box does)?

I notice also that it is almost impossible to get rid of older settings for wireless. I was at a conference last week and hooked up to their wireless. Now NetWork Settings has a tick against the wireless box, which I can't get rid of! Irritating.

---

### Post by bobyy on 2008-06-29
Hy there ...
for the wired connection ..
just run in console when you are trouble:
$sudo dhclient eth0 

another way to force reload the network is to run

$sudo /etc/init.d/network force-reload

for the wirelles y am working with WICD because network manager is buggy for some network cards(for use WICD you must unninstall network manager)

---

### Post by xadder on 2008-06-29
Many thanks. I've saved that info away for the next time I hit trouble - likely the next time I try to connect.

Sees strange to me that such a routine thing should need command-line work. Still not ready for the grandparents, unfortunately! (I have nothing against the command line, that's where I do most of my work, but I would really like networking to "just work").

---

### Post by xadder on 2008-06-29
Hi Bobbym

Just reporting back. I've used your first command a few times today and it works like a charm. Life just got much easier :-)

---

### Post by Gomezie on 2008-07-09
Hi.. I am having the exact same issue, but with a static IP setting.. is there any way to force this setting, as above?

Cheers

---

