---
title: "Need a network bridge to connect xbox 360 live"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by groman88 on 2008-07-24
I have a wireless network and a laptop connected to it at home. In the past while using Windows Vista I could easily create a network bridge and connect my xbox 360 using a network cable so to share the connection with my laptop. 

Now I was wondering if i can do the same thing using ubuntu? How do i create a network bridge in ubuntu?

---

### Post by Endwin on 2008-07-24
A little console work and it is done.

Make sure you have the extra repositories, and install...

```
sudo aptitude install bridge-utils
```

Once installed edit **/etc/network/interfaces** as root

Remove references to other network interfaces for the ones you want to bridge.

Add in the bridge with those interfaces like this:

```
 auto br0
 iface br0 inet dhcp
       bridge_ports eth0 ath0

```

where eth0 is your wired and ath0 is your wireless interface.

---

