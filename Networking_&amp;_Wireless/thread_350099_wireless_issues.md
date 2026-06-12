---
title: "wireless issues"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by TheAlmightyNilz on 2007-01-31
I would like to set it up so that when I travel to different wireless networks, it will automatically connect to them and grab an IP and all that. In fedora core 6, network-manager-gnome worked for this, in ubuntu, it does not. network-manager-gnome just says disconnected.

wireless works fine as long as I do a dhclient wlan0 when i log in, but that is getting old.

interfaces:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

auto eth0
iface eth0 inet dhcp

```

iftab:

```

eth0 mac 00:E0:B8:B8:51:FC  arp 1
wlan0 mac 00:14:A5:EA:1B:E7 arp 1

```

I'm using ndiswrapper. 
ifconfig: (after issuing dhclient wlan0)

```

eth0      Link encap:Ethernet  HWaddr 00:E0:B8:B8:51:FC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:EA:1B:E7  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:feea:1be7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4281697 (4.0 MiB)  TX bytes:461575 (450.7 KiB)
          Interrupt:50 Memory:c0300000-c0304000 

```

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:A0:2A:3A   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by TheAlmightyNilz on 2007-01-31
Anybody at all have an idea?

---

### Post by Floppyjoe on 2007-01-31
Do you have all your network interfaces disabled in System/Administration/Networking?
This is required for Network Manager to work. You probably do but that is the only thing that comes to my mind.

---

### Post by TheAlmightyNilz on 2007-02-01
I disabled the network devices in the networking window, network-manager-gnome still says no network connection, no network devices found. wireless works, i am posting this right now via the wireless connection i just had to do the dhclient thing.

---

### Post by Floppyjoe on 2007-02-01
Did you restart the computer after making this change?

---

### Post by TheAlmightyNilz on 2007-02-01
yes i did, no different.

---

### Post by TheAlmightyNilz on 2007-02-01
gave up on gnome-network-manager, removed and installed dhcpd (somehow it broke, it didn't even work when wired) again and network-laptop and now it finds the ssid automaticlally on bootup and grabs an IP. so this problem is fixed, sort of. just have to reboot when entering a new network.

---

