---
title: "FTP works but not HTTP?"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by GummiBj on 2007-12-13
Hello. I posted this question on Kubuntu but so far no one has replied, I presume that means that they don't know the answer to the question. Here it goes: 

I am running Kubuntu 7.10 on an Fujitsu/Siemens laptop. It has a SiS191 ethernet card and a Atheros(i think) wlan card connecting to a Dreytek 2800 router. I have gotten to the point where I have the driver installed through ndiswrapper and as far as I can see this works. I can work through FTP but try as I may I cannot get WWW or kopete to work, the packet seems to go out to the router because I can see the light on the router blinking regularly but nothing is coming back to my system. HTTPing says that there is error in receiving the packets and a 100% loss. 

So far I have tried everything I can think of.
- I have disable the firewall through guarddog. If I nmap the router it says that port 80 is open, but if    I nmap localhost it says that this is closed (does this matter because on my desktop system it is also closed but WWW works fine)
- I have tried numerous dns combinations in my resolv.conf including the Virgin DNS servers (right now it only has one line and this is "nameserver 192.168.1.1"
- I have put 192.168.1.1 router.local (for whatevever reason) into the hosts file
- the interfaces file has wlan as "iface inet wlan0 dhcp"

At first I thought that it must be a DNS problem but why should the FTP protocol work. Then i installed xinetd because I thought this might have something to do with this, although I have not made any adjustments to the basic setup.
Knetworkmanager will not recognise the card, I have installed and reinstalled again but to no avail. I guess I might try purging the files but then again...

It seems to be a case of everything lookes like it works but there is something that isn't,

Am I missing some magic Ubuntu file that would solve all my problems? Do I need a special dns program for the whole puzzle to click together? Or is this some kind of conflict in resources.

The only hint came out of /var/log/syslog which say that something like this:

Dec  9 11:18:46 Laptop kernel: [  279.988000] wlan0: no IPv6 routers present

What does this mean? I think the router is logged as IPv4 but the system settings are a mixture of both. Does this have anything to do with this, I have really no clue about IPv6 or for that matter IPv4.


Help!
Gummi

P.S. since I posted this thread on Kubuntu I also tried using the live-cd version of Kubuntu and Ubuntu and installing the ndiswrapper driver in the live version. In Kubuntu this resulted in excactly the same problem even through I hadn't changed any programs apart from removing the restricted drivers and installing the driver for my Ethernet card. I couldn't even install the ndiswrapper driver in Ubuntu because ndiswrapper-utils isn't on the cd. I have also tried to work with port scanners but I don't really know what I am doing so that didn't give me very much. I have read the networking howto but got just as much out of that as trying the scanners. 

Anyway, I hope that I have some luck here. I tried about 6 different live cd distros and Kubuntu was the only one that got close to "just working" so I have high regards for it.

Gummi

---

