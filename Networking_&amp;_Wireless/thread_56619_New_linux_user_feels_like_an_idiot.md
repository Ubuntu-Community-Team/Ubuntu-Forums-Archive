---
title: "New linux user feels like an idiot"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by karim on 2005-08-13
Hi. Help. I'd appreciate if someone could help me out. I'm a complete novice, and I was trying to connect to the net for the first time (through ethernet LAN to a wireless provider). While configuring the network I put in the proxy's address as host name (euh...) . That's when things went quite wrong. When I rebooted the computer would stall for a minute on the network configuration line. At logon an error message would appear warning me that Gnome would not work properly and that I needed to add something to /etc/hosts. I added the proxy's address to /etc/hosts since that was what I had changed. That took car of the error message and now Gnome works again, but when I open Network Administration to try to delete what I had changed it crashes ("Network Administrator has shut down unexpectedly"). I'd really be grateful if someone could help me out.

---

### Post by IronKnuckles on 2005-08-13
I am having the exact same problem. Can you post the contents of your /etc/hosts file?

---

### Post by karim on 2005-08-13
Sure, but it will take a while. I have a windows and a linux partition, so I need to reboot, get the etc file from linux, then reboot again to connect to the net from windowd. I'll also have to copy the file by hand...

---

### Post by karim on 2005-08-13
This is etc/hosts:

127.0.0.1 localhost. localdomain localhost karim
#The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
172.16.30.1


The last line is my proxy's address. I know it's not supposed to be there, but I added it to make Gnome work again. 
P.S. eth0 no longer shows up on the network configuration applet, only eth1 (wireless) and lo; but when I press Configure it goes into Network Administrator and crashes. Also, in Network Tools the hardware address for eth0 reads "unavailable", although it shows up in iconfig.

---

