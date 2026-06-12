---
title: "Configuring network in terminal"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by Gordonbp531 on 2005-11-03
I've installed 5.10 in server mode. Due to the absolute inaccessibility and configuration of the router I use, I have to skip network configuration on install as I have to edit /etc/dhcp3/dhclient.conf before I can use apt. that's fine in a GUI environment, but I need to know how to set the eth0 parameters using the command line as obviously until I get the network up and running i can't use Apt to get the XFCE desktop that I need!

thanks

---

### Post by swerner on 2005-11-03
As root you need to run
```
ifconfig eth0 up 192.168.0.1
```
this will configure eth0 for the given IP address. To see how your network devices are configured just type ifconfig by itself. When you want to stop the eth0 connection you type
```
ifconfig eth0 down
```
It's really that simple! :)

---

### Post by Gordonbp531 on 2005-11-03
Thanks! How do I configure dhcp rather than a static address?
Is it possibly "ifconfig eth0 up dhcp" ?

---

### Post by az on 2005-11-03
add to the /etc/networking/interfaces

auto eth0
iface eth0 inet dhcp


and then do 
sudo ifup eth0 

It will also just bring the interface up on boot.

---

### Post by Gordonbp531 on 2005-11-03
Thanks! That did the business.

---

### Post by jdong on 2005-11-03
Read "man interfaces" if you want a full look into how /etc/networking/interfaces works, including setting up multiple IP's or static IP's, both important features on servers.

"sudo dhclient eth0" will assign you a DHCP address just once, while you can use ifconfig (as previously mentioned) to set up non-permanent static IP's.


The settings in /etc/networking/interfaces are applied at every bootup though.

---

