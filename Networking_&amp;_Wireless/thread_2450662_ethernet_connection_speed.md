---
title: "ethernet connection speed"
date: 2020-09-18
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2020-09-18
Hi all, 

I don't know about hardware to much, so I asked guys from computer shop to install gigabit pci ethernet card. They looked into it and answered that my built-in ethernet is gigabit already. So I bought gigabit router (tplink archer c7 if matters), but wired connection information still says that my speed is 100 Mb/s. How do I fix that? Also I'm not sure how to check my built-in ethernet card specification in ubuntu.
Please advise.

[IMG]https://i.postimg.cc/8zcL97jZ/ethernet-info.png[/IMG]

---

### Post by CelticWarrior on 2020-09-18
Welcome.

'lspci' will give you information about all "PCI bus" devices and that should include your onboard Ethernet. And yes, almost all nowadays are 1000...

Now, you should check the router's settings -and- the cables you're using.

---

### Post by poorguy on 2020-09-18
Most internet speed is determined by type of internet and the speed of the internet card.
What type of internet package do you have.

I have a standard fiber internet and my speed is 100 Mbps up and 100 Mbps down.

My Ethernet card shows to have the ability to run up to 1000 Mbps

Run **fast.com** in your URL search bar and see what your actual speed is.

```


Network:   Device-1: Broadcom and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe vendor: Dell driver: tg3 
           v: 3.137 port: 0980 bus ID: 05:00.0 
           IF: enp5s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Broadcom and subsidiaries NetXtreme BCM5761 Gigabit Ethernet PCIe vendor: Dell driver: tg3 
           v: 3.137 port: 0980 bus ID: 06:00.0 
           IF: enp6s0 state: down mac: <filter> 


```

---

### Post by TheFu on 2020-09-18
Check that the cable is CAT5e or better and that the router port is GigE.  If the cable is over 10 yrs old, it probably isn't CAT5e.  There's little reason to get CAT6 cables, so even if the price difference is $0.50 between CAT6 and CAT5e, I'd get the CAT5e one, even for very long cable runs across a house.

Also, move the cable from 1 port to another on the router. Sometimes, router/switch ports fail.

```
$ inxi -n
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: eth0 state: up speed: 1000 Mbps duplex: full 
```

BTW, IP addresses aren't private. The one used on your LAN is useless for anyone else. The public IP that your router has is only slightly interesting, but it is public too. The MAC would be a larger concern.

Testing between 2 physical systems here using iperf3, I see:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.20 port 59838 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   113 MBytes   950 Mbits/sec    0    262 KBytes       
[  4]   1.00-2.00   sec   113 MBytes   945 Mbits/sec    0    274 KBytes       
[  4]   2.00-3.00   sec   112 MBytes   **940 Mbits/sec**    0    274 KBytes  
```
But testing using speedtest-cli ... I see only:
```
$ speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Selecting best server based on latency...
Hosted by Hotwire Fision (Atlanta, GA - Ya'll) [42.77 km]: 15.677 ms
Testing download speed........................................
Download: [B]25.34 Mbit/s
[/B]Testing upload speed..................................................
Upload: **5.94 Mbit/s**
```

So, it is clear that my fast, GigE LAN doesn't help at all with internet speeds.  I'd be just as happy with 100 base-tx connections if I only had 1 computer.  Because I have multiple systems and they all communicate between each other, the LAN performance matters.

In short, worry about things that actually matter.

---

### Post by marchello_lippi2 on 2020-09-20
Thanks to all, will try different port and modern cable.

---

