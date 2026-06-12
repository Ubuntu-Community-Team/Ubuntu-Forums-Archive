---
title: "Compaq Mini 110 - mobile broadband - Internal SIM/WAN"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by danhansendenmark on 2014-09-11
**Compaq Mini 110 - mobile broadband - Internal SIM/WAN**                          [HR][/HR]                                                                   Hi,


**Please help me, my netbook can't use mobile broadband! Attending university and need it in school.**

Issue: Mobile broadband/Internal SIM card 
OS*: Ubuntu 12.04.5*
Computer: Qualcomm Gobi1000 HP un2400-module
Hardware: Compaq Mini 110 - 110c-1010SO

*OS: Ubuntu 12.04.5 (or higher if this solves the problem)
SIM-card tested in a usb modem, and it works.

Please help me if you can. If this means I have to use a whole new  distro I don't mind! This Netbook is what I have and I bought a 240Gb  SSD and maximum memory to make it as good as possible. I'm attending  university and I need this computer to work. I solved all other issues. I  got online banking, skype, cairo-dock, open-office etc. to work but I  need the internal modem/WAN/SIM-card to run. There's no room for a  external modem and it's not possible to run win7 on this computer. It  came with XP, but XP is not being serviced anymore, as you might know.  And I really like and prefer Linux/Ubuntu 12.04 or higher to work with  this SIM/WAN. I would really like to keep Linux!

So please help me solve this issue, if you can. I've posted this problem  some time ago and there's two other who has asked me if we solved the  problem. So we are several who really needs this issue to be solved. 

To begin with, I can tell you that the internal modem/WAN doesn't appear when doing "lspci" or "lsusb".         

                                                                                       __________________
                Kind Regards
Dan

---

### Post by sheldon-corey on 2014-09-12
please run and provide the resultant report USING "code" tags please:

wget -N -t 5 -T 10 [[COLOR=#1155cc]http://dl.dropbox.com/u/[/COLOR]57264241/wireless_script]("http://dl.dropbox.com/u/57264241/wireless_script") && chmod +x wireless_script && ./wireless_script


also advise if modemmanager is presently installed and if so what version  ......

---

### Post by danhansendenmark on 2014-11-18
Hi Sheldon-Corey,


My G..!!! I haven't noticed your reply before just now! I'm telling you, if this works you have saved not my day or my week - you'll have saved my whole year! I'm just eager to try it. I'll try it right now. First as the system is and then on a clean installation!! Then I'll get right back to you. Several others has asked me during these last months if I solved the problem. So if this works, many will gain from your fix/help!! ;)

> also advise if modemmanager is presently installed and if so what version  ...
Not sure if I'm giving you the right answer, but the network adapter (LAN) and the the wireless network adapter can be seen/is installed. But not the internal modem (sim card). As I understand it, it's because the driver for the modem only works with windows. What people have tried is to install wine or to use some from the windows installation file and use in Linux. Tried it all. It's just a mess.
I've been reading some more sites containing this and I'm pretty sure that the problem is exactly what you are refering to, the modem manager. I just didn't know it was called a modem manager. I've been calling in a "driver" for internal modem.
Here's a couple of the sites/links I've just read regarding this matter:
[http://zipforums.com/?tagid=mobile-broadband](http://zipforums.com/?tagid=mobile-broadband)
[http://askubuntu.com/questions/139878/ubuntu-12-04-cant-detect-internal-mobile-broadband-gobi-2000](http://askubuntu.com/questions/139878/ubuntu-12-04-cant-detect-internal-mobile-broadband-gobi-2000)
[http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000](http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000)

What I tried last time, before giving up was to read about the gobi_loader, since the problem (what I thougt it was) had to do with the modem driver. This is what I tried in my last attempt:
[http://web.archiveorange.com/archive/v/PqQ0Rk5YTSTGcy1IDEPN](http://web.archiveorange.com/archive/v/PqQ0Rk5YTSTGcy1IDEPN)

Other pretty interesting links regarding this matter:
[http://forums.debian.net/viewtopic.php?f=7&t=81928](http://forums.debian.net/viewtopic.php?f=7&t=81928)
[http://web.archiveorange.com/archive/v/PqQ0Rk5YTSTGcy1IDEPN](http://web.archiveorange.com/archive/v/PqQ0Rk5YTSTGcy1IDEPN)

Same problem found here:
[http://ubuntuforums.org/showthread.php?t=1768630](http://ubuntuforums.org/showthread.php?t=1768630)


Just tried this [COLOR=#ff0000]dmesg | grep -e "modem" -e "tty"[/COLOR]. Isn't this some kind of "contact" with the modem? Is it mini pci or is it using a usb port? I'm pretty confused because I've read 1000 pages:
```
# dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    9.438180] usbserial: USB Serial support registered for Qualcomm USB modem

```



Here's the content of "lspci" and "lsusb" which shows the 2 adapters mentioned above:

Content of "lsusb"
```
# lsusb
Bus 001 Device 002: ID 10f1:1a0f Importek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Content of "lspci"
```
# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
02:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)
```


I've written in many forums but haven't had any luck yet. 


Here's the content of "wireless-info.txt":

```
########## wireless info START ##########

Report from: 18 Nov 2014 19:23 CET +0100

Booted last: 18 Nov 2014 00:00 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1508]
    Kernel driver in use: wl

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 001 Device 002: ID 10f1:1a0f Importek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
wmi                    18673  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe66:d3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:193541 errors:0 dropped:0 overruns:0 frame:483125
          TX packets:112983 errors:31 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:279381647 (279.3 MB)  TX bytes:10076273 (10.0 MB)
          Interrupt:16 Base address:0xc000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"NASA1_DLink"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'NASA1_DLink' [AC1]>   
          Bit Rate=2 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [NASA1_DLink - Static] ----------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           2 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    tophat:          Infra, <MAC 'tophat' [AC2]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 42 WPA
    Tobeline:        Infra, <MAC 'Tobeline' [AC8]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Notebook:        Infra, <MAC 'Notebook' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    DTEnu6Ek:        Infra, <MAC 'DTEnu6Ek' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    ttmtgeg9:        Infra, <MAC 'ttmtgeg9' [AN5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *NASA1_DLink:    Infra, <MAC 'NASA1_DLink' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WPA2
    75a5af4v:        Infra, <MAC '75a5af4v' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    473qk3yv:        Infra, <MAC '473qk3yv' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    DIRECT-HW[TV]SPARTUS: Infra, <MAC 'DIRECT-HW[TV]SPARTUS' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    SEMIH-PC_Network:Infra, <MAC 'SEMIH-PC_Network' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    TDC-4344:        Infra, <MAC 'TDC-4344' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             194.239.134.83
    DNS:             193.162.153.164

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

[[/etc/NetworkManager/system-connections/NASA1_DLink - Static]] (600 root)
[connection] id=NASA1_DLink - Static | type=802-11-wireless
[802-11-wireless] ssid=NASA1_DLink | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Copenhagen (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.422 GHz (Channel 3)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NASA1_DLink' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NASA1_DLink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'tophat' [AC2]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"tophat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Notebook' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Notebook"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'DTEnu6Ek' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"DTEnu6Ek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '75a5af4v' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"75a5af4v"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'DIRECT-HW[TV]SPARTUS' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-HW[TV]SPARTUS"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '473qk3yv' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"473qk3yv"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Tobeline' [AC8]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Tobeline"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authenticalo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

tion Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

coretemp
qcserial
hp-wmi
qcserial
hp-wmi
qcserial
hp-wmi
qcserial
hp-wmi
qcserial
hp-wmi

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.861138] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.004148] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.856350] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)

########## wireless info END ############
```




Kind Regards,
Dan

---

