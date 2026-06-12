---
title: "wlan0: link is not ready"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by finneces on 2008-01-01
Im trying to set up my Ubuntu desktop as a wireless server for other computers in the house.  I got a Fritz WLAN USB, tried the native linux driver, ended up going to the ndiswrapper for the windows driver (the only possible way).  Then I used this webmin tool to set it up as a server (after failing to achieve this by hand).  The problem is that the usb WLAN device is loaded and running:

```
ndiswrapper -l
fwlan64 : driver installed
        device (057C:6201) present
```

```
ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:1C:4A:F0:86:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:1C:4A:F0:86:72  
          inet addr:169.254.7.211  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```

But I cant connect to it from my laptop and in /var/log/messages I see "link is not ready"!
```
Jan  1 18:50:13 matt-desktop kernel: [   37.923322] wlan0: ethernet device 00:1c:4a:f0:86:72 using NDIS driver: fwlan64, version: 0x2000c6f, NDIS version: 0x501, vendor: 'AVM FRITZ!WLAN USB Stick', 057C:6201.F.conf
Jan  1 18:50:13 matt-desktop kernel: [   37.923364] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
Iv been banging my head over this problem for two days non stop, so I would really appreaciate any help from someone who has been able to do this, or knows what Im doing wrong.  

Just in case it helps, here is my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#pre-up iptables-restore < /etc/iptables.conf

auto wlan0
iface wlan0 inet dhcp
wireless-mode master
wireless-essid "FliegendesSpaghettimonster"

```

Please help!

---

### Post by harak on 2008-02-24
I have the same problem. But If i manually switch the card on using the button on my lappie I am able to connect to the internet/router. I would not prefer to use the switch everytime I start the comp. I hope somebody would help me in this.

---

