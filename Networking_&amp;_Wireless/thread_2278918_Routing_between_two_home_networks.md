---
title: "Routing between two home networks"
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by paul68 on 2015-05-19
Hi,

I have a home router and two devices - 192.168.1.8 (device A) and 1.236.230.154 (device B). They're both connected by wire to the same router but for some reason are not on the same network/subnet.

I want to be able to connect between the two devices. I can ping device B from device A but vice versa doesn't work. I can't ssh or from device A to B or anything else.

I know I need to either add a route to both devices or forward using NAT but I have no idea of the right command to issue. I've tried commands like:

```
sudo route add -net 1.236.230.0/24 gw 1.236.230.153
``` 

To add a route from device A to B but I get "SIOCADDRT: Network is unreachable".

Any ideas? I would greatly appreciate any help!!!

---

### Post by Keith_Helms on 2015-05-19
What kind of "devices" are these?  Are they both PCs?  It sounds like you have an IP address hard-coded for Device B instead of letting the router's DHCP function assign one to it.

---

### Post by SeijiSensei on 2015-05-20
1.236.230.154 is a public address [belonging to]("https://wq.apnic.net/whois-search/static/search.html?query=+1.236.230.154") SK Broadband Co Ltd, Jung-gu SK NamsanGreen Bldg,Namdaemunno 5(o)-ga, Seoul.  You shouldn't be using it on any internal networks.

---

### Post by paul68 on 2015-05-20
That's really strange. It's assigned the public IP to my LAN connection:

```
p1p1      Link encap:Ethernet  HWaddr 94:de:80:85:f4:48          inet addr:1.230.236.154  Bcast:1.230.236.159  Mask:255.255.255.224
          inet6 addr: fe80::96de:80ff:fe85:f448/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128858745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114651195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:129568809703 (129.5 GB)  TX bytes:114593131179 (114.5 GB)
```

---

### Post by SeijiSensei on 2015-05-20
Is "device B" running Ubuntu?  If so, do you have a static IP assigned in /etc/network/interfaces for it? Is the device configured to use DHCP?  Unless you have some specific need to use static addressing, all the devices behind the router should be using DHCP.  If you do use a static address, it needs to be in 192.168.1.0/24.

---

### Post by paul68 on 2015-05-20
both devices are running ubuntu. 

The problem was my router. One of the ports is configured for IPTV and when the technician installed the internet he plugged one of my devices into it (it looks like the IPTV port connects directly to the internet and bypasses the internal LAN).

---

