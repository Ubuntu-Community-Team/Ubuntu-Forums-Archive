---
title: "Wireless doesn't connect with Accesspoint"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by joojle on 2007-06-25
my wireless was work with my computer but when i use it to connect to the wireless network. it isn't get IP address from the network. This is my log in that time
```
[ 5430.312996] wlan0: starting scan

[ 5431.223486] wlan0: scan completed

[ 5479.356990] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[ 5484.373676] wlan0: Initial auth_alg=0

[5484.373685] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5484.572952] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5484.772657] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5484.972362] wlan0: authentication with AP 00:16:b6:4f:53:d8 timed out

[ 5489.372609] wlan0: Initial auth_alg=0

[ 5489.372619] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5489.569592] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5489.769300] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5489.777287] wlan0: no IPv6 routers present

[ 5489.969005] wlan0: authentication with AP 00:16:b6:4f:53:d8 timed out

[ 5494.371050] wlan0: Initial auth_alg=0

[ 5494.371060] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5494.570232] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5494.769937] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5494.969644] wlan0: authentication with AP 00:16:b6:4f:53:d8 timed out

[ 5499.369857] wlan0: Initial auth_alg=0

[ 5499.369867] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5499.566873] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5499.766582] wlan0: authenticate with AP 00:16:b6:4f:53:d8

[ 5499.966288] wlan0: authentication with AP 00:16:b6:4f:53:d8 timed out

```

---

### Post by lslayer on 2008-05-02
Yeah, the same trouble. 
```
01:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

```
[ 1889.488053] wlan0: Initial auth_alg=0
[ 1889.488059] wlan0: authenticate with AP 00:1c:f0:e3:6f:d3
[ 1889.488151] wlan0: Initial auth_alg=0
[ 1889.488153] wlan0: authenticate with AP 00:1c:f0:e3:6f:d3
[ 1889.687837] wlan0: authenticate with AP 00:1c:f0:e3:6f:d3
[ 1889.887815] wlan0: authenticate with AP 00:1c:f0:e3:6f:d3
[ 1890.087791] wlan0: authentication with AP 00:1c:f0:e3:6f:d3 timed out

```

:(
Have any ideas?

---

### Post by geezerone on 2008-06-04
Any solutions??

---

### Post by Fingel on 2008-07-14
I'm having this same problem, using the iwl3945 driver. Never connects to access point, just keeps saying authentication timed out. This pretty much makes my laptop useless, any help would be appreciated.

---

### Post by geezerone on 2008-07-14
What signal strength are you getting? I have found the same problem with signal strength of 50% or less. Also, try a different channel number on your AP.

---

