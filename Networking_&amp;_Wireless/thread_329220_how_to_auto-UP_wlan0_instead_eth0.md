---
title: "how to auto-UP wlan0 instead eth0"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by aDOT on 2007-01-01
Dear friend,
1.how to config Ubuntu610 to auto-mount wlan0 after rebooting.
2. when I do > sudo /etc/init.d/networking restart:
 - wlan0 loses preferences of Access Point and 
 - "route" loses default DNS (that was Access Point 192.168.1.1) 

What do I need to do to avoid these issues? :confused: 

regards,
A.

---

### Post by evilghost on 2007-01-01
Modify /etc/network/interfaces and add "auto wlan0" and disable the "auto eth0".

---

### Post by jblebrun on 2007-01-02
> **aDOT said:**
> Dear friend,
1.how to config Ubuntu610 to auto-mount wlan0 after rebooting.
2. when I do > sudo /etc/init.d/networking restart:
 - wlan0 loses preferences of Access Point and 
 - "route" loses default DNS (that was Access Point 192.168.1.1) 

What do I need to do to avoid these issues? :confused: 

regards,
A.

Since you're using a wireless interface, I'd recommend trying network-manager and either network-manager-gnome or knetworkmanager. This will make the detection and connection to wireless access points much easier. It's still of a bit of a pain, but I find it easier than dicking around in /etc/network/interfaces and /etc/wireless. It'll manage your connection to wired lines, too.

Two caveats... currently, you can't bring up both interfaces simultaneously, and it doesn't have any options for static interface configuration, afaik.

---

### Post by aDOT on 2007-01-02
I have below interface description

```
root@andrew-laptop:/home/andrew# more /etc/network/interfaces
#auto lo

#iface lo inet loopback

#auto eth0
#iface eth0 inet static
#address 192.168.1.122
#netmask 255.255.255.0
#gateway 192.168.1.1

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.1.123
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid myField
wireless-key 1010101010
```

But, I have to do next after every rooting to connnet to internet
```
sudo ifconfig eth0 down
sudo ifconfig wlan0 up
sudo route add default gw 192.168.1.1
```

If I do not do above I cant ping access point

---

### Post by aDOT on 2007-01-02
Dear **Jblebrun**

I installed KDE wifi-radar, but in any cases (using or donot usig wifi-radar) the behavior of my wireless card does not change.

regards,
A.

---

### Post by jblebrun on 2007-01-02
> **aDOT said:**
> Dear **Jblebrun**

I installed KDE wifi-radar, but in any cases (using or donot usig wifi-radar) the behavior of my wireless card does not change.

regards,
A.

wifi-radar doesn't include interface management functionality, as far as I know. network-manager (and the KDE frontend for it, knetworkmanager) provide much more functionality, although for some people it is somewhat buggy. 

As for your current approach... try moving the wireless config options before the IP config options. 

What happens if you type **ifup wlan0** at the command line?

---

