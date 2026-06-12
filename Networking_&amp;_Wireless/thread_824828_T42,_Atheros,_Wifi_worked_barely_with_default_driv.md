---
title: "T42, Atheros, Wifi worked barely with default drivers, not at all after trying madwif"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by tmcw on 2008-06-10
Egh.

I'm using 8.04 on an IBM T42 with an Atheros card. I tried to switch to madwifi because my logging on was booting other computers off the office network (everyone else has a Mac, connecting to the network from my machine would put it down temporarily). I tried the svn version of madwifi first, which gave nothing in my network manager. I'm not using the distro version: apt-get install madwifi-tools will not do anything - nothing installed/uninstalled/etc.

Right now I can see networks in the Network Manager. Running 'iwlist scan' will show the networks I can connect to. I try connecting to one, though, and it never resolves with a connection.

The network I'm trying to connect to is (from iwlist)

```

                    ESSID:"(censored)"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=40/70  Signal level=-55 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

```
tom@tom-t42:~/Applications/wifi$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0e:9b:ac:b3:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:11:25:15:8e:d1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe15:8ed1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17625262 (16.8 MB)  TX bytes:4487886 (4.2 MB)
          Base address:0x8000 Memory:c0240000-c0260000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21030838 (20.0 MB)  TX bytes:21030838 (20.0 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-0E-9B-AC-B3-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:286425 errors:0 dropped:0 overruns:0 frame:37440
          TX packets:2793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:28356796 (27.0 MB)  TX bytes:189102 (184.6 KB)
          Interrupt:11 

```

```

tom@tom-t42:~/Applications/wifi$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:28:86:DE   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-97 dBm  Noise level=-97 dBm
          Rx invalid nwid:277459  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

tom@tom-t42:~/Applications/wifi$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```

Thanks for any help! This is quite ridiculous, I feel like it's 1995 all over again, having to plug in.

---

