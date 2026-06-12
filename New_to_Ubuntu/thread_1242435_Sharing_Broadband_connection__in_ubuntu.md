---
title: "Sharing Broadband connection  in ubuntu"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-17
I have two ethernet cards in my PC which is running ubuntu 9.04 and i have more than 20 xp systems which are connected to switch..I have connected eth0 to modem and eth1 to switch..I haven't assigned static ip for  both cards and they are configured as DHCP..What should i do next??

---

### Post by 3rdalbum on 2009-08-17
> **getyourkarthick said:**
> I have two ethernet cards in my PC which is running ubuntu 9.04 and i have more than 20 xp systems which are connected to switch..I have connected eth0 to modem and eth1 to switch..I haven't assigned static ip for  both cards and they are configured as DHCP..What should i do next??

You should look up a HOWTO for internet connection sharing on Google.

This is one I found from the Firestarter website. It involves using the wizard in Firestarter to set up ICS:

[http://www.fs-security.com/docs/connection-sharing.php]("http://www.fs-security.com/docs/connection-sharing.php")

This is a different way, using Network Manager:

[http://www.freesoftwaremagazine.com/columns/howto_share_mobile_broadband_ubuntu_using_only_gui]("http://www.freesoftwaremagazine.com/columns/howto_share_mobile_broadband_ubuntu_using_only_gui")

---

### Post by mapes12 on 2009-08-17
Attached is a diagram of a suggested broadband sharing configuration using 2 NIC's in a Linux box. The full article is here: [http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm)

---

### Post by karthick87 on 2009-08-17
Wat is said to be internal interface and wat is said to be external interface??

---

### Post by mapes12 on 2009-08-17
> **getyourkarthick said:**
> Wat is said to be internal interface and wat is said to be external interface??Internal connects to the machines _inside_ your LAN. _External_ connects to the internet and the rest of the outside world via your modem.

---

### Post by karthick87 on 2009-08-17
This is my configuration,
eth0(on board Lan)
is connected to broadband router and it is configured to DHCP configuration..

eth1
is connected to switch,and these are the IP settings
IP address:192.168.1.1
Subnet:255.255.255.0
Default gateway:Left Blank

Is this correct?If it is correct,pls say me how to configure NAT..

---

### Post by superprash2003 on 2009-08-17
are you running the server or desktop version of ubuntu?

---

### Post by karthick87 on 2009-08-17
Desktop version..

---

### Post by xebian on 2009-08-17
> **getyourkarthick said:**
> This is my configuration,
eth0(on board Lan)
is connected to broadband router and it is configured to DHCP configuration..

eth1
is connected to switch,and these are the IP settings
IP address:192.168.1.1
Subnet:255.255.255.0
Default gateway:Left Blank

Is this correct?If it is correct,pls say me how to configure NAT..

Are you running your desktop as a router?

You said your desktop is connected to a 'broadband router'?  If this is combination modem/router then there should be some extra ports where you can connect the switch and be done with.

---

### Post by karthick87 on 2009-08-18
Yes i have given eth1 to the switch and from switch to XP systems..

---

### Post by superprash2003 on 2009-08-18
in that case ,you could try out this software called firestarter which has the ICS feature , it has a GUI , so easy to setup

---

### Post by karthick87 on 2009-08-19
After a long time,i have shared my connection successfully,but every time i have to re-enter the below commands to get it work..How to save this command permanently?
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE

---

