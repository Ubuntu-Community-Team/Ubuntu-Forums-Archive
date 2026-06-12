---
title: "wireless problems - liksys card"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by chrisb62 on 2007-11-03
here is the info. 

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:9A:4E:1A   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0_rename  IEEE 802.11b  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:9A:4E:1A   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-60 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:191  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:52   Missed beacon:0

```

/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp
wireless-essid linksys
#	 wireless-* options are implemented by the wireless-tools package
#	wireless-mode managed



iface eth0 inet dhcp

auto eth1

auto eth0

```

according to the light on the card it has a connection. iwconfig says it see's my linksys router.

in the applications>system>network window, i went into properties, and was actually able to select "linksys" from the list, so it obviously sees it. ive tried restarting after each change. and even just restarting the network services. but still doesnt seem to work.

it works fine with a wired connection. any help would be appreciated. thx!

---

### Post by rickdog on 2007-11-03
I had a friend that had trouble accessing their linksys router and I worked and worked on it until I realized that at least 5 neighbors in the near vicinity had linksys routers with "linksys" as the network name. I wired in, changed the name to something else, set up WEP and got on wirelessly without a problem after that.

That's all I got. Good luck.

---

### Post by chrisb62 on 2007-11-03
i dont think that is case here. it worked without issue before when i had xp installed. never picked up any other wireless signals before.

---

