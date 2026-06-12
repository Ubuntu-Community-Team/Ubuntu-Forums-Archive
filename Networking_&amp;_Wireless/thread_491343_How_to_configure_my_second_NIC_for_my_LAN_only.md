---
title: "How to configure my second NIC for my LAN only?"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by hobs0n on 2007-07-03
Ive been searching for this answer but really couldnt find any direct answer and I only know how Windows works, IE simple :D

I have 1 NIC, eth0, connected to the switch that gets the intarweb from my gateway and it is set as dhcp in the network manager in Xubuntu and internet works just fine. I have a second NIC, eth1, set as 192.168.0.3 as ip and 255.255.255.0 as subnet mask, nothing as gateway. I want this NIC to be connected to the LAN so I can connect to the SAMBA and so on. IIRC Ive searched what gateway is and how to config it and really didnt find anything, I bet there is information but I suck at finding things ;) 

What exactly is the gateway and what should I type there? I cant ping this NIC, 192.168.0.3 on the other computers in the LAN.

EDIT: I disabled the FIrewall on the other Windows computers.

---

### Post by spd106 on 2007-07-03
Check that the IP address (192.168.0.3/24) is on the same subnet as the PCs you are trying to ping from. 

A gateway provides a route to an external network, so if you mean the default gateway then you only need one and that points to the internet router/modem and provides the default route.

Sorry for not answering your ICS thread from a couple of weeks ago. Is this still the set-up you are trying to configure? If so then it sounds like you will need the Xubuntu server to be the gateway to your Internet connection (router). This does mean a DHCP server on would be useful and you are right that the ICS wiki page is not particularly clear.

You might find this wiki page useful for background information [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by hobs0n on 2007-07-04
The two PCs I try to ping from has 255.255.255.0 as subnet and 83.226.217.1 as gateway according to XPs ipconfig. I set the subnet and gateway to the same on eth1 on the Xubuntu box. If I understand you correctly I dont need to set a gateway on the eth1 since it wont be connected to the internet? It still wont work to ping the Xubuntu eth1@192.168.0.3, what am I doing wrong?

I dont need my Xubuntu server as a ICS any more, I can get up to 5 IPs from my ISP so I connect the LAN broadband to the gateway that I got from the ISP (has to use it since we have broadband telephony) and the ISP gateway is connected to my switches which give the two XP boxes and the Xubuntu server their own IPs.

Its NP that you dont answered btw :)

---

### Post by spd106 on 2007-07-05
What id the address range of the other PCs? Is it 192.168.0.x? If not then you won't be able to ping eth1.

You will have to either set up a NAT box (router) and move the network to a private address range (192.168.0.x/24) 

Alternatively you can give the other PCs a second IP address from this range.
e.g on Windows [http://www.windowsnetworking.com/articles_tutorials/multiipa.html](http://www.windowsnetworking.com/articles_tutorials/multiipa.html)
On Ubuntu you do this by adding an alias interface such as eth0:0 or if you want to you can use a second interface card.

---

### Post by hobs0n on 2007-07-06
I got it to work with that url there but the problem is my ISP doesnt seem to like it since when I have the IPs written in instead of DHCP my connection breaks all the time, which is kind of weird since the IP stays the same..

Thanx for helping!

---

