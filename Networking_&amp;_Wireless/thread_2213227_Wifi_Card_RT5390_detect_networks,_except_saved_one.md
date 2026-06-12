---
title: "Wifi Card RT5390 detect networks, except saved ones"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by makkekkazzo on 2014-03-25
Hi to everybody,

I have had always problems with this card, but today is doing something really really strange, I can see a lot of networks except the one to which I have always been connected (even though in the last days, it was connected but I couldn't surf the internet, reason why I used my Asus TF700T to use internet on this laptop, and I'm still using this solution).

Here the return from some common code:
```
makkekkazzo@fra:~$ sudo lshw -C network
[sudo] password for makkekkazzo: 
  *-network               
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 08:3e:8e:0b:9e:8e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-37-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7d00000-f7d0ffff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 30:85:a9:2e:0f:f0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:19 memory:f7c00000-f7c3ffff ioport:e000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 82:af:a7:74:85:a3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.109 link=yes multicast=yes


```

```
makkekkazzo@fra:~$ sudo ifconfig
eth0      Link encap:Ethernet  IndirizzoHW 30:85:a9:2e:0f:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:108280 (108.2 KB)  Byte TX:108280 (108.2 KB)

usb0      Link encap:Ethernet  IndirizzoHW 82:af:a7:74:85:a3  
          indirizzo inet:192.168.42.109  Bcast:192.168.42.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::80af:a7ff:fe74:85a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44211 errors:3 dropped:0 overruns:0 frame:3
          TX packets:30578 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:55760276 (55.7 MB)  Byte TX:4559342 (4.5 MB)

wlan0     Link encap:Ethernet  IndirizzoHW 08:3e:8e:0b:9e:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)


```

```
makkekkazzo@fra:~$ sudo iwconfig
usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


```

```
makkekkazzo@fra:~$ sudo nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        08:3E:8E:0B:9E:8E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
"Here there was the list of all the networks that the Card is detecting, naturally except the one to which the tablet is connected"


- Device: usb0  [Connessione via cavo 1] ---------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        82:AF:A7:74:85:A3

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        30:85:A9:2E:0F:F0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

```
makkekkazzo@fra:~$ sudo lsmod | grep rt2800pci
rt2800pci              18754  0 
rt2800lib              67510  1 rt2800pci
rt2x00pci              14621  1 rt2800pci
rt2x00lib              55630  3 rt2800pci,rt2800lib,rt2x00pci
eeprom_93cx6           13344  1 rt2800pci


```


I have already followed this method substituting "ath5k" with "rt2800pci"
```
sudo rmmod ath5k
sudo rfkill block all
sudo rfkill unblock all

sudo modprobe ath5k
sudo rfkill unblock all
sudo ifconfig wlan0 up
```

I hope all this informations are useful, and clearly ask me for any other output.
Thank you very much

---

### Post by makkekkazzo on 2014-03-25
Now only 5 minutes later the first post, without doing anything from that moment, I'm again connected to the network but without possibility of surfing
outcomes without the connections via usb
```
makkekkazzo@fra:~$ sudo iwconfig
[sudo] password for makkekkazzo: 
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AAA-WLAN"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1B:9E:E8:AC:B3   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:20   Missed beacon:0
```


```
makkekkazzo@fra:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:9E:E8:AC:B3
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"AAA-WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025585fe664
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 00084141412D574C414E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180205F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


```

```
 makkekkazzo@fra:~$ ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.035 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.035/0.035/0.037/0.007 ms 

makkekkazzo@fra:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms


```

---

