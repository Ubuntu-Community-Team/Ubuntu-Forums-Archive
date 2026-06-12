---
title: "WiFi disconnected when Ethernet is connected"
date: 2015-12-03
forum: Networking &amp; Wireless
---

### Post by chris_3 on 2015-12-03
Hi folks, 

I'm connected on a public WiFi (Set on DHCP) and I also have a device connected with Ethernet (Manual IP). When I plug this device on the Ethernet, it disconnects my wireless connection, like if I'm not able to use both wireless and Ethernet at the same time. When I run ifconfig, my wireless connection still have an IP (given by the DHCP server).. I don't get it. Any suggestions ? Thanks.

---

### Post by SeijiSensei on 2015-12-03
If both the wired and wireless connections are using the same router and network, then you don't want both of them active at the same time.  This leads to routing problems.  There is also no advantage to having both adapters connected to the network, unless you use some advanced features of the Linux kernel like "bonding" to make the two adapters appear to be one.  Just use the wired connection and all will be fine.

---

### Post by chris_3 on 2015-12-03
As I said I have a device (Radio receiver) connected on the Ethernet interface. Actually this is a gigabit Ethernet interface. I can't use my device on the wireless interface, since I need at least 60Mbps of data rate. 
Moreover I only can get the Internet access through the wireless network. 

That's why I need to fix it.

---

### Post by SeijiSensei on 2015-12-03
So you want to configure the machine as a router?  Does the wifi interface get its configuration from the upstream router via DHCP?  If so, just assign some other network subnet to the Ethernet interface and the device.  For instance, if wlan0 has 192.168.1.2 from your router, use static addressing to assign an address like 192.168.2.1 to the Ethernet interface and 192.168.2.2 to the radio device.  Edit /etc/sysctl.conf and remove the hash mark from the line
```
net.ipv4.ip_forward=1
```
then reboot.  If the device needs to communicate with the external network or the Internet, then you need to add 
```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```
as well.  Put the command (without sudo) in /etc/rc.local to have it run at boot.

---

### Post by chris_3 on 2015-12-04
Thanks for your answer. The DHCP server gave me this address: 10.132.10.160. I set my Ethernet interface up to 192.168.10.1. The device is 192.168.10.2. Moreover I removed the hash in sysctl as you said. It finally worked when I removed the gateway 192.168.10.1 within the GUI interface for the Ethernet connection.. Thanks for your answer.

---

