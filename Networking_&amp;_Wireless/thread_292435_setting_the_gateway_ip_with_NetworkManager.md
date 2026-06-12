---
title: "setting the gateway ip with NetworkManager"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by solasaurus on 2006-11-03
hi,

This should be simple - but I don't know what I don't know. :oops: 

I recently installed NetworkManager in order to get my wireless running after reading through these forums. Now I can't connect to the internet (even with the wired connection) but I can see everything on the LAN. I have a gateway/modem that has IP 192.168.1 254.

I know from running Debian on a webserver that /etc/network/interfaces, you can specify a gateway IP for each interface. Now following instructions from these forums I've deleted most of the entries so that NetworkManager can take control of the ifaces. eth0 is working fine using DHCP but ifconfig tells me no gateway has been defined. I'm fairly sure this is why I cannot connect to the net with my Ubuntu PC.

Can anyone tell me how to set a gateway address with NM? Which files do I need to edit to set up my network configs?

TIA; sol

---

### Post by wieman01 on 2006-11-03
I don't think you can. NetworkManager supports DHCP only.

---

### Post by NetworkGuy on 2006-11-03
If your router is supplying DHCP (which it should be default) you should be getting the correct gateway from your router.   Can you supply the output of a netstat -rn command from the terminal.

---

### Post by solasaurus on 2006-11-03
> **NetworkGuy said:**
> If your router is supplying DHCP (which it should be default) you should be getting the correct gateway from your router.   Can you supply the output of a netstat -rn command from the terminal.

192.168.1.0    0.0.0.0    255.255.255.0    U    0 0    0    eth0
0.0.0.0        192.168.1.2  0.0.0.0        UG   0 0    0    eth0


Could it be that it's seeing the router (192.168.1.2) as the gateway rather than the modem (192.168.1.254)? This has me a bit green cos I always tend to use static IPs and have control over things. I'm new to DHCP as well as Ubuntu. :-? 

Thanks for your assistance. :-)

---

### Post by NetworkGuy on 2006-11-03
If you want to use NetworkManager, you will need to reconfigure your network to work with DHCP.

But if you are only going to use wired networks, you really don't need NetworkManager

---

### Post by solasaurus on 2006-11-03
> **NetworkGuy said:**
> If you want to use NetworkManager, you will need to reconfigure your network to work with DHCP.

But if you are only going to use wired networks, you really don't need NetworkManager
Okay, I finally figured it out. I was so used to doing all the network configs on my linux box it didn't occur to me that with DHCP you just do the configs on the router and modem and just let it all work. Thanks NetworkGuy for pointing this out to me, especially as it's not strictly an Ubuntu/Linux question.

For the benefit of anyone else that comes across the same issue, I fixed this problem by logging on to my router and setting it up as an Access Point. It then accepted an IP number (automagically) from my modem which also has DHCPd. So the router now forwards everything automatically  to the modem which is acting as a gateway to the net.

The whole problem for me is that networking is just getting too damn simple. And that's confusing! :p

---

### Post by stream303 on 2006-11-13
> **solasaurus said:**
> 
Could it be that it's seeing the router (192.168.1.2) as the gateway rather than the modem (192.168.1.254)? This has me a bit green cos I always tend to use static IPs and have control over things. I'm new to DHCP as well as Ubuntu. :-?

That's correct.  Your router is the first thing your Ubuntu box's ethernet card sees on it's way out to the internet, therefore the router is the gateway, not the modem - even though it is only inches away. :)

---

