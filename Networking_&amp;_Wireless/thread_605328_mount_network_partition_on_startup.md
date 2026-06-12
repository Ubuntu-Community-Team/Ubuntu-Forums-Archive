---
title: "mount network partition on startup"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by lgastmans on 2007-11-06
I have editted the fstab file as follows:

<server>:/var/www/html  /home/luk/serverHTML    nfs     defaults        0      0
<server>:/home/luc      /home/luk/serverLUC     nfs     defaults        0      0

and all works fine, except that i have to run the mount command each time i boot my computer. I have read some threads regarding this topic, but without success.

Can anybody help me on how to make it mount on startup?

Thanks

---

### Post by Idiot_Box on 2007-11-08
I am having the same issue with nfs mounts in fstab during boot.  

Wired NIC was set manually in /etc/network/interfaces
[INDENT]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
         address 192.168.1.100
         netmask 255.255.255.0
         network 192.168.1.0
         broadcast 192.168.1.255
         gateway 192.168.1.1
[/INDENT]

fstab settings: 
[INDENT]192.168.1.50:/Media/Documents /home/user/Documents nfs rw 0 0
192.168.1.50:/Media/Pictures /home/user/Pictures nfs rw 0 0
192.168.1.50:/Media/MP3s /home/user/Music nfs rw 0 0
192.168.1.50:/Media/Backups /home/user/.Backups nfs rw 0 0
[/INDENT]

This does not mount automatically upon boot, but once the machine is up and running, these folders DO mount when I restart my network (/etc/init.d/network restart).
What can I do to get these folders to mount at boot?

---

