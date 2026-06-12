---
title: "Does my DHCP server need at least 2 LAN ports?"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by webmiester on 2018-09-04
Hi everyone,

Im reading about the DHCP server.  Some sites tell me that it is possible to have more than one DHCP server in a LAN.  Do all DHCP servers need to have at least 2 LAN ports (given that we wont be using wifi) ?

LAN Port 1 goes to the internet or to the ISP modem
LAN Port 2 goes to a switch which connects to the computers in the network

Is it possible to just have just 1 LAN port?

With 1 LAN port, all the computers and the DHCP server will just be connected to a switch which connects to the ISP or the ISPs modem?

Can I connect a 2nd DHCP server into the LAN with the 2nd one having only 1 LAN port too?

My goal here is to come up with computers with 2 different sets of IPs.

Group 1 computers will have IP addresses of 192.123.12.0-255
while Group 2 computers will have IP addresses of 192.123.13.0-255
I want to do this with the least rewiring as possible because the network is already setup (Its a flat network), and the network spans different floors in the building.  I can use MAC address binding to assign which computers will get group 1 and group 2 IP addresses. 

Thank you so much.

---

### Post by TheFu on 2018-09-04
> Do all DHCP servers need to have at least 2 LAN ports (given that we wont be using wifi) ?
No. No need for different subnets or multiple LAN connections. Well, unless you want it to perform other duties.

Having 2 DHCP servers on the same LAN can be a problem, because the first (quickest) to answer the client will be the one most clients use.  Advanced DHCP is beyond my skill.

If you only have a modem from the ISP, then you NEED a router/firewall for basic security.

---

### Post by webmiester on 2018-09-04
Thanks TheFu,

Even my IT network guy isnt able to imagine it.  Yes, what I know is that the first DHCP to answer the client will be the one that the client will use. So I am thinking of binding all the IP addresses of DHCP server 1, so that when a new device enters the network, it wont be given an address.  Instead, it will be DHCP server 2 that will give it an address since DHCP server 2 will have free IPs available.  I am having some trouble preventing cellphones connecting to our network from accessing the server system.  So I figured, one way to do this is to give all these devices a different subnet.

My IT is suggesting that I we give them a range of IPs to block to the server...  So the company computers will be given for example IPs of 192.123.123.0 up to 192.123.123.99 then the guests will be given 192.123.123.100 up to 255.  This is currently what the system is doing.  Now I was setting the IPtables to drop the connection of those with IPs of 100-255, but it doesnt work :(.  My discussion on this approach is on this thread: [https://ubuntuforums.org/showthread.php?t=2399909](https://ubuntuforums.org/showthread.php?t=2399909)

So now I am thinking of a different approach which is to have 2 DHCP servers giving out different subnets.  I read that its possible to have 2 DHCP is possible but I havent read whether it is possible to give 2 subnets on the same network without having to rewire my network.  In my mind it is possible, but I havent read anyone doing it yet.

Thanks so much for your post.

---

### Post by TheFu on 2018-09-05
Or don't use wifi at all. IMHO, wifi is always non-secure.

Why are cell phones even allowed on the network?  Is there no secured passphrase? Do you have to provide wifi for anyone walking by due to legal requirements?  Why not have a separate wifi network for guests if that is your intent?  Too many questions.

If you have to use wifi (poor choice, IMHO), why don't devices you control access the main network either with a VPN or radius authentication system?

---

