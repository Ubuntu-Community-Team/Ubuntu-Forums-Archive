---
title: "Can't connect to the internet"
date: 2005-03-29
forum: Networking &amp; Wireless
---

### Post by ibs on 2005-03-29
Recently i upgraded to Ubuntu Hoary from Warty using Synaptic. But when i rebooted into Hoary i could not connect to the internet. I saw on a previous thread that i had to insert a comma between netbios-scope and interface-mtu in the 21th line in /etc/dhcp3/dhclient.conf. 

In my file there was no interface-mtu so i tried to add it in and put the comma in. But that didn't work. I tried to reboot also after that, but it still didn't work.

Please help me, i really need internet access from that computer.

---

### Post by arctic on 2005-03-29
have you already checked that it is not a problem with ipv6 and your resolv.conf?
[http://www.ubuntuforums.org/showthread.php?p=22132#post22132](http://www.ubuntuforums.org/showthread.php?p=22132#post22132)

---

### Post by alastair on 2005-03-29
Look at your syslog and check for thernet (eth) messages e.g. ethernet module loading etc.

/var/log/syslog

Also check :

ifconfig -a
route -n

---

