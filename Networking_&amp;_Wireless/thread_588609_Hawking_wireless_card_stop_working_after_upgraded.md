---
title: "Hawking wireless card stop working after upgraded"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by lorenzo111 on 2007-10-23
I just upgraded my ubuntu to 7.1 now my wireless card will not scan for networks anymore.
Have a hawking HWC54D had to use ndiswrapper to get it to work before. Tried duplicating the same steps again but will not work after upgrade. Shows my driver is installed but after that nothing. Any help would be appreciated. Any one else have problems since upgrade???

---

### Post by lorenzo111 on 2007-10-25
no suggestions??
I'm hurting

---

### Post by mpierce on 2007-10-25
I'm assuming your wireless card is eth1 but you can change for whatever it is a nd that it is getting its address from the router.
Try putting the following into /etc/networks/interaces:

iface eth1 inet dhcp
wireless-mode managed
wirelsess-essid: name of your router
wireless-key1 xxxxxxxxxxxxxxxxxxxx (your wep key)

My wireless router stores 4 keys so I use wireless-key1. You may have to use wireless-key.

Hope it helps...

---

### Post by lorenzo111 on 2007-10-25
nope didnt help would appreciate any other suggestions out there
something told me not to upgrade will think long and hard now for next time

---

