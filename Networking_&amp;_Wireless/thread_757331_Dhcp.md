---
title: "Dhcp"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by Dark_Ness998 on 2008-04-16
Hey there, I am new to Ubuntu but I have been using fedora for a while. However, I am a little confused on how to configure DHCP. I have installed it using apt-get install, however I am not sure how to configure it. I know the /etc file with how to configure it. Just, im not sure what addressing scheme to use.. or ne thing. 

In class, I  seemed to be able to configure and start/restart the dhcp service using the GUI interface DHCPD program, but was unable to allow for automatic Ip addressing. Also.. not much research has been done with ftp or telnet, but if you could lead me further, that's appreciated :0

---

### Post by juan@forum on 2008-04-16
if you want a DHCP Server ->
sudo apt-get install dhcp3-server


then check this file /etc/dhcp3/dhcpd.conf, read it, that should help you to make a basic configuration

then sudo /etc/init.d/dhcp3-server start or sudo invoke-rc.d dhcp3-server start

then sudo netstat -anup, port udp 67 should be up

---

