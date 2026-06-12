---
title: "wireless: cannot set txpower on"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by attilia on 2006-10-28
Hi everybody,

I have an Acer TravelMate 660, Kubuntu 6.06.
My wireless card seems to be working fine, it displays all available connections, but then does not connect to anyone.

I found out that the problem lies on the fact that it is actually turned off, and it cannot be turned on using txpower. This is what I get when I try to connect

Wireless interface(s): eth1
Permissions checked.
radio_on: /sbin/iwconfig eth1 txpower auto
==>stderr: Error for wireless request "Set Tx Power" (8B26) :
SET failed on device eth1 ; Invalid argument.
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
Networks found: 7
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
Gateway address: 192.168.1.254
Checking for active connection.

And if I manually want to set txpower on:

root@celestina:~# iwconfig eth1 txpower on
Error for wireless request "Set Tx Power" (8B26) :
SET failed on device eth1 ; Invalid argument.
root@celestina:~# iwconfig eth1 txpower auto
Error for wireless request "Set Tx Power" (8B26) :
SET failed on device eth1 ; Invalid argument.

I'm STUCK. ](*,) 
Can anyone help? thanks a lot...

---

