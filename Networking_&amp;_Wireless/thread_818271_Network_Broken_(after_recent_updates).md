---
title: "Network Broken (after recent updates)"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Creap on 2008-06-04
The other day I installed the latest updates from the Update Manager. I believe, but ain't a 100% sure, it was after that my network suddenly stopped working. I tried using another NIC, in case the first one broke, but that didn't help.

When using the network in "roaming mode", I get no ip address at all, when changing to DHCP I get an "eth2:avahi" with a 169.. ip. ifconfig returns "UP BROADCAST MULTICAST  MTU:1500 Metric:1" etc etc.

I am posting this with my girlfriends laptop, so there's obviously nothing wrong with our router or modem.

plz help ;(

---

### Post by erlyrisa on 2008-07-08
I have the same problem

---

### Post by tcpip4lyfe on 2008-07-08
open up a console and:

sudo /etc/init.d/networking restart 

and post the output.

Also do a:
sudo nano /etc/network/interfaces

and make sure you have:

auto eth(?)
iface eth(?) inet dhcp

where eth(?) is the name of the iface you want to pull your dhcp from.  (eth0, eth1, etc...)

---

### Post by tinee on 2008-07-08
my wireless was working fine until i updated this morning and now i cant connect online but i can get on when its wired.. i tried doing what you said but it didnt work

---

### Post by chuckbert on 2008-07-30
Did you manage to solve this?

---

### Post by saxophin on 2008-08-01
I have the same problem. Before the update I could see my Windows machines though not their shares. (I could access their shares using Firefox).  Now I get as far as Windows Network but clicking on that shows nothing.
(Later)Having manually re-enabled wireless connection, i can now see the machines but still no shares visible.  Windows can see my Linux shares.

---

### Post by Zeike on 2008-08-01
> **tinee said:**
> my wireless was working fine until i updated this morning and now i cant connect online but i can get on when its wired.. i tried doing what you said but it didnt work

Same here, wireless borked but wired fine.

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

Linux jardine-laptop 2.6.24-20-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux


BOOTING WITH AN OLDER KERNEL VERSION FIXED IT.

---

### Post by maxomai on 2009-03-22
Sorry, wrong thread. Please ignore.

---

