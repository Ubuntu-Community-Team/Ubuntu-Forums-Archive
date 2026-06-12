---
title: "Use Router with Firestarter"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by thon0925 on 2008-10-26
I want to have a firewall setup that connects to my cable modem and my router. I am able to connect to my cable modem, but I cant get my router to connect to Firestarter. I tried to use DHCP to allow the router to auto configure itself, but no matter what IP I choose, it failed. I am also connected to my router through the internet port with a static IP.
Any ideas on what to do?

---

### Post by dmizer on 2008-10-26
If you want this configuration:

modem -> ubuntu -> "router" -> network

Then, you will need to disable routing (NAT) on the router. You will also be unable to make use of the WAN port on the router. all connections will need to be on one of the regular ethernet ports on the back of the router.

Bascially, your Ubuntu computer will become the router, and the router will become a hub.

---

### Post by thon0925 on 2008-10-26
I see, will wireless still work with setup?

---

### Post by dmizer on 2008-10-26
You mean this?

modem -> ubuntu -> router/hub -wireless-> network

Then yes ... it should work even with NAT disabled on the hardware router.

---

### Post by thon0925 on 2008-10-26
Ok, I am using a Netgear WGR614v6 and it does not have an option to disable NAT. Will I have to get a new router to get this setup to work?

---

### Post by dmizer on 2008-10-26
> **thon0925 said:**
> Ok, I am using a Netgear WGR614v6 and it does not have an option to disable NAT. Will I have to get a new router to get this setup to work?

All routers have the ability to turn this off. Problem is, this is usually called several things, and located in different menus.

I took a peak at the manual for your router. You'll need to disable the SPI firewall as well as uncheck "Use Router as DHCP server" under the LAN IP setup section.

Keep in mind, it will be tricky to access the router configuration page after you've made these changes, so make sure you have everything set up exactly the way you need it. If you want to use your router as a router again, the easiest way to do so will be to reset the router with the "Default Reset" button on the back of the router.

---

### Post by thon0925 on 2008-10-26
Yeah, I disabled DHCP and the firewall, but Firestarter still gives an error whenever I try to start it with DHCP (its setup for 192.168.1.3-192.168.1.10).

---

### Post by dmizer on 2008-10-26
> **thon0925 said:**
> Yeah, I disabled DHCP and the firewall, but Firestarter still gives an error whenever I try to start it with DHCP (its setup for 192.168.1.3-192.168.1.10).

Is the cable still connected to the WAN port on the router? If so, you'll have to move it. You cannot use the WAN port for this configuration.

Here is some more information about ICS: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing). There are some rough pointers for Firestarter included in this link. Unfortunately, I don't have any solid Firestarter howto's on hand.

As an aside, is there any reason why you need this setup? There may be an easier way of going about it.

---

### Post by thon0925 on 2008-10-27
Yeah my PC is connected to the LAN port. I want this setup so I can trace information that is sent from my PSP to my PS3 and examine the info. I've tried this with a few other setups, but the PSP will not connect if it is on a network bridge, so I thought it may work if I have a firewall at the source of the internet.

---

### Post by inkrypted on 2008-10-27
Never disable any of the security of your router that is dangerous. you can do DHCP if you want just make sure it's enabled in the router and in Ubuntu. As for Firestarter you might want to try GUFW it is a lot less of a headache. If you are using a router you have a firewall at the source of the internet so to speak.

---

### Post by dmizer on 2008-10-27
> **inkrypted said:**
> Never disable any of the security of your router that is dangerous. you can do DHCP if you want just make sure it's enabled in the router and in Ubuntu. As for Firestarter you might want to try GUFW it is a lot less of a headache. If you are using a router you have a firewall at the source of the internet so to speak.

I'm sorry, but in this situation, how is it dangerous to disable the router's firewall and NAT? It's either that, or purchase a hub.

---

### Post by dmizer on 2008-10-27
> **thon0925 said:**
> Yeah my PC is connected to the LAN port. I want this setup so I can trace information that is sent from my PSP to my PS3 and examine the info. I've tried this with a few other setups, but the PSP will not connect if it is on a network bridge, so I thought it may work if I have a firewall at the source of the internet.

Okay ... take a look here: [https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless#Configuring%20the%20SERVER](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless#Configuring%20the%20SERVER)

The above link suggests that you should not use firestarter's dhcp feature.

You can install a separate dhcp server according to these directions: [https://help.ubuntu.com/community/Internet/ConnectionSharing#DHCP/DNS%20server](https://help.ubuntu.com/community/Internet/ConnectionSharing#DHCP/DNS%20server)

I've never used or looked at GUFW so I have no way of knowing how well it will perform as a gateway.

---

### Post by thon0925 on 2008-10-27
What I want to do is make my PC act as a pass through device than can log network packets when I choose to. I tried this on a different setup, but the PSP can not connect to the PS3, so I thought that if I had a pass through device at the source of my internet, I could log the info.

---

### Post by inkrypted on 2008-10-27
Well if you want to disable additional security it's cool. Sounds like you might want to use your computer as a router for your PS3 along with your wireless router? Maybe Wireshark will help with logging.

---

### Post by dmizer on 2008-10-27
> **inkrypted said:**
> Well if you want to disable additional security it's cool. Sounds like you might want to use your computer as a router for your PS3 along with your wireless router?

As far as I know, it's not just "it's cool", it's absolutely necessary in order to do what this user wants to do. The only way to incorporate two routers on the same network is to configure them for different subnets. If the Ubuntu computer is not on the same subnet as the PSP, then you can sniff data all day long and never learn anything.

---

### Post by inkrypted on 2008-10-27
I do not want to argue. After reviewing the post it just seems I really fail to see why you would want or need to use Ubuntu as a firewall enabled router behind a firewall enabled router. Just to review packet logs on the PS3? Maybe I am not fully understanding and if that is the case I apologize. I wish the user good luck.

---

