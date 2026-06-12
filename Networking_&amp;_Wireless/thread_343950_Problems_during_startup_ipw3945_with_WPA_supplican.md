---
title: "Problems during startup ipw3945 with WPA supplicant."
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by andrey_bakhmet on 2007-01-22
Hello, i have the problem with my DELL INSPIRON 6400 wireless connection.

My system: Edgy Eft (6.10)  2.6.17-10-generic. It is fresh (alternative) installation.

after installation i do:

apt-get update
apt-get install linux-restricted-modules-generic

Reboot... and my wireless connection is up. But my router (D-Link DSL604T) have WPA encription, so I change etc/network/interfaces to

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        wpa-driver wext
        wpa-ssid HW
        wpa-psk "mypassword"
	address 192.168.1.55
        netmask 255.255.255.0
        gateway 192.168.1.1

```


then I do: /etc/init.d/networking restart
and my wireless connection working. I can use Internet and other..

When i reboot the laptop wireless card is up, but without WPA, so i can't connect to the router.

Then, i do : /etc/init.d/networking restart   and connection works well again! (with WPA).

In the system log i found strange differences:
during boot up present line"ADDRCONF(NETDEV_UP): eth1: link is not ready"

and when i did /etc/init.d/networking restart - 
ADDRCONF(NETDEV_UP): eth1: link is not ready
ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready


So, can anybody help me? What i did wrong? Why after restart connection lost the WPA encryption?

---

### Post by wieman01 on 2007-01-22
This is a know bug... I have the same issue with my IPW2200. Please try _**post #2**_ of the WPA HOWTO in my signature. That should resolve your problem (has worked for a number of users).

---

