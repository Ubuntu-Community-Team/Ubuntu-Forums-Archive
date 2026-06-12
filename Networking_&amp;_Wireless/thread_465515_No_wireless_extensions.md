---
title: "No wireless extensions"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by parrimin on 2007-06-05
Hi all,
I have in my laptop a Prism 2.5 Wavelan Chipset. It wasn´t running since i upgraded to feisty but fixed it installing linux-wlan-ng and rebooting. I dont know what i did, but if i type iwconfig, it says:
> lo     no wireless extensions
eth0    no wireless extensions
wlan0    no wireless extensions

It´s not a great problem because in network-manager i can see the different networks and connect. But today i was tryin to test aircrack, and interesting program... but i cant do the first step to make it run. I cant do iwconfig wlan0 mode monitor, because it says there is no wireless extensions. Anybody knows how to solve this?

---

### Post by jglen490 on 2007-06-05
Try ifconfig and also look in the file /etc/network/interfaces to see what interfaces have been configured.

---

### Post by parrimin on 2007-06-12
Hi jglen,
Hmmm, it seems i havent fixed my prpoblem. Can you explain what have i to do to  have network-manager run properly?
I was unable to connect to any connections listed. So I tried to connect manually. When i tried to configure manually, i couldnt see the tab where you can select SSID, i only was able to say it have DHCP. After rebooting, i went to system->administration->networking, and i was able to see the SSID, and connected manually. All OK, and if i type iwconfig in console, there is wlan0 configured all OK.
Now i want network-manager to work, but... with wlan0 activated (from system->administration->networking), I can see any wireless option in network-manager. If in manual configuration i check a checkbox that says... i cant remember (something like activate ... mode)... Network-manager seems to be running ok, with options to change to another wireless connection, but no SSIDS are available, I can´t see any SSID, and cant connect to any of them if i type manually the name. What am I doing wrong?

---

### Post by nbayiha on 2007-06-12
Actually i have the same problem , when i put iwconfig , i have 
```
lo        no wireless extensions.

eth0      no wireless extensions.


```
and when i open my  
 /etc/network/interfaces i have this
 ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

 what am i suppose to modify or to add to this , cause there is a lot of thread about making my wirelless card work but the problem is i can't follow them if my system  don't even see my wireless card.

And help is really needed.:(

PS; actually i'm using hp dv6040us and my wireless is Broadcom 4311 but like my wireless card isn't seen

---

