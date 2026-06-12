---
title: "Help with Eth0 and Eth1 setup on gateway firewall"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by shadycuz on 2008-03-03
Hey guys,

I'm using a guide to set up a firewall and gateway on an old machine with 2 nics. The guide is here [http://howtoforge.com/ubuntu6.06_firewall_gateway](http://howtoforge.com/ubuntu6.06_firewall_gateway). The only problem is it doesnt explain how to set up this nics very well. I know that for eth1 (my internet econnection) Should be set to DHCP ( I have it set to static since I have one). But for my internal Nic Eth0 I'm a bit confused. I set it as a manual configuration, and entered 192.168.1.1 for the Ip address. I then set the subnet as 255.255.255.0 but the third box said gateway and I'm not sure what to put their. If any one would like to help me it would be greatly appreciated. 

Thanks,
Levi

---

### Post by Dennis on 2008-03-03
If I understand you correctly, 192.168.1.1 goes in the Gateway box as well.

---

### Post by shadycuz on 2008-03-03
Thank you dennis, Ill give that a shot.

---

### Post by el Arm on 2008-06-29
> **shadycuz said:**
> Hey guys,

for my internal Nic Eth0 I'm a bit confused. I set it as a manual configuration, and entered 192.168.1.1 for the Ip address. I then set the subnet as 255.255.255.0 but the third box said gateway and I'm not sure what to put their.


I'm just learning about this as I set up a similar system so take it all with a grain of salt, but my understanding is that you want to leave it blank for eth0.

The gateway is what your computer uses to send packets to addresses that aren't on any of the NIC (eth0 or eth1) subnetworks.  Generally this means;
[LIST]
[*]you only want a single gateway
[*]the gateway will deal with internet-bound addresses
[*]it should be attached to the internet NIC
[/LIST] 

So the gateway is your modem, and the modem and eth1 IPs should be on the same subnetwork.

---

