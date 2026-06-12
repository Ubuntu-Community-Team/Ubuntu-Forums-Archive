---
title: "wirless on lenovo tablet"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by BenWhitey on 2007-05-21
I'm trying to get my wifi to work on my lenovo tablet.  I've tried a lot and I can't seem to get something to work.

```

ben@ben-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=17/94  Signal level=-71 dBm  Noise level=-88 dBm
          Rx invalid nwid:1450  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

```

```

ben@ben-laptop:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:06:25:F7:C8:6A
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/94  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

```

```

ben@ben-laptop:~$ netstat -nr -4
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

Thanks!  Just ask me if you want more stuff.

EDIT:
```

           *-network
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@03:00.0
                logical name: wifi0
                version: 01
                serial: 00:19:7e:35:c7:15
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.14 latency=0 multicast=yes wireless=IEEE 802.11a
                resources: iomemory:edf00000-edf0ffff irq:21

```

---

### Post by jglen490 on 2007-05-21
Everything is good, just need to configure the actual connection between the card and the router (i.e., WEP, WPA) using a GUI tool such as network-manager, wlcd, or manually configure the /etc/network/interfaces file.

---

### Post by BenWhitey on 2007-05-22
This is my interfaces file.  I think I may have screwed it up by accident.

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
 
auto eth0
iface eth0 inet dhcp
 
auto eth1
iface eth1 inet dhcp
 
auto eth2
iface eth2 inet dhcp
 
auto ath0
iface ath0 inet static
address 192.168.1.35
netmask 255.255.255.0
broadcast 255.255.255.0

auto wlan0
iface wlan0 inet dhcp

```

The network I am trying to connect to is not encrypted.

Thanks!

---

### Post by BenWhitey on 2007-05-26
My problem stems form a bug in the madwifi driver.  [http://madwifi.org/ticket/1343](http://madwifi.org/ticket/1343)

---

