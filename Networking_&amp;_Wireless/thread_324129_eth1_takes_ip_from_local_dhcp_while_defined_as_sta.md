---
title: "eth1 takes ip from local dhcp while defined as static"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by choizy on 2006-12-23
This is my configuration in /etc/network/interfaces. As you can see I want eth1 to have a static IP. What realy happends is that it takes the last IP in the local dhcp server range. Not at once but im guessin at the same time eth0 renews its lease. How can I stop this from happening. (The dhcp server's range is 192.168.50.50 - 192.168.50.200).

iface eth0 inet dhcp
iface eth1 inet static
        address 192.168.50.10
        netmask 255.255.255.0


**EDIT: RESOLVED**

Case was resolved by checking for processes running dhclient and updating the interface

ps ax | grep dhclient

found severeal, used:

kill pid

The I restarted networking

/etc/init.d/networking restart

---

