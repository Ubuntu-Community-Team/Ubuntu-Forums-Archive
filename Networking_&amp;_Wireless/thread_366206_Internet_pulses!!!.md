---
title: "Internet pulses?!?!?!"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2007-02-20
My internet is suddenly playing up. The only thing thats changed was a day or so ago, i thought i hadnt done my updates so did. There was about 80 of them.

The pc seems to be playing up now where it was great before. The internet is connected fine one minute and not the next. My windows pc on the same hub is fine. Looking at the network history in systemmonitor, its totally flatlining for ages then gets a large spike, th internet workd for a while then flatlines again. 

latest updates must have changed something, how can i roll back?

edit: One thing to add, my lan traffic seems fine, no problems at all, so its not my card playing up.

---

### Post by gradedcheese on 2007-02-20
> 
latest updates must have changed something, how can i roll back?


Try booting into the previous kernel (ie: the second-to-newest).  To do that, reboot and right after the BIOS screen press ESC to get to the grub menu, choose the kernel there and proceed to booting up.  If that works for you, then you can change the default kernel by editing /boot/grub/menu.lst

---

### Post by dgrafix on 2007-02-21
Tried that today, so it appears its not the updates after all.

It is weird though, on my windows machine x.x.1.3 i can ping both x.x.1.1 and x.x.1.2 (ubuntu) fine. And browse the internet smoothly.

However on x.x.1.2 my ububtu machine if i ping the router at x.x.1.1 i get periodic hits and it returns something like 70-90% packet loss. However, if i ping my windows machine x.x.1.3 its fine!!! All local net traffic is normal too. 

Its as if the router (which was fine 2 days ago) has suddenly decided not to talk to ububtu.

Ive tried switching ports cables etc.

If i bypass the router ubuntu works fine.

---

### Post by gradedcheese on 2007-02-21
just to be sure: you don't have more than one interface up (on the Ubuntu PC), all on the same subnet?

---

### Post by dgrafix on 2007-02-21
Just the one interface, although, looking in the router status, i seem to get "--" as my device name?!? it sometimes is linuxopc which is my computer name.

 Could this be causing the problem?

Why isnt my pc name appearing in the list?

BTW, whats the lin equivalent of ipconfig command?

---

### Post by gradedcheese on 2007-02-21
The PC name is probably looking for a Netbios (Windows) name, so that's ok.

ipconfig is "ifconfig", a much more sophisticated tool.  There's also "iwconfig" for the WiFi side of things.  Examples:

ifconfig
(list info about all interfaces)

ifconfig eth0
(just eth0 interface)

sudo ifconfig eth0 192.168.1.12
(assign a static IP)

Run "man ifconfig" for more information.

---

### Post by dgrafix on 2007-02-21
Kind of solved it... Bit of a botch though :/

I think ubuntu isnt broadcasting the devicename properly or the router isnt detecting it right. One minute the name is right and the next its just '--' the pings stop flowing when the device name is '--'

What ive done now is replace the offending netgear wgr614v6 with my old non wireless di-604 router(which works great with ubuntu) as the main gateway/firewall. Then disabled dhcp, firewall etc. on the other one and set it to x,x,1,2 now im just using it as a wireless hub (for my wireless win lapptop) with just a port (the wan port is empty) connected to the di604. 

This seems to work fine, however i have lost DHCP but wasnt a fan of it anyway.

Weird thing was everything was fine a few days ago and i havent done any system mods :confused:

---

