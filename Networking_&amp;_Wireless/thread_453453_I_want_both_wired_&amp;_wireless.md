---
title: "I want both wired &amp; wireless"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by zacktu on 2007-05-24
I installed 7.04 as a new install on a laptop that requires adapters for both wired and wireless networking.  

I've done two installs.  The first install was with the wired network adapter plugged in during the installation.  I had wired networking, but if I changed to the wireless adapter, I couldn't access the network.  I did another install with the wireless adapter plugged in during installation.  Now I had wireless access, but if I changed to the wired adapter, I couldn't access the network.  In each case the adapter that was plugged in during the install was seen as eth0, and the other adapter was seen as eth1.  The wireless adapter could have had another name (wlan0? wifi0? -- don't remember).

I don't see how this could be a driver issue because whichever adapter is present during the installation works okay.

It's physically impossible to have both adapters plugged in during an installation because the wired network adapter is double height.

I've tried to set properties of the "alternate" adapter manually.  I must not be doing enough.  What's needed here?

Thanks.

Zack

---

### Post by blazercist on 2007-05-24
it probably didnt work because if u switch adapters the other adapter has to be downed manually: sudo ifconfig wlan0 down or sudo ifdown wlan0, then and only then can you dhcp the other adapter with sudo dhclient eth0

good luck.

---

### Post by zacktu on 2007-05-24
This was half of what I needed.  The dhclient command didn't work.

I discovered that /etc/iftab didn't have both mac addresses.  I added the second mac address, so that I now have

eth0 mac yy:yy:yy:yy:yy:yy arp 1
wlan0 mac yy:yy:yy:yy:yy:yy arp 1

in /etc/iftab.  Now, I can use

sudo ifconfig eth0 down
sudo dhclient wlan0

and

sudo ifconfig wlan0 down
sudo dhclient eth0

to switch between adapters.

Thanks very much!

Zack

---

