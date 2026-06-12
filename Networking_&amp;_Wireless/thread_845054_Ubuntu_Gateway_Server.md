---
title: "Ubuntu Gateway Server"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by prats84 on 2008-06-30
Hi,
  I am new to Linux and would like to install a Ubuntu Gateway server to a small test network i created.

I have a server running DHCP which is used to service 6 clients.

Can u direct me to some links where a manual to configure gateway server is available. 

I do not wish to install any other services on the gateway machine like apache etc..

Thanks
Pratik

---

### Post by SpaceTeddy on 2008-06-30
check out this tutorial on [[COLOR="Blue"]internet sharing[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") - i guess that is what you need :)

hope it helps :)

---

### Post by prats84 on 2008-06-30
Hey thanks a lot.. i will configure it tomorrow.


Thanks again
Pratik

---

### Post by prats84 on 2008-07-01
Hey thanks .. its seems to be working .... thanks

---

### Post by prats84 on 2008-07-03
Hey... Now.. i have a server tht runs DHCP , APache on it and connected to the VLAN1 (2 other VLANS on the DELL switch). DHCP lease range is 192.168.11.3 to 192.168.11.40 . The server static address is 192.168.11.20
I want to make another PC as the gateway server. I have configured the iptables . This gateway has a static ip 192.168.11.7 on eth2 and 131.231.223.76 on eht0(connected to the internet).

In the server i have given eth0 default gateway as 192.168.11.7 .. I am not able to use internet from my server. 

Could u let me knw where am i wrong.

Thanks a lot
Pratik

---

### Post by SpaceTeddy on 2008-07-04
does the new gateway itself have internet ? are there any other clients in the 192.168.11.x network that can access the internet ? 

My main aim at the moment is figuring out if this is a problem with the server itself or a general network problem with the new gateway... 

Another guess is that you (maybe) need to reconfigure the dns server on the server. check the /etc/resolv.conf for that... 

hope it helps :)

---

### Post by prats84 on 2008-07-04
The gateway has internet on eth2. 
and yes there are other clients connected to the network.. by a switch which has has ip as 192.168.11.2 ... 

as of now... i guess the issue is with the DNS server... i suppose i should install a dns on the server .. rite... the server doesnot have have internet

---

