---
title: "hELP:PC Client got IP from Server with Netmask wrong"
date: 2015-12-16
forum: Networking &amp; Wireless
---

### Post by n3wguys on 2015-12-16
Hello,

I have Ubuntu Server 14.10 as DC and 6 windows as client  have registered. one year ago, the client get IP from DHCP server and can access internet connection. With assign IP range is
192.168.11.10 to 192.168.11.xx
netmask 255.255.255.192
gateway 192.168.11.1
dns   192.168.0.1


but yesterday and now, three PC could not access internet but ping to server is OK.
and I get information from PC client, their IP assigned is being :
IP 192.168.11.12
netmask : 255.255.255.0
gateway :  192.168.11.1
dns = blank


I try this step
-ipconfig/flushdns
-ipconfig/release
-ipconfig/renew

and one PC is solved with should IP assign from server such as below:
IP  = 192.168.11.12
netmask = 255.255.255.192
gateway = 192.168.11.1
dns =192.168.0.1

and other PC is still nothing to solved except setting manual configurate for this PC. I could have not imagine when I configure the IP for 100 PC by manual when Ubuntu Server is being wrong netmask assigned.

Could you explain to me why did DHCP server share IP to client with netmask wrong ? 
and I sure one year ago with fix setting, I never got wrong netmask from client.


Thank you

---

