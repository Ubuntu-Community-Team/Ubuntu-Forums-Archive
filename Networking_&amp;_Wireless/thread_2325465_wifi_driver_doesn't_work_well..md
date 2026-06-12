---
title: "wifi driver doesn't work well."
date: 2016-05-22
forum: Networking &amp; Wireless
---

### Post by Matrix01 on 2016-05-22
My Lubuntu 14.04  sometime doesn't connect wifi.
Does different wifi driver work better?

---

### Post by wildmanne39 on 2016-05-22
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by pjalegria on 2016-05-29
Maybe is related to this bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986)

---

### Post by Matrix01 on 2016-06-12
here's my report:

forum said this file is too alrge to be in attachment.



```
########## wireless info START ##########

Report from: 12 Jun 2016 09:32 PDT -0700

Booted last: 12 Jun 2016 08:17 PDT -0700

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-88-generic #135-Ubuntu SMP Wed Jun 8 21:10:37 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, acpi_backlight=vendor, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Device [1895:30a1]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 002: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 148698  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              554291  1 ath9k
cfg80211              417586  3 ath,ath9k,mac80211
wmi                    18673  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.4.20  Bcast:192.168.7.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49215 errors:0 dropped:1 overruns:0 frame:0
          TX packets:33214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36110900 (36.1 MB)  TX bytes:4380465 (4.3 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"attwifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'attwifi' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:1004   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.4.1     0.0.0.0         UG    0      0        0 wlan0
192.168.4.0     0.0.0.0         255.255.252.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search 24hrft0888.snd.wayport.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       785     1  0 08:17 ?        00:00:06 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [attwifi] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DIRECT-JD-VIZIOTV: Infra, <MAC 'DIRECT-JD-VIZIOTV' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA2
    attwifi:         Infra, <MAC 'attwifi' [AC9]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 69
    attwifi:         Infra, <MAC 'attwifi' [AC8]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 67
    attwifi:         Infra, <MAC 'attwifi' [AC4]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47
    attwifi:         Infra, <MAC 'attwifi' [AC6]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 47
    *attwifi:        Infra, <MAC 'attwifi' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 61

  IPv4 Settings:
    Address:         192.168.4.20
    Prefix:          22 (255.255.252.0)
    Gateway:         192.168.4.1

    DNS:             192.168.4.1
    DNS:             64.134.255.2
    DNS:             64.134.255.10

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Java Depot]] (600 root)
[connection] id=Java Depot | type=802-11-wireless
[802-11-wireless] ssid=Java Depot | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Solace]] (600 root)
[connection] id=Solace | type=802-11-wireless
[802-11-wireless] ssid=Solace | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Bounce]] (600 root)
[connection] id=Bounce | type=802-11-wireless
[802-11-wireless] ssid=Bounce | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ENCINITAS-WiFi]] (600 root)
[connection] id=ENCINITAS-WiFi | type=802-11-wireless
[802-11-wireless] ssid=ENCINITAS-WiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Better Buzz Coffee WiFi]] (600 root)
[connection] id=Better Buzz Coffee WiFi | type=802-11-wireless
[802-11-wireless] ssid=Better Buzz Coffee WiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Google Starbucks]] (600 root)
[connection] id=Google Starbucks | type=802-11-wireless
[802-11-wireless] ssid=Google Starbucks | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/LDSAccess]] (600 root)
[connection] id=LDSAccess | type=802-11-wireless
[802-11-wireless] ssid=LDSAccess | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Digiboo]] (600 root)
[connection] id=Digiboo | type=802-11-wireless
[802-11-wireless] ssid=Digiboo | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/PEETS]] (600 root)
[connection] id=PEETS | type=802-11-wireless
[802-11-wireless] ssid=PEETS | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/St Tropez-guest]] (600 root)
[connection] id=St Tropez-guest | type=802-11-wireless
[802-11-wireless] ssid=St Tropez-guest | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATT240]] (600 root)
[connection] id=ATT240 | type=802-11-wireless
[802-11-wireless] ssid=ATT240 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_Free Westfield WiFi]] (600 root)
[connection] id=_Free Westfield WiFi | type=802-11-wireless
[802-11-wireless] ssid=_Free Westfield WiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/InternetOnly]] (600 root)
[connection] id=InternetOnly | type=802-11-wireless
[802-11-wireless] ssid=InternetOnly | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CoffeeBeanWiFi]] (600 root)
[connection] id=CoffeeBeanWiFi | type=802-11-wireless
[802-11-wireless] ssid=CoffeeBeanWiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/RalphsWiFi]] (600 root)
[connection] id=RalphsWiFi | type=802-11-wireless
[802-11-wireless] ssid=RalphsWiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WholeFoodsMarket]] (600 root)
[connection] id=WholeFoodsMarket | type=802-11-wireless
[802-11-wireless] ssid=WholeFoodsMarket | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Crazy Bowls and Wraps]] (600 root)
[connection] id=Crazy Bowls and Wraps | type=802-11-wireless
[802-11-wireless] ssid=Crazy Bowls and Wraps | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SBPC_225_Guests]] (600 root)
[connection] id=SBPC_225_Guests | type=802-11-wireless
[802-11-wireless] ssid=SBPC_225_Guests | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-37-HP ENVY 7640 series]] (600 root)
[connection] id=DIRECT-37-HP ENVY 7640 series | type=802-11-wireless
[802-11-wireless] ssid=DIRECT-37-HP ENVY 7640 series | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CCOFREE]] (600 root)
[connection] id=CCOFREE | type=802-11-wireless
[802-11-wireless] ssid=CCOFREE | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/DMP Guest WiFi]] (600 root)
[connection] id=DMP Guest WiFi | type=802-11-wireless
[802-11-wireless] ssid=DMP Guest WiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Flower Hill Free Wi-Fi]] (600 root)
[connection] id=Flower Hill Free Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=Flower Hill Free Wi-Fi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SurfSPRINTER]] (600 root)
[connection] id=SurfSPRINTER | type=802-11-wireless
[802-11-wireless] ssid=SurfSPRINTER | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR77]] (600 root)
[connection] id=NETGEAR77 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR77 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Church_Guest]] (600 root)
[connection] id=Church_Guest | type=802-11-wireless
[802-11-wireless] ssid=Church_Guest | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATT230]] (600 root)
[connection] id=ATT230 | type=802-11-wireless
[802-11-wireless] ssid=ATT230 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sharp_Guest]] (600 root)
[connection] id=Sharp_Guest | type=802-11-wireless
[802-11-wireless] ssid=Sharp_Guest | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SD_CO_LIBRARY]] (600 root)
[connection] id=SD_CO_LIBRARY | type=802-11-wireless
[802-11-wireless] ssid=SD_CO_LIBRARY | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SDVBC-OPEN]] (600 root)
[connection] id=SDVBC-OPEN | type=802-11-wireless
[802-11-wireless] ssid=SDVBC-OPEN | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Starbucks WiFi]] (600 root)
[connection] id=Starbucks WiFi | type=802-11-wireless
[802-11-wireless] ssid=Starbucks WiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Swell Cafe]] (600 root)
[connection] id=Swell Cafe | type=802-11-wireless
[802-11-wireless] ssid=Swell Cafe | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/UCSD-GUEST]] (600 root)
[connection] id=UCSD-GUEST | type=802-11-wireless
[802-11-wireless] ssid=UCSD-GUEST | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR]] (600 root)
[connection] id=NETGEAR | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/airportthru]] (600 root)
[connection] id=airportthru | type=802-11-wireless
[802-11-wireless] ssid=airportthru | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.457 GHz (Channel 10)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'attwifi' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"attwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006abdc50b3f
                    Extra: Last beacon: 212ms ago
          Cell 02 - Address: <MAC 'DIRECT-JD-VIZIOTV' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-JD-VIZIOTV"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006acc79bd9c
                    Extra: Last beacon: 2620ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '
```

> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by jeremy31 on 2016-06-12
Please use code tags when posting terminal results and wireless script results
Find the wireless-info.tar.gz file and attach it to a post as the previous results were incomplete

---

### Post by Matrix01 on 2016-06-19
> **jeremy31 said:**
> Please use code tags when posting terminal results and wireless script results
Find the wireless-info.tar.gz file and attach it to a post as the previous results were incomplete


here is wireless-info.tar.gz file.

---

### Post by Rick St. George on 2016-06-20
In /etc/resolv.conf, the nameserver was set is 127.0.1.1. 
Try changing it to 8.8.8.8.

See this Link for further info;
[http://unix.stackexchange.com/questions/128220/how-do-i-set-my-dns-when-resolv-conf-is-being-overwritten](http://unix.stackexchange.com/questions/128220/how-do-i-set-my-dns-when-resolv-conf-is-being-overwritten)

---

### Post by Matrix01 on 2016-09-10
Is this the code to type?
I do not mess this up.

 sudo vim /etc/resolvconf/resolv.conf.d/base
  Then put your nameserver list in like so:
  nameserver 8.8.8.8
nameserver 8.8.4.4
  Finally update resolvconf:
  $ sudo resolvconf -u

---

### Post by Keith_Helms on 2016-09-11
Tinkering with dns servers in resolvconf is not going to fix a problem where you can't connect to a wifi network.  I looked at the wireless info you attached a couple of months ago and it appears you have successfully connected to many, many networks.  It also looks like the attwifi network you're trying to connect to has multiple access points, so maybe you just need to try another.

---

### Post by Matrix01 on 2016-09-17
BUMP

network connection looks like this.
I guess I followed the instruction.

[ATTACH=CONFIG]271281[/ATTACH]

my Internet browser said "there is no network connection",
or

On college campus, Lubuntu connects WiFi in the beginning, and disconnects in the middle of anything.

any fix?

---

