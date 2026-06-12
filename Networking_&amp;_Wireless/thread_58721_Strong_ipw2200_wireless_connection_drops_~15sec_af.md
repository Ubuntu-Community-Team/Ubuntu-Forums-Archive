---
title: "Strong ipw2200 wireless connection drops ~15sec after connecting (dhclient fixes it)"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by staeiou on 2005-08-21
**Fixed it. If I have eth0 (wired ethernet) up, both of them screw up. If I ifdown eth0, then ifdown/ifup eth1, it works fully. Thanks for the driver update though.**

Computer:
IBM X41 Thinkpad with ipw2915 (using ipw 2200 driver).  Connecting to a WRT54G router.  When I run dhclient, or ifup, I get an IP address, and I can ping / visit websites / etc.  However, 5 to 30 seconds after I send/recieve my first packet of data, the connection drops.  The wireless LED continues to blink, but all packets are being lost. Ifconfig still reports that I have an IP address, and iwconfig reports that I've got a strong signal to my essid (88/100).  No encryption being used.


iwconfig eth1
```

eth1      IEEE 802.11g  ESSID:"nethack"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:95:D9:36 
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-41 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

```

ifconfig eth1
```

eth1      Link encap:Ethernet  HWaddr 00:12:F0:C8:99:27
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fec8:9927/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1279 errors:0 dropped:7 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34469010 (32.8 MiB)  TX bytes:1514418 (1.4 MiB)
          Interrupt:21 Base address:0x6000 Memory:a0202000-a0202fff



```

cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
iface eth1 inet dhcp

```

Thanks.

---

### Post by luca_linux on 2005-08-21
You should really update the ipw2200 driver: the one included in Ubuntu is obsolete (version 0.19) while the latest version is 1.0.6.
Here's a HowTo: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623). Just follow the first part if you're not interested in WPA.

---

### Post by staeiou on 2005-08-21
Well, I updated the driver, and the same thing happened (or didn't happen, depending on how you look at it)

---

### Post by staeiou on 2005-08-21
Fixed it.  If I have eth0 (wired ethernet) up, both of them screw up.  If I ifdown eth0, then ifdown/ifup eth1, it works fully.  Thanks for the driver update though.

---

