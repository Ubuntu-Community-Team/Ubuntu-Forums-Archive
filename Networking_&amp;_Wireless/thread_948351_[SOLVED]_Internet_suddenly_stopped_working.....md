---
title: "[SOLVED] Internet suddenly stopped working...."
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2008-10-15
I am using Hardy and an ethernet connection for internet. earlier today in the morning i was able to connect to internet without any problem but when i turned on my laptop in the afternoon..it didn't connect to internet when i checked for the problem i found that there was no "eth0" network interface..
It just disappeared..
The output of 
```
cat /etc/network/interfaces
``` is 
```
auto lo
iface lo inet loopback
```
i added the following lines to it..
```
auto eth0
iface eth0 inet dhcp
```
and then restart the network using the following command```
sudo /etc/init.d/networking restart
```
then it showed some errors..
```
*Reconfiguring network interfaces...
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systemss Consortium.
All rights reserved.
For info,, please visit http://www.isc.org/sw/dhcp/
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0
```
As i have already mentioned "ifconfig" only shows 2 network interfaces..
"lo" and "wlan0"
I am really confused  
please..help me..

---

### Post by shredder12 on 2008-10-15
somebody  help please..

---

### Post by mtrtm on 2008-10-15
I experienced what I believe was the same problem.  Additionally, logging in took ages, trying to "sudo -s" seemed to hang for several minutes, and attempts to connect to localhost by SSH was disconnected.  

What solved the problem for me was (as root) to run restart the system logging utilities.  You can do that with the command

"/etc/init.d/sysklogd restart"

After that, several hanging/queued actions were executed, and I could restart the network ("/etc/init.d/networking restart").

I hope this might help you.

---

### Post by shredder12 on 2008-10-15
no sadly it didn't work..
the network manager still shows only 2 connections..
one is point to point and the other is wireless connection..
the "wired connection" interface is not there..
i think may be i should try and create a new wired connection manually...but i have no idea how to do this..
can you help me..

---

### Post by shredder12 on 2008-10-16
hey finally i got the solution..
actually earlier on the very same day when this problem occured..i updated my kernel...to 2.6.24-21 the problem was all because of it..
When i switched back to 2.6.24-19..everything started working fine..
so may be the new kernel needs to be fixed..

---

