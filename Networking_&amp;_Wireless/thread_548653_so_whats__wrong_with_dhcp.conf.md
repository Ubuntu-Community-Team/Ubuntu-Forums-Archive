---
title: "so whats  wrong with dhcp.conf"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2007-09-11
ive been looking at this for 30 mins now and cant see it. ive tried commenting out  all the lines and it still generates an error

msc@goldthorpe:~$ /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was:
msc@goldthorpe:~$        

heres the file

root@goldthorpe:/etc/dhcp3# grep ^[A-Za-z] /etc/dhcp3/dhcpd.conf
ddns-update-style none;
option domain-name "home.nw";
option domain-name-servers 62.31.144.39;
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.0.0 netmask 255.255.255.0 {
option broadcast-address 192.168.0.255;
option routers 192.168.0.254;
range 192.168.0.100 192.168.0.120;
root@goldthorpe:/etc/dhcp3#    


so what have i got wrong ?

---

### Post by leespa on 2007-09-11
what does tail -f /var/log/syslog say when you try to start it?

---

