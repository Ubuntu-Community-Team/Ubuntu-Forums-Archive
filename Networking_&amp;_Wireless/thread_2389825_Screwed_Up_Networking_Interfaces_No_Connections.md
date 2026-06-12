---
title: "Screwed Up Networking Interfaces: No Connections"
date: 2018-04-21
forum: Networking &amp; Wireless
---

### Post by amtraq on 2018-04-21
Hey everyone, I have been trying to set up an OpenVPN server on my machine running 16.04. I had previously made some setting changes configuring Apache on the same machine. 

Anyway this is where I am:

[LIST]
[*]Network manager on system tray at top says "wifi networks \n device not ready" and does not show any wireless networks!!! 
[*]It also says that I have a wired connection "Wired connection 1" (which I do, but I am still not getting internet access) 
[*]I made some changes in my iptables and in my /etc/network/interfaces file but I reverted them (command used: sudo iptables -F) to default with no success 
[*]I un-installed network manager and installed WICD which did show wireless connections but still no internet so I uninstalled it 
[*]I reinstalled network manager, I think my biggest mistake was removing network manager, and ran "nm-applet" 
[*]Network manager is up and running but it seems to me that I screwed up something with my wifi card interface or something 
[*]/etc/network/interfaces file: 
[/LIST]

```
auto lo
iface lo inet loopback
```


[LIST]
[*]-"ifconfig -a" output: 
[/LIST]
```
en2ps0
Link encap:Ethernet
inet addr:192.168.0.142 Bcast: 192.168.0.255 Mask: 255.255.255.0
UP BROADCAST RUNNING MULTICAST 
RX packets:13608 errors: 0 dropped: 0
TX packets:69691 errors: 0 dropped: 0

lo
Link encap:Local loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
UP LOOPBACK RUNNING

wlp3s0
Link encap:ethernet
inet addr: 192.168.0.103 Bcast...
UP BROADCAST RUNNING MULTICAST MTU:1500 
RX packets: 39465 errors: 0
TX packets: 7119 errors: 0

```


[LIST]
[*]"lspci -nn | grep -i network": Qualcomm Atheros AR9462 Wireless Network Adapter 
[*]"lspci -k | grep -i network -A 2": Driver in use: ath9k 
[*]"rfkill list -a": no blocks 
[/LIST]


-BUT when I run **iwconfig** it says that **wlp3s0 is connected to my wireless network** 
```
wlp3s0 IEEE 802.11 ESSID:"insert network here"
Mode:managed 
Bit rate=28.9 Mb/s
Retry short limit: 7   RTS thr: off   Fragment thr: off
Power management: off
Link quality=70/70
...Invalid misc:5240
```
I have tried everything that I know, and am tired of searching around the net for answers that are unrelated so I'm coming to you guys! Please help me, I just wanted to set up a static ip (easy right? I thought so too), and configure my PC to run as an OpenVPN server (which required me to change /network/interfaces.

---

