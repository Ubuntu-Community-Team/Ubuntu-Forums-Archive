---
title: "Slow wireless/ethernet only on home network"
date: 2018-10-05
forum: Networking &amp; Wireless
---

### Post by jjd7 on 2018-10-05
Hello, 

I am new to the forum but I havent't seen this specific problem yet. I am running ubuntu 16.04 on 3 different computers. All three computers have slow internet speeds (cap out at about 3.4 MiB/s) only on my home network. When I connect the networks at work, the speed is fine which makes me think it maybe isn't a driver issue but something with my home network? Additionally, since I have 3 different compters with the same issue, I don't believe it is specifically HW related. One of my computers (Dell precision M5500) is also running windows, and when I boot to windows, my speeds jump to about 25 MB/s which is about the max internet speed I get. 

The three computers (all with the same slow internet in ubuntu at home but not at work) are 
Dell Precision M5500
Lenovo W540
and Asus UX305U

Is there something with the way my LAN is configured that is not playing nice with Ubunut?

---

### Post by TheFu on 2018-10-05
> **jjd7 said:**
> 
Is there something with the way my LAN is configured that is not playing nice with Ubunut?

Yes.  How is your LAN setup?

---

### Post by jjd7 on 2018-10-07
Not sure what you mean by how my LAN is set up but basically I have home wifi networks (both 5G and 2.4G bands) and most devices are connected that way. I have found that either wireless or wired connections do not work well in ubuntu though. Most of my router configuration is default though so I'm not sure where I should look. It is setup with DHCP, and nothing is static at the moment. Default firewall settings as well.

---

### Post by TheFu on 2018-10-07
Wifi?   Wired is always better.  Always.
Never enable both wifi and wired at the same time.  That will mess up routing.

From each machine, you should be able to 'ping' the others using the hostname when a network is setup correctly. 

As for making wifi work better, start by knowing the capabilities for each device.  There's a wifi-scan script  or wifi-info in these forums.  Run that and post the URL it creates.  I can only help with wifi hardware I know.  If you have any older wifi devices connecting, those often will force the entire network to drop back to that slower speed.

Simplify and test.  Disconnect and power off the wifi on  all but 1 device. Don't forget TVs and media players and those things we talk at.  Test.
Keep simplifying and testing until you've determined the system with / causing the problem.

Servers need to have static IPs on the LAN.  You can do that in the configuration or using DHCP reservations. Many routers will do that.  NEVER have the same IP used for wifi and wired connections.

You didn't say how you are trying to connect between the systems.  Because Linux is 1,000x more flexible than Windows, it needs to know what you intend. Plus, Linux talks IP by default. IP doesn't yell on the network "I'm here, I'm here." like other OSes do.  If you want the best solution for Linux, each of the systems need to know about each other - hostnames, IPs, and protocols.

For a small network, a central router might be able to handle running an internal DNS server and DHCP reservations so each machine can 'ping' the other machines using the hostname.  If that isn't working, then the network management needs to be fixed.   Remember, Linux is designed to be internet-scale - 100,000+ servers, all working together.

Gotta head out now.

---

### Post by alcotross on 2018-10-08
Hey! anyone can help me, I having an issue with configuration of [netgear arlo support]("https://www.netgearroutersupportnumber.com/netgear-arlo-support/") security camera, I am using Linux Ubuntu I want to manage my camera with my Laptop wi-fi network. Is it any requirement of any driver installation. Then please share driver name or link.
Thanks a lot!!!

---

