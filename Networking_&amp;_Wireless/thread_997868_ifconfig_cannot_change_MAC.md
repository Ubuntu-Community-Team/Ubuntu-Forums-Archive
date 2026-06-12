---
title: "ifconfig cannot change MAC"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by notgeekenough on 2008-11-30
I'm having trouble changing my mac address. I have two cards a b43 broadcom and a linksys USB WUSB54GC. When I try
```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:11:22:33:44:55

```
it does not work with either the b43 or the usb nic. After scanning the forums it sounded like maybe it was because the drivers did not support MAC address changing but then I tried macchanger:
```

sudo ifconfig eth0 down
sudo macchanger --mac=00:11:22:33:44:55 eth0

```
this works. Why cant I use ifconfig to do it?

---

