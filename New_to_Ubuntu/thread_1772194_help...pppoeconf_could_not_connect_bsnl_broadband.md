---
title: "help...pppoeconf could not connect bsnl broadband"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by pushpavanam on 2011-05-31
I hav ubuntu 9.04 inside win xp ..my bsnl broadband connects well both pppoe thru ethernet and as bridge in win xp..but in ubuntu i could not get atleast the network device in my task bar...i hav tried everthin
sudo /etc/network/interfaces edited for static ip..... my device is pan0
auto pan0
iface pan0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
tried sudo /etc/init.d/networking restart
[ok]
tried pppoeconf pan0 as root user eventhen... experiencing timeout with my access concentrator it prompts me to username password creating resolv.conf everthing ...but in the task bar no device connected ..dispalyed 
ifconfig -a displaya both lo and pan0
also tried editing network connections (system -prefernces) dsl ..given ip,netmask,gateway and dns server..but i could not connect thru my modem
what should i do ?do i hav to install any driver for my modem ?
also how should be the connection normally i used to connect net thru bridge in xp do i hav to make it as pppover ethernet ...is it must?plz help

---

### Post by dineshs on 2011-06-01
I think pan0 is for bluetooth and you have an ethernet driver issue.Please post the result of ```
sudo lshw -C network
```.Once you install the driver you can follow [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")

---

