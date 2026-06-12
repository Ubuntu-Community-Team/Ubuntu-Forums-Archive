---
title: "TRENDnet TEW-501PC works 'partialy'"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by ksz on 2007-04-21
System is Feisty. Laptop - Acer TravelMate 292ELC.
Card's driver loaded, I can configure it via nework-manager and console tools. My home network is recognized and connected. But I can't ping AP and of course any thing else..
On WinXP card works fine on the same config.. I have no idea now, what's the problem.. :confused: 
Help please! ;-)

Some commands outputs:

**lspci**
```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
```

**lsmod|grep ath**
```
ath_rate_sample        14080  1
ath_pci                97312  0
wlan                  204484  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
```

**dmesg|grep ath**
```
[   29.344000] ath_hal: module license 'Proprietary' taints kernel.
[   29.348000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   29.588000] ath_pci: 0.9.4.5 (0.9.3)
[   30.432000] ath_rate_sample: 1.2 (0.9.3)
[   40.704000] ath0: no IPv6 routers present
[ 5479.808000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 5490.268000] ath0: no IPv6 routers present
[ 5614.588000] ath0: no IPv6 routers present
[ 6175.092000] ath0: no IPv6 routers present
[10950.960000] ath0: no IPv6 routers present
```

**ifconfig**
```
ath0      Link encap:Ethernet  HWaddr 00:0E:8E:01:D0:1D
          inet6 addr: fe80::20e:8eff:fe01:d01d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:18583 (18.1 KiB)  TX bytes:18583 (18.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0E-8E-01-D0-1D-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:63
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:9720 (9.4 KiB)  TX bytes:10002 (9.7 KiB)
          Interrupt:10
```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"ksz_r"  Nickname:""
          Mode:Managed  Frequency:5.66 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=67/94  Signal level=-23 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**iwlist ath0 scanning**
```
ath0      Scan completed :
          Cell 01 - Address: 00:4F:62:0B:DE:D7
                    ESSID:"ksz_r"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/94  Signal level=-25 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
```

---

### Post by ksz on 2007-04-23
Come one! No one can't help? :(

---

### Post by ksz on 2007-05-07
**apt-get remove network-manager* **
and manual config by ifconfig/iwconfig helped :-?

---

