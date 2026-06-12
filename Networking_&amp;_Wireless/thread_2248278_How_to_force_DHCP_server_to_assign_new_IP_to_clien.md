---
title: "How to force DHCP server to assign new IP to client&#8207;"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by 17e4T3uRsk on 2014-10-13
[FONT=Verdana,sans-serif][COLOR=#000000]I am working on a project in which I would like to force DHCP server to assign a new IP address to client whenever the client sends an IP request, instead of keeping the current IP address. Is it possible? If yes, can someone please tell me how to do it? [/COLOR][/FONT][COLOR=#444444][FONT=Calibri][FONT=Verdana,sans-serif][COLOR=#000000]
[/COLOR][/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][FONT=Verdana,sans-serif][COLOR=#000000]Thank you very much,

Jeffrey[/COLOR][/FONT][/FONT][/COLOR]

---

### Post by Michael_McKenney on 2014-10-13
Usually, you don't want to do it.   You can change the lease settings to a lower amount so it drops and clears the table more often.  

# Sample /etc/dhcpd.conf
# (add your comments here) 
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "mydomain.example";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
}

These are in seconds.  
default-lease-time 600;   # 5 minutes
max-lease-time 7200;     # 2 hours

Usually set to 1 day
default-lease-time 86400;
max-lease-time 86400;

---

### Post by Penguin360 on 2014-10-17
After some research and asking experts in this field, I found out this is not possible without some hacks on the DHCP server. When a client sends an IP request, the server will check its lease table to see if the client has already have an IP assigned, if yes and if the lease is still valid (not expired), then the server will send an ACK (acknowledgement) message to the client and also let the client keep the current IP address. Even if the lease has expired, but if the IP has not been assigned to another client, then the server will ACK the client's request and reassign the IP back to the client. To force the DHCP server to assign new IP to client, then the config file of the server needs to be purged, this way when the server checks its lease table it will not find any record and it will have to find an IP from the available IP pool to assign to the client.

---

