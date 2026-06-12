---
title: "IP Masquerade How to"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by LMSSML on 2008-01-08
Hi people

Is there any how to about IPMasquerade for Ubuntu ?

---

### Post by HermanAB on 2008-01-08
What do you mean?  You can assign multiple IP addresses to an ethernet port using ifconfig, if that is what you mean and you can set up a firewall using NAT with iptables if that is what you want.

---

### Post by LMSSML on 2008-01-08
1) Use your server as a NAT gateway.Is there a way to define this ?

2) Connect one NIC card to the modem (or Internet)
(defined as the NAT-servers WAN interface) How could be define the NAT-servers as WAN interface ?Is it defined on the /etc/network/interfaces file ?

3) Connect the other NIC card to a switch with serveral Ethernet ports
(defined as the NAT-servers LAN interface) How could be define the NAT-servers LAN interface ? Is it defined on the /etc/network/interfaces file ?

4) Connect all other PC's to the switch Done

5) Install a DHCP-server and DHCP-client software on your server I think I can handle with this.

5) The servers WAN interface should be defined as a DHCP-client
(the DHCP client should get one public IP-address 
from the ISP with DHCP when the server start up)So my problems start in here, this is defined on the dhcp or in other local ?

6) The server LAN interface should be defined as a DHCP-server
(the DHCP-server on the LAN interface delivery 
private IP-addresses to all your PC's)
(=>one unique private IP-address for each PC)Ok here I think with this I could define where dhcp will work /usr/sbin/dhcp dev ethx (ethx belong to eth to define dhcp)

7) Configure the DHCP server (on your servers LAN interface)I think this is an introduction to the below points

7.1 Set a private IP-address of the servers LAN interface
(e.g. 192.168.0.100) 
This could be defined like this auto eth1 
iface eth1 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.100


7.2 Set a subnet mask (e.g. 255.255.255.0) Couldn't this be done in the above point ? if not where I could define it ?

7.3 Definde a scope of private IP-address to your servers DHCP-server
(e.g. 192.168.0.10-192.168.0.99).This could be probably defined on the dhcp (/etc/dhcp.conf) and must start with range 192.168.0.10 192.168.0.99

7.4 Set a default gateway to the LAN interfaces IP-address
(e.g. 192.168.0.100)This probably would be the same has the above point, if not, where it can be defined.

---

### Post by LMSSML on 2008-01-08
Anyone could help

Manual would be great.

Thanks a lot

---

