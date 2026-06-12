---
title: "Connecting two wireless routers - Ubuntu 14.04"
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by robertzito on 2015-04-12
I just installed 14.04 and I am trying to get an understanding of my network, I go from my cable modem with internal wireless router that has an ip range of 192.168.0.x, I go from one of the Ethernet ports on the newcable modems LAN port to the Internet/Wide Area Network (WAN)Ethernet port of my older Netgear WNR3500 that has a range of192.168.1.x. 


So here is where Iam getting confused, when I am on the wireless SSID of the older Netgear router I am able to access the 192.168.**0**.1 internal webpageof the new cable modem w/ wireless router. When I am on the SSID of the cable modem with wireless router I am NOT able to access the192.168.**1**.1 of the internal web page of the Netgear WNR3500 router.On the WNR3500 wireless routers Ethernet port, I have my printer, my media drives, etc.


The question is, how can I make this an entire network that no matter which SSID I am connected to, I am able to access all the network elements of mynetwork without having to switch SSID's which I am currently doing?


Is it a matter ofassigning the netgear router a static IP in the range of 192.168.0.xor is there some sort of port forwarding that needs to be setup?

---

### Post by michi1983 on 2015-04-12
we would need to know all settings on both routers to see what your problem is. 

why do you use two routers anyways?
is router 2 (netgear) set up in accesspoint mode?
if yes, put the cable in one of the ethernet ports and not the WAN port.

---

### Post by robertzito on 2015-04-13
I have some older wifi equipment that is 2.4GHz and I have some that is 5GHz, the cable modem with internal router is 5GHz, I do have the ability to set the cable modem with internal router to allow for both 2.4 and 5GHz, but want to keep them separate so that the kids use the older router and I am the only one using the 5GHz router. In my mind I thing it give me more bandwidth but at the end of the day the bottle neck is the cable modem but I thing I benefit because when I look at the older Netgear router there are sometime 15+ clients with 6 users in the same house with handheld devices and gaming systems. At least being on the 5GHz give me a sense of my own network and I can control the bandwidth of the users on the 2.4GHz, I can also block sites on their router that would not be blocked on mine.

In the attached zip files are the print screens of both routers, I am looking at the cable modem with built in wireless router as the master unit and the Netgear WNR as the slave unit.

---

### Post by michi1983 on 2015-04-14
Well according to your screenshots there is no device with an IP of 192.168.**1**.x

Your cable modem has the IP 192.168.0.1 and your Netgear gets its IP via DHCP from your cable modem, so it also gets an IP from the 192.168.0.2-192.168.0.254 range.
What you could do is change the DHCP range from your cable modem to 192.168.0.2-192.168.0.100 for example.
And then give the netgear a fixed IP address e.g. 192.168.0.150, netmask 255.255.255.0, gateway 192.168.0.1, DNS 192.168.0.1
THEN you can access the webinterface of your netgear via 192.168.0.150 in your browser.

---

### Post by Keith_Helms on 2015-04-14
From your screenprints, it looks like the cable modem router has assigned an IP address of 192.168.0.12 to your netgear router.  Make sure you have DHCP server turned off on the Netgear router and your network might be working like you described.

---

### Post by michi1983 on 2015-04-14
> **Keith_Helms said:**
> From your screenprints, it looks like the cable modem router has assigned an IP address of 192.168.0.12 to your netgear router.  Make sure you have DHCP server turned off on the Netgear router and your network might be working like you described.

It does not ;) 192.168.0.12 is just the IP he used last when he had set it to static.
I first needs to log into the cable modem and change the DHCP range.
Then find out what IP gets distributed to the netgear (on the cable modem screenshot I see a menu item "client list", maybe its there.)
Then log into the netgear with the IP address it got from the cable modem and then change it to an IP address OUTSIDE the ip range.

---

### Post by robertzito on 2015-04-25
I just can not get my head around this!

I have tried all suggestions and can not get it to work, where I am confused is why would I set the range of available IP!

This is the part I don't understand: 

[COLOR=#000000]**Then log into the netgear with the IP address it got from the cable modem and then change it to an IP address OUTSIDE the ip range.**

Give me an example, are you saying it should be outside of the range of IPs, because if lower the IP's to lets say 100, when I set the slave router to 101 the cable router will be able to communicate with it?[/COLOR]

---

### Post by robertzito on 2015-04-26
Today I was able to dedicate some time and nailed it! Where I was totally unaware that I could go from lan to lan, thought it had to be lan to wan, so now I have all the kids on the old routers SSID and I am able to block sites and do filtering without it impacting me because I use the cable modem with router. I will look to see if putting the kids on one router with about 16 wifi devices (phones, games, tablets) give me better performance because I am the only one on the newer SSID, the only wired connection is the printer and now they can all reach it from their network 

[http://www.linksys.com/us/support-article?articleNum=132275](http://www.linksys.com/us/support-article?articleNum=132275)

---

