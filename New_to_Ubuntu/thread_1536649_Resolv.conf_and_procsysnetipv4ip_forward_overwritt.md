---
title: "Resolv.conf and /proc/sys/net/ipv4/ip_forward overwritten"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by LRT on 2010-07-22
I'm running ubuntu server 10.04 that is setup as a dhcp server. It has eth0 and eth1 with static IP for both.

I have the nameserver entries in /etc/resolv.conf but they are getting erased out every time I reboot the server.

/proc/sys/net/ipv4/ip_forward is also getting reset to '0' everytime I reboot. 

How can i make both of these configurations permanent?

---

### Post by LRT on 2010-07-22
found this on the net:

change the following lines in /etc/dhcp3/dhclient.conf
supersede domain-name “example.com”
prepend domain-name-server xxx.xxx.xxx.1, xxx.xxx.xxx.2

is this the best way of fixing my problem with resolv.conf? or should i just comment out all lines in dhclient.conf since i'm using static IPs?

[http://lenss.nl/2008/11/making-permanent-changes-to-resolvconf-under-ubuntu/](http://lenss.nl/2008/11/making-permanent-changes-to-resolvconf-under-ubuntu/)

---

### Post by LRT on 2010-07-22
i found the solution to automating the ip_forward setting in another thread:

[http://ubuntuforums.org/showthread.php?t=202100](http://ubuntuforums.org/showthread.php?t=202100)


but i'm still having trouble making the nameservers setting in /etc/resolv.conf stay permanent. anyone know how to do this?

---

### Post by bodhi.zazen on 2010-07-22
Are you running networkmanager ?

---

