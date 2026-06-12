---
title: "Need help connecting to wireless network, Averatec 2260-EK1"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by kernco on 2007-07-17
I'm trying to get my wireless working in Ubuntu 7.04 on my Averatec laptop.  I believe the wireless chipset is rt73 (ralink).  In the network manager panel applet, it detects my wireless network, but when I select the network, it never connects.  The network has no WPA or any other type of security, it is completely unsecured.

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.462 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:11:54:23:BF   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Something seems strange about the output of netstat:
```

~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 wlan0

```
I have a d-link router whose IP address is 192.168.0.1. This appears as my gateway for the eth0 interface, which works fine.  My gateway for wlan0, though, is 0.0.0.0.  Could this be the problem? How do I configure it to use the right gateway?

---

### Post by mrsticks on 2007-07-17
I think this version of the network app has an issue with the ralink driver, especially when it comes to wireless networks and joining them.
You can still setup your wifi through the network manager, but youll have to do it manually.  Manually choose the wifi AP.  You should still be able to get a dynamic IP though.  

I dont have a laptop in front of me though, so I cant be of too much more help. Sorry!

-peter

---

### Post by MarkusRTK on 2007-08-06
Ralink wireless chips are a pain (I just went through this on my Averatec 3250). Try uninstalling network-manager altogether, as it often doesn't play well with a Ralink, and just configure with ifconfig and/or the default Gnome tray applet; also, try blacklisting the ipv6 module (you'll never need it anyway), since it might interfere with your DHCP. Those two strategies, used in tandem, worked for me anyway. (I have an RT2500, though, which might be different from your RT73.)

One other thing -- does your Averatec, like mine, have a wireless button? If so, try *not* pressing it, as Linux doesn't quite get Averatec's ACPI. On my system, my wireless only works if the switch is off (and the little wireless light is not on); if the switch and the light are on, it claims to be connected but can't receive any data (kind of like your situation, actually).

---

