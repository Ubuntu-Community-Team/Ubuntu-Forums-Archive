---
title: "WIRED issue on Dell Insprion B120"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by CodeDragon on 2008-07-12
So many problems with the wireless (stupid Broadcom chips), and I'm the one who ended up with trouble on the wired side...  :P

Anywho, I have Ubuntu 8.04 Server installed on an old Dell Inspiron B120 laptop.  I did that to find a use for it as its screen went bad (I have two of the same model purchased at the same time who both went bad at about the same time).  I'm intending to pretty nearly exclusively use SSH once the machine is ready.

However, it's not getting a network address through the ethernet adapter.  I know the cable is good, and the router works fine, but the to-be server doesn't seem to know it's connected.

I ran lspci and this is the line pertaining to the ethernet:
> 02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100BASE-TX (rev 02)
(I didn't want to type everything there, since I can't copy/paste, but that line is exact)

I noticed that the wireless is also a Broadcom chip, but wireless on the server is unimportant.

Any help would be greatly appreciated.  Thank you in advance.

---

### Post by nixscripter on 2008-07-13
First, see if you have the Broadcomm driver running: ```
lshw -C network
``` It should show up in the list. Figure out what the logical interface name is. If it's not in the list, it's a driver problem.

Second, see what the configuration is of that interface. Let's suppose it's eth0 (which is most likely). If it's eth0, then try: ```
ifconfig **eth0**
``` See if it has an IP, and that it is UP (should be on the first line). If there is no IP, try assigning it a manual IP and see if that fixes it: ```
sudo ifconfig **eth0 static.ip.addr.here**
```

Third, check on the routing table: ```
route
``` There should be an entry for your subnet and a default entry. Assuming your router hands out IP addresses on the network 192.168.1.0 there should be a **192.168.1.0** line and a **default** line with the IP of the router in it. Both should specify interface eth0. If it's not, it's probably a routing problem; try: ```
sudo route add default gw **ip.of.router.here** 
``` See if that fixes it.

Good luck.

---

