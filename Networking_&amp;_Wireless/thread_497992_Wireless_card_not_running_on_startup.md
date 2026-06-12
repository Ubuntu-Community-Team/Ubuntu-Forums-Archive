---
title: "Wireless card not running on startup"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Onay on 2007-07-10
A quick question...

I am using a dwl-g132 wireless d-link card in ubuntu 7.04. I recently configured it to work in linux, but whenever I restart the computer or go into standby the internet is disconnected the wireless card disappears from the network settings. Even when I rerun my commands to get it working, it doesn't show up. 

Is there any way that I can get the wireless card to always work at startup without my manual commands? How can I set up a script that runs at startup that mimics the ones that I do normally? I use ndiswrapper on startup as well, so will that affect what time I execute this script? Any help would be much appreciated.

---

### Post by Onay on 2007-07-10
Bump, still haven't figured it out. What filetype is a shell? .sh?

---

### Post by #Reistlehr- on 2007-07-17
cat your /etc/network/interfaces and /etc/iftab files, post the outcome

---

### Post by Onay on 2007-07-23
cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

--------------------------------------------------------

cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0d:60:20:9d:15 arp 1

---

### Post by sunexplodes on 2007-08-09
Yeah, I've had the same device since Dapper, and this problem's always been the case. If you leave it unplugged until you hit the GDM login, then plug it in, it works like a charm. That's the only workaround i've ever been able to find.

---

