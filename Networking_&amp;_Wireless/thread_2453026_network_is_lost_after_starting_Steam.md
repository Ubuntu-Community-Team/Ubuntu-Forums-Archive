---
title: "network is lost after starting Steam"
date: 2020-11-02
forum: Networking &amp; Wireless
---

### Post by mastablasta on 2020-11-02
so we have a wired laptop that also uses rtl8821ce patched to kernel. when machine starts up both chips get connected and all works fine.

it was all working quite well until recently when i noticed that when starting up steam the internet connection is lost, though LAN is still there. when i check the network manager i can see there is some traffic going on both chips, but i can't reach any website.

one way i found out to solve it is to turn off the wi-fi, then i run ping [www.google.com]("http://www.google.com") in konsole. if all goes well it starts pinging and internet suddenly works. sometimes i need to do a reboot and internet work then. 

is this a modem/router issue? i just never saw this so i don't even know where to start. and i have no idea why suddenly only LAN would work. the network works OK on reboot so it is hard to say if anything is actually wrong on OS. also this issue doesn't always appear. sometimes Steam can be launched and connects normally as it always did in the past. but lately i saw it 4 times already.

Kubuntu 20.04
kernel patched with wi-fi driver
iommu=soft parameter added to be able to boot using battery power only.

---

### Post by mastablasta on 2020-11-02
one of the IP addresses taken by this laptop was assigned by static DHCP server to another mac address. i wonder if this could have caused the issues. i just saw the kid using steam for his daily hour with no issues at all.


[LIST]
[*]I wrote down the IP addresses,
[*]checked where they belong to,
[*]removed the inactive mac (e.g. old mobile phone we no longer use, old PC i gutted...),
[*]added active macs,
[*]corrected the offending mac and matched it with IP,
[/LIST]

hopefully this will resolve it.

i think i need to add one more mac & IP address and that is my personal netbooks wired connection.

i have DHCP set to assign IP to mac, but if none is assigned it would assign a random IP (e.g. if i had a family member visit and that i would give wifi access to).

---

### Post by mastablasta on 2020-11-10
it seems network is lost on other occasions as well. even when i use wired connections. static local IP works and is properly assigned.

i noticed strange things like:
[QUOTE][FONT=monospace][COLOR=#000000]ping [www.google.com]("http://www.google.com") [/COLOR]
ping: [www.google.com]("http://www.google.com"): Temporary failure in name resolution
[[/FONT]/QUOTE]

i unplug the cable & plug it back in, and it works as if nothing happened.

sometime she can play CS:GO online for over one hour and there are no issues. then turn it off, goes online on firefox, suddenly no connection. it'd rops and suddenly it is back on.

most disturbing -  clicking in learning site that the kid uses it says connecting to facebook.com, sending information to facebook.com and then just hangs. but there is no connection with facebook and this page, not even in any java scripts. he doesn't have a facebook account.

what is going on and how do i troubleshoot this?


cable connection is done from modem via switch to the PC.

---

