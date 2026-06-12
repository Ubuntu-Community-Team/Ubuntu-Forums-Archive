---
title: "Internet Gateway with dynamic IP"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by skap on 2008-09-06
Hello, i'm kind of newbie in linux networking, so, here is my question:

I have a pc with Ubuntu Hardy and i want to make some kind of gateway, to share internet to my LAN. I have 2 GB network cards. Also, i must say that i dont have a static ip, i have a dynamic ip, so it changes sometimes. So i need help with this. =)

Thanks in advance.

---

### Post by skap on 2008-09-07
Up!

---

### Post by jimv on 2008-09-07
Why would you have a dynamic IP on your LAN?

---

### Post by skap on 2008-09-07
i dont want a dynamic ip on my lan, i dont know how to make a gateway with a dynamic ip from ISP...

---

### Post by superprash2003 on 2008-09-07
dynamic ip shouldnt be a problem.. all you need to do is enable internet connection sharing [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by skap on 2008-09-07
so, if i follow that tutorial, i'll have some kind of internet gateway? I want that my second gb card gives dhcp...first receives the internet and the second gives internet to lan by dhcp...

---

### Post by superprash2003 on 2008-09-09
yes you would get a gateway..for dhcp [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by skap on 2008-09-09
Hm...I'm gona try out that howto, it seems that it will work, btw, after that ill put a router on the network card that gives dhcp, it will work nice right?

Greetz.

---

### Post by skap on 2008-09-09
Oh well... I've followed the last tutorial step by step and guess what...Didnt worked...I've noticed on /etc/network/interfaces that eth0 is set to iface "eth0 inet dhcp" but im receiving internet directly from WAN. 

So here is my case: A modem > pc with ubuntu hardy > router > clients

What is wrong?

---

### Post by superprash2003 on 2008-09-10
are you on ppoe or bridged mode?ensure that you are mentioning the right interface for the right use.An alternative could be installing firestarter.It is a firewall which has built in ICS feature with DHCP

---

### Post by skap on 2008-09-10
How i know if its ppoe or bridged? I've set the eth0 for WAN and eth1 for LAN... I think that its correct...

---

### Post by skap on 2008-09-11
I think my problem is about the external ip that connects to eth0 cause its dynamic... I need some help plz.

---

### Post by dmizer on 2008-09-11
Very few connections to the interenet are not dynamic, so no, I'm certain this is not your problem.

Take a look here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Once your Ubuntu is configured for ICS, your Ubuntu computer will be the router. If you introduce a second router into the mix, it will likely cause problems. You will either need to use a hub, or disable dhcp on you router.

---

### Post by eentonig on 2008-09-11
Tackle you problem in small steps.

Pure IP related first:
1. Can you(r gateway) connect to the internet and get an ip address from your ISP?  
2. Can your LAN hosts connect to the LAN and receive an IP address?
3. Can you LAN hosts ping the gateway on it's LAN ip address?
4. Can you LAN hosts ping the gateway on it's WAN ip address?

---

### Post by superprash2003 on 2008-09-11
please post an ifconfig output from your terminal..

---

