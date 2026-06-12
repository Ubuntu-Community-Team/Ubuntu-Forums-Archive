---
title: "Wireless DHCP Not Working"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by Neon_c on 2008-07-02
I'm using Ubuntu Studio. Just set up my Netgear WG111v3. Everything works when i set it up for a static IP but when i tell it to use DHCP everything stops working. I'm Really Really rusty at UNIX and a brand new Linux n00b. I'm running off of a Linksys wifi router with DHCP range above address 100. I have no control over it because it's not mine. however all of my other wireless devices work aswell as my stepbrothers Linux PID.

Any help would be great. if i'm leaving anyhthing out please ask!
Neon

---

### Post by Neon_c on 2008-07-04
Still no luck. Also it isnt working when pluged into a hard line either! Please help!

Something seems funny when i look run an ifconfig. There is no ipv4 address being assigned. Is it not looking for an ipv4 address? my network dose not support ipv6.
```

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:c5:9f:1d  
          inet6 addr: fe80::21b:2fff:fec5:9f1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1228934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:674394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1048671334 (1000.0 MB)  TX bytes:47623787 (45.4 MB)

```

---

### Post by Threbus5 on 2008-07-04
Hmmm.
Usually, DHCP will work more easily than fixed IP.
What was the result of resetting it to the fixed IP?
If that still works, examine the configuration settings and compare them to the DHCP. 

Determine whether the network is open or closed. DHCP is nice for open nets but firewall configurations and passwords need setting on private networks.

Also, verify that the default connection uses the intended card instead of something else such as a modem or a different network card in the same machine.

Remember that it is possible to configure to have a wireless and wired card active simultaneously. I usually engage one at a time.

Regarding the ipv4 and ipv6, do a search on enabling each.
However, the recent disappearance of hard wired connectivity suggests investigating whether both cards are active simultaneously. I may be conservative, but I usually enable only one at a time.

Good luck.

---

### Post by Neon_c on 2008-07-04
> **Threbus5 said:**
> Hmmm.
Usually, DHCP will work more easily than fixed IP.
What was the result of resetting it to the fixed IP?
If that still works, examine the configuration settings and compare them to the DHCP. 

Determine whether the network is open or closed. DHCP is nice for open nets but firewall configurations and passwords need setting on private networks.

Also, verify that the default connection uses the intended card instead of something else such as a modem or a different network card in the same machine.

Remember that it is possible to configure to have a wireless and wired card active simultaneously. I usually engage one at a time.

Regarding the ipv4 and ipv6, do a search on enabling each.
However, the recent disappearance of hard wired connectivity suggests investigating whether both cards are active simultaneously. I may be conservative, but I usually enable only one at a time.

Good luck.

Once i got NDISWrapper working with my wireless card i disabled my hard wire NIC. the wifi works fine without DHCP. In fact i'm using my static ip-address to make this post.

this is what ifconfig gives me when i'm on a static IP:
```

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:c5:9f:1d  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fec5:9f1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9501 (9.2 KB)  TX bytes:13712 (13.3 KB)

```

i notice that there is a difference when i'm running static i have
inet addr: 192.168.1.18
when i'm on DHCP that line is missing and all i have is 'inet6 addr'

i'm still quite a linux n00b and all of my other unix experiance is rusted solid.

My network right now is 100% open. (step dad didn't bother with passwords, firewalls or encryption)

---

### Post by Neon_c on 2008-07-05
Ok! IpV6 was the culprit!

What i did was this,

```

sudo pico /etc/modprobe.d/aliases

```

then i find the line that says

```

alias pf-net-10 ipv6

and change it to

alias pf-net-10 off

```

than i restarted the network services. (or you could just restart the machine)

---

