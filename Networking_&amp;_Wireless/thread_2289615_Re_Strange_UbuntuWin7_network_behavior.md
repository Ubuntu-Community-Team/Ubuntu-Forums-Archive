---
title: "Re: Strange Ubuntu/Win7 network behavior"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by WB0HYQ on 2015-08-05
Several months ago, I installed Ubuntu 14.04LTS on my laptop (HP-G60). Everything went fine and I was able to network everywhere to/from this computer (including back to me from my laptop). I have three Win7 computers that can see each other on the house LAN and, up until this morning, I could see the laptop just fine and transfer files back and forth from either end.

Today, when I booted up the laptop (the others are on 24/7), it connected just fine, but I couldn't access any of my Windows machines. I checked the smb.conf file to make sure I was still in my workgroup and it hadn't changed. There had been one occasion when a core update altered the workgroup back to WORKGROUP, but not in this case.

Now, the strange part is that although I can (finally) move files TO my Win7 machines from my laptop, I absolutely cannot connect from my Win7 machines to my laptop. Windows pops up a login dialog and when I enter my (only) Ubuntu account on the laptop and the correct password, I am told "Invalid username/password".

My laptop has only ONE user and that's my one account that I use when I start up the laptop. The password is the same as I am entering from Windows, but it fails there.

An example:

I start up my laptop and let it boot up/begin running. It is a wireless connection, by the way.

I open the Files and then click Browse Network.

I get "Windows Network". Double-click that and I get my proper workgroup.

Double-clicking the workgroup, I get two Win7 computers and my own laptop

I can double-click either Win7 machine and move files to/from each of them easily.

When i double-click my OWN laptop, I get a prompt for username/password. (Password Required for Bill-G60) The Username is the one I use to initially start up Ubuntu and the Workgroup is already filled in with the proper workgroup name. I enter the password that I normally use and the login fails, giving me the login pop-up again.

Now, on the Windows side (this happens with either Win7 machine).

I bring up Network and see my laptop (Bill-G60) and double-click it.

I get a login dialog that refuses to accept my Ubuntu username/password and returns to the dialog again and again.

All this effectively isolates my laptop apparently from itself and Windows machines.

This is long-winded and I apologize for this, but it is something that I cannot figure out by myself.

Bill

A little more information:

I created an absolutely new user on my laptop (as an Administrator) and gave it a password.

The same exact set of circumstances outlined above happen if I am logging in as that user AND the same thing happens from my Windows 7 machines, endless login dialogs when trying that account.

Bill

Something that may help:

One of my Win 7 machines is dual boot, so I fired it up into Ubuntu (Xubuntu actually) 14.04. The only user on that machine is identical to the user on the laptop - including the password. It will connect to my Win7 mahcines and those machines will connect to my Xubuntu machine. I can pass files back and forth.

So, if the desktop will work with the Win 7 machines, why won't the laptop, using exactly the same logon name/password that I used when I set up the laptop?

EDIT: What I am now wondering is maybe I have a password issue on the laptop. When I created the 'test' user on it, I was not allowed to use the password I wanted because it was "not good enough". I do NOT remember that happening when I set up the laptop the first time. Now, I had to add a bunch of numbers and a symbol before Ubuntu accepted it and let me created the user.

Is it possible that the password I used originally (8 letters long) is being rejected as being "not good enough' so it never gets to the OS before being rejected?

Bill

---

### Post by WB0HYQ on 2015-08-06
Anyone??

EDIT: (24-hours later) Still not anyone?

Bill

---

### Post by WB0HYQ on 2015-08-08
Apparently editing doesn't bump the thread.

I still am unable to connect to my laptop from either Windows 7 machine even with a completely new user created on the laptop. From what I can tell, Ubuntu reject the request from Windows, and I get the 'unknown user/password' error. Windows is famous for giving erroneous errors so I am not sure this is exactly the reason.

At a deal loss to explain the behavior.

Does this wireless report help?

```


########## wireless info START ##########

Report from: 08 Aug 2015 14:10 EDT -0400

Booted last: 08 Aug 2015 13:37 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:22:15 UTC 2015 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth

07:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1381]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 002: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mxm_wmi                12893  1 nouveau
mac80211              546118  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
wmi                    18673  3 hp_wmi,mxm_wmi,nouveau

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
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5050619 (5.0 MB)  TX bytes:335772 (335.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Not_FBI_Van"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Not_FBI_Van' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:227   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.pace.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       772     1  0 13:37 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Not_FBI_Van] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Rooter:          Infra, <MAC 'Rooter' [AC9]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WPA2
    ATT625:          Infra, <MAC 'ATT625' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    Rooter:          Infra, <MAC 'Rooter' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    Who Dey:         Infra, <MAC 'Who Dey' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    linksys:         Infra, <MAC 'linksys' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    No Stealing My Internet: Infra, <MAC 'No Stealing My Internet' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    hpsetup:         Ad-Hoc, <MAC 'hpsetup' [AC6]>, Freq 2437 MHz, Rate 11 Mb/s, Strength 20
    *Not_FBI_Van:    Infra, <MAC 'Not_FBI_Van' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA
    NETGEAR99:       Infra, <MAC 'NETGEAR99' [AC7]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA2
    2WIRE071:        Infra, <MAC '2WIRE071' [AN10]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: eth0 -----------------------------------------------------------------
  [COLOR=#ff0000]Type:              Wired[/COLOR]
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

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

[[/etc/NetworkManager/system-connections/Not_FBI_Van]] (600 root)
[connection] id=Not_FBI_Van | type=802-11-wireless
[802-11-wireless] ssid=Not_FBI_Van | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Not_FBI_Van' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"Not_FBI_Van"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ae5ed041
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Who Dey' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Who Dey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016919e576b
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Rooter' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Rooter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a5ef932d7e
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'linksys' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a5f28d3a28
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'No Stealing My Internet' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"No Stealing My Internet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a5eff3e9a3
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'hpsetup' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
          Cell 07 - Address: <MAC 'NETGEAR99' [AC7]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a5efce56dd
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'ATT625' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ATT625"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f659cd3996
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Rooter' [AC9]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"Rooter"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a5eee0303a
                    Extra: Last beacon: 6512ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-61-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-61-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        69:0E:88:ED:16:F5:AE:8F:D7:69:92:3C:2E:8D:08:FD:CA:A4:2F:02
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-61-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-61-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        69:0E:88:ED:16:F5:AE:8F:D7:69:92:3C:2E:8D:08:FD:CA:A4:2F:02
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-61-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     65C14EF588BF1A68181643C
depends:        ath
intree:         Y
vermagic:       3.13.0-61-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        69:0E:88:ED:16:F5:AE:8F:D7:69:92:3C:2E:8D:08:FD:CA:A4:2F:02
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-61-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-61-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        69:0E:88:ED:16:F5:AE:8F:D7:69:92:3C:2E:8D:08:FD:CA:A4:2F:02
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-61-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E33EFDA3ABA56A33AC14EE7
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-61-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        69:0E:88:ED:16:F5:AE:8F:D7:69:92:3C:2E:8D:08:FD:CA:A4:2F:02
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-61-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     22618C9A8AD682CBE73FFF2
depends:        
intree:         Y
vermagic:       3.13.0-61-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        69:0E:88:ED:16:F5:AE:8F:D7:69:92:3C:2E:8D:08:FD:CA:A4:2F:02
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

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
# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

########## wireless info END ############


```

I can't really see anything here, but I am mystified as to why it reports I am on a "Wired" (red highlight) connection at ath0. There is NO cable connected. I am using my wireless connection.


Bill

---

### Post by weatherman2 on 2015-08-08
You have to share folders on the laptop for Windows to see them.  How have you done this?  Did you setup Samba shares manually with smb.conf?  Or did you use Nautilus (mouse/folders) to share a folder?  If you did it the later way, you can choose password authentication or "guest."  If you are using your computers on a secure LAN, you might be able to get away with sharing as a guest and no password.  (Then the username would be "guest" I think and no password, if you are asked for one.)

---

### Post by WB0HYQ on 2015-08-08
Please look at the first sentence of my first post in this thread. Until that morning (3 days ago) I could transfer data in every direction between any of my computers.

Now, the laptop refuses to let any of them to even CONNECT to it, let alone give the the shared directories. I have tried both Samba sharing and sharing using the File Manager. Neither method works as near as I can tell because I cannot connect to the laptop to see them.

Bill

---

### Post by weatherman2 on 2015-08-08
But you ARE connecting - you just aren't authenticating.  You're being asked for a username/password.

Did you try, in Nautilus, sharing as a guest or not?

---

### Post by WB0HYQ on 2015-08-08
Okay, I grant you I am contacting the laptop, but the connection itself is refused due to the failure of username/password. If that is the case, then why does it fail if I give it a legitimate username/password that I can log into the Ubuntu desktop with?

I have tried sharing as every user I've created as well as Guest with/without password. Nothing works. I cannot get through the authentication process.

That includes being logged in as a user, opening up the File Manager (pick one of them), clicking Browse Network. When i do that, I see one directory (Windows Network). drilling through that, I now see my workgroup name. I drill through that and I can see all of my Windows machines AND the laptop. I can double-click any of the Windows/Xubuntu machines and see their shared directories with no authentication (or, if there was, I did it once and checked "remember forever"). If I double-click the laptop, I get a login dialog and NOTHING works, not even the username/password I am currently logged in as.

EDIT: New wrinkle: I tried just now to make a newly created directory shared. It failed (I think) because I got this strange error:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Unexpected information received.

Does this make sense? I've never seen it before.

Bill

---

### Post by weatherman2 on 2015-08-08
Try the solution listed here (uncomment "guest account = nobody" in smb.conf then restart):

[http://askubuntu.com/questions/405926/samba-cannot-share-folder-cannot-convert-name-everyone-to-a-sid](http://askubuntu.com/questions/405926/samba-cannot-share-folder-cannot-convert-name-everyone-to-a-sid)

---

### Post by WB0HYQ on 2015-08-09
Hmmmm. I took a look at the samba configuration file and found this already there:

```

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    security = user
    encrypt passwords = no
    guest ok = yes
    guest account = backup


```

There was absolutely no change in my problem when I altered "backup" to "nobody". I tried to create a new shared directory on my laptop and got the very same error as above (error 255).

Bill

---

### Post by WB0HYQ on 2015-08-09
I have no idea why I didn't do this before......

I took a look at he other (dual boot) Xubuntu machine's samba file. In the section I quoted in my last post, only the very first line "usershare allow guests = yes" was there. NONE of the other stuff was present.

So, figuring I had nothing to lose, on the laptop, I commented out the other 5 lines and rebooted.

I am back to where I was before all this started - happily exchanging files between every one of my machines regardless of OS flavor.

Now, I guess I need to know if I've messed up anything by commenting out those lines. and, do I need to alter any more lines in the smb.conf file in any way to cover for those commented out lines?

Bill

---

### Post by oldfred on 2015-08-09
Not related to your specific issue.

I used Samba for several years. My laptop was XP and Desktop dual boot XP & Ubuntu. I only used laptop when travelling several times a year so really only wanted to transfer files from desktop to laptop & back 2 or 3 times a year. On desktop I was finally in Ubuntu 90% of time and only one app needed Windows, and I did not run it on laptop.
But every Ubuntu upgrade on desktop and every update of Windows, or virus or firewall or just about anything in Windows made me have to totally redo Samba.

Easy solution, install Ubuntu on laptop and I use NFS. If I install a new copy of Ubuntu, I have scripted the software install, and file configurations I need in Ubuntu so NFS just works.

---

### Post by WB0HYQ on 2015-08-09
I definitely agree. Samba is tricky to use. If I didn't need Windows to run my web design software (Serif's WebPlus X7), I'd be totally running Ubunto/Xubuntu on all my machines. But Serif isn't likely to port to Linux.

So, when i go to a customer's shop, I take my laptop and transfer files back and forth to my Windows machines before I leave/when I get back. I hadn't thought about NFS, though. maybe that is a better way to go. I'll have to do the research on it.

Thanks for the tip.

Bill

---

