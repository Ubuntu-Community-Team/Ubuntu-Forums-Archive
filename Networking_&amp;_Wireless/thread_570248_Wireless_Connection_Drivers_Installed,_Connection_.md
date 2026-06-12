---
title: "Wireless Connection: Drivers Installed, Connection Made, IP Acquired...no Internet..."
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by Hexydes on 2007-10-08
Hey all,

Ok, so I finally got sick of this old laptop with Windows XP on it crashing when playing movies. I use Ubuntu on my main desktop, but hesitated to install it on my laptop because it is wireless. Well anyway, I took the plunge. It is an older laptop, so I threw Xubuntu on it.

I have a Trendnet TEW-226PC wireless card. It of course was not recognized after installation, fine, no problem. I installed ndis-utilities, as well as a driver that was said to work with the card. There was no wireless connection listed before that, afterwards, wireless connection was an option in network prefs. Also, the card has two lights on it, PWR and LNK, of which PWR has always been on, LNK came on after I installed the driver and NDIS.

Now, I am assuming since I have a light and wireless is listed as an option, at least the hardware is working, right? I set it to DHCP, told it to hook up with my SSID (no encryption), and said to enable the connection. I now get an IP address for the device (x.x.x.8), as well as one for my wired connection (x.x.x.7).

Problem: When I don't have wired plugged in, I get no Internet. I cannot ping any other devices on my network. It shows I have an IP coming from DHCP that makes sense on the network, but I can't ping, and no Internet. When I plug wired back in, everything goes back to working. Unplug, doesn't work anymore.

Any thoughts as to what the problem is here? I ran an ifconfig in terminal, here is what I came up with:

```

eth0      Link encap:Ethernet  HWaddr 00:20:E0:6C:C1:AE  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:e0ff:fe6c:c1ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13850427 (13.2 MiB)  TX bytes:749652 (732.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5606 (5.4 KiB)  TX bytes:5606 (5.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:9E:B2:56  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe9e:b256/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10955 (10.6 KiB)  TX bytes:4482 (4.3 KiB)
          Interrupt:11 Memory:24000000-24000100

```

Thanks!

EDIT

P.S. I blanked the IPs so that just the pertinent number is seen. Obviously you can see the full IP in the code (generic 192.168 range)

---

### Post by noob12 on 2007-10-08
You have eth0 and wlan0 up and on the same subnet and this can cause problems both with ARP and your default gateway.

If you are using NetworkManager, I'd suggest that you reduce your /etc/network/interfaces file so that it contains only the initial  loopback (lo) section (i.e. just):
```

auto lo
iface lo inet loopback

```
This is equivalent to putting them in roaming mode (and also removes the configs for interfaces you don't actually have).

Then reboot.  See if things are better.

---

### Post by Hexydes on 2007-10-08
No luck. Now my wireless connection doesn't even show up in the Network Manager list. :confused:

---

### Post by kevdog on 2007-10-08
Can you post the following:

lspci -nn
lshw -C network
iwlist scan

---

### Post by Hexydes on 2007-10-08
Oooooook.....and now I just went in and disabled the wired connection from the manager and it seems that wireless Internet is now working.

Which may jive with what you said previously, perhaps I just needed to leave the wlan info in there? Oh well, whatever, this is a portable media computer, connecting only with wireless, so I'll just live with that. Thanks! :)

---

