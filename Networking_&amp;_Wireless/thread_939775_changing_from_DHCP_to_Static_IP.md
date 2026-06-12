---
title: "changing from DHCP to Static IP"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by keiffee30 on 2008-10-06
when i change from a DHCP address to a static address i lose all network connection. all i can do is change it back.

say ... 

192.168.9.2-9 is static and 10-20 is DHCP 
Subnet 255.255.255.0
Gateway 192.168.9.1

Im using Ubuntu 7.10 and 8.04. dose anyone know what is going on?

---

### Post by Bucky Ball on 2008-10-06
System->Admin->Network, unlock, click on your wireless then properties. In configuration, have you go 'Static IP' and not 'Automatic DHCP'? Your router needs to be serving a specific static ip you can enter along with you correct ESSID and WEP/WPA details.

---

### Post by keiffee30 on 2008-10-24
I have gone to this section and when ever i change from DHCP to Static i lose all connection to my internal network.

I have put in the correct IP addressing the MAC address of the NIC is in my Router (as i use MAC filtering). I can not see why this is not working for Static. As soon as i change to DHCP everything works. 

This happens on 7.04, 7.10, 8.04

---

