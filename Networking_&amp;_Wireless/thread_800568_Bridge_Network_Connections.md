---
title: "Bridge Network Connections"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by madman92 on 2008-05-19
Hi everyone,

Right now I'm using the making things MAKE controller, and I talk to it using Open Sound Control through an ethernet port. However, when I want to use my controller, I have to statically set my ethernet to a local  address, and then I lose my wifi. Is there any way that my wifi and ethernet can be bridged?

---

### Post by SpaceTeddy on 2008-05-20
i guess you are using network manager to connect to other the ehternet or the wifi ?

if that is the case, there is no other but to configure one of the interfaces statically, effectivly removing it from network manager. The Problem you are experiencing is that Network Manager does not support multiple network connections.

connect to wifi via Network manager. Then open up a console and try to run this command if you have a dynmaic IP (via dhcp):
```
sudo dhclient eth0
```
I am assuming that eth0 is your ethernet card.

If you have a static configuration, try this command
```
sudo ifconfig eth0 %IP
```
where %IP is the IP that you want to set on the device.

These Settings are all temporary and will (latest) disappear after a reboot. To make them permanent, you will need to edit /etc/network/interfaces and set the device there permanently. Setting the device there will *remove* the network card entirly from network manager. 

hope it helps :)

---

### Post by madman92 on 2008-05-26
In the end, I added this
> iface eth0 inet static
address 192.168.212.222
netmask 255.255.255.0
gateway 192.168.1.1

in my network/interfaces file, with my Make Controller running on 192.168.212.223, and I can talk to that through OSC and use wifi.

---

