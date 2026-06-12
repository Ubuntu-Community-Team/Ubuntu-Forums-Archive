---
title: "wireless recognizes sometimes doesn't recognize network that other devices can access"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by sgriggly on 2015-11-30
i have a really strange issue with the network in my apartment complex. there are two networks, network "A" let's call it and network "A2". since i live on the 2nd story, network "A2" is stronger; sometimes, my computer has no problem connecting to it. 

other times, however, it recognizes network "A", along with the other networks in range... all except for network "A2"!!! "oh," you think, "network A2 is just down at these times". nope. my phone recognizes network A2, connects to it, and it works. my computer, meanwhile, can connect to network A and it works (albeit slowly). 

it goes through phases of about 1 day. it recognizes A2, connects with no problem, but at some point... A2 is just gone from my available networks and i have to use A. i know A2 still is active and working b/c i'm connected to it thru my phone, and i know my wireless is working b/c i'm connected to A, but ubuntu isn't recognizing A2... until about a day later, when it does. then A2 mysteriously works again. for about a day. 

i've tried connecting to A2 as a hidden network, but that doesn't work. 

help please!

---

### Post by jeremy31 on 2015-11-30
Might be a regulatory setting, what country are you in and open a terminal window and post the result of ```
iw reg get; cat /etc/default/crda | grep REGDOMAIN
```

---

### Post by sgriggly on 2015-12-01
i'm in Thailand now

iw reg get; cat /etc/default/crda | grep REGDOMAIN
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
REGDOMAIN=

following your implied suggestions, i set to TH

iw reg set TH

now, iw reg get returns: 

iw reg get

country TH:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)

now it's working, but not sure if this is the reason. will update if problem resurfaces...

this step did NOT solve the problem. is it normal that, upon restart, my iw settings reverted to 00?

---

### Post by jeremy31 on 2015-12-02
You can set it by editing /etc/default/crda and change the last line to ```
REGDOMAIN=TH
```
Save and reboot

---

### Post by sgriggly on 2015-12-02
ok. REGDOMAIN=TH is now set, and "reg get" reads TH on reboot. 

but still same problem. my phone is connected to A2, but computer only recognizing A

---

### Post by jeremy31 on 2015-12-02
Lets run the wireless script ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]chmod +x wireless-info && ./wireless-info
```

Post the contents of the wireless-info.**txt** file[/FONT][/COLOR]

---

### Post by sgriggly on 2015-12-02
*** accidentally posted full script instead of readout. deleted for readability of the post***

---

### Post by slickymaster on 2015-12-02
@sgriggly:
You're expected to run the script and post back in the thread the output you get from it, not to transcribe the script itself.

Please open a terminal window (Ctrl+Alt+T) and copy+paste the following into it```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```It will gathers the info necessary for troubleshooting your wireless connection and saves them in a text file, wrapping it in an archive if it exceeds the 19.5 kB size limit for .txt attachments on the Forums.

---

### Post by sgriggly on 2015-12-02
oh haha you're right, i opened the wrong file. they're both called "wireless-info" so i just opened the first one and hit ctrl a - ctrl c - ctrl v since i don't know what i'm looking for. 


```
########## wireless info START ##########

Report from: 02 Dec 2015 18:46 ICT +0700

Booted last: 02 Dec 2015 18:16 ICT +0700

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise

##### kernel ############################

Linux 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell Device [1028:0652]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 0b05:5480 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
mxm_wmi                13022  0 
wmi                    19257  2 dell_wmi,mxm_wmi
wl                   4108704  0 
cfg80211              208382  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop

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

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22789 errors:0 dropped:0 overruns:0 frame:33881
          TX packets:19020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20143663 (20.1 MB)  TX bytes:3947179 (3.9 MB)
          Interrupt:18 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"NOOTOU"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'NOOTOU' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1

##### resolv.conf #######################

nameserver 127.0.0.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1319     1  0 18:16 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth1  [NOOTOU] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Speed:           13 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    praija:          Infra, <MAC 'praija' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    MANISORN:        Infra, <MAC 'MANISORN' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA
    *NOOTOU:         Infra, <MAC 'NOOTOU' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Almali 3:        Infra, <MAC 'Almali 3' [AN4]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    Almali 2:        Infra, <MAC 'Almali 2' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HAPPYHOUSE:      Infra, <MAC 'HAPPYHOUSE' [AN6]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Bee:             Infra, <MAC 'Bee' [AC3]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AUX]] (600 root)
[connection] id=AUX | type=802-11-wireless
[802-11-wireless] ssid=AUX | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Goldenjade]] (600 root)
[connection] id=Goldenjade | type=802-11-wireless
[802-11-wireless] ssid=Goldenjade | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/black-tent-cafe-wifi]] (600 root)
[connection] id=black-tent-cafe-wifi | type=802-11-wireless
[802-11-wireless] ssid=black-tent-cafe-wifi | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LingCaiHotel]] (600 root)
[connection] id=LingCaiHotel | type=802-11-wireless
[802-11-wireless] ssid=LingCaiHotel | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Oldtown2nd_Floor1]] (600 root)
[connection] id=Oldtown2nd_Floor1 | type=802-11-wireless
[802-11-wireless] ssid=Oldtown2nd_Floor1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Seeds-Cafe]] (600 root)
[connection] id=Seeds-Cafe | type=802-11-wireless
[802-11-wireless] ssid=Seeds-Cafe | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JLWBG—207]] (600 root)
[connection] id=JLWBG—207 | type=802-11-wireless
[802-11-wireless] ssid=74;76;87;66;71;226;128;148;50;48;55; | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-OFFICE]] (600 root)
[connection] id=ESUKHIA-OFFICE | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-OFFICE | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ELCI.WIFI]] (600 root)
[connection] id=ELCI.WIFI | type=802-11-wireless
[802-11-wireless] ssid=ELCI.WIFI | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/salad houes_A2]] (600 root)
[connection] id=salad houes_A2 | type=802-11-wireless
[802-11-wireless] ssid=salad houes_A2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Black Canyon Coffee]] (600 root)
[connection] id=Black Canyon Coffee | type=802-11-wireless
[802-11-wireless] ssid=Black Canyon Coffee | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/COFFEE-MEAL]] (600 root)
[connection] id=COFFEE-MEAL | type=802-11-wireless
[802-11-wireless] ssid=COFFEE-MEAL | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/aeea]] (600 root)
[connection] id=aeea | type=802-11-wireless
[802-11-wireless] ssid=aeea | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tony2]] (600 root)
[connection] id=Tony2 | type=802-11-wireless
[802-11-wireless] ssid=Tony2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RATTANASIN_2]] (600 root)
[connection] id=RATTANASIN_2 | type=802-11-wireless
[802-11-wireless] ssid=RATTANASIN_2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU 3]] (600 root)
[connection] id=NOOTOU 3 | type=802-11-wireless
[802-11-wireless] ssid=NOOTOU 3 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU]] (600 root)
[connection] id=NOOTOU | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=NOOTOU | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Budgetroom]] (600 root)
[connection] id=Budgetroom | type=802-11-wireless
[802-11-wireless] ssid=Budgetroom | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU 2]] (600 root)
[connection] id=NOOTOU 2 | type=802-11-wireless
[802-11-wireless] ssid=NOOTOU 2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-TENNOR-1]] (600 root)
[connection] id=ESUKHIA-TENNOR-1 | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-TENNOR-1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CARPEDIEM]] (600 root)
[connection] id=CARPEDIEM | type=802-11-wireless
[802-11-wireless] ssid=CARPEDIEM | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Indy Tattoo ]] (600 root)
[connection] id=Indy Tattoo  | type=802-11-wireless
[802-11-wireless] ssid=Indy Tattoo  | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JLWBG-204]] (600 root)
[connection] id=JLWBG-204 | type=802-11-wireless
[802-11-wireless] ssid=JLWBG-204 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZTE-ddda2a]] (600 root)
[connection] id=ZTE-ddda2a | type=802-11-wireless
[802-11-wireless] ssid=ZTE-ddda2a | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pacific Coffee]] (600 root)
[connection] id=Pacific Coffee | type=802-11-wireless
[802-11-wireless] ssid=Pacific Coffee | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/A Journey]] (600 root)
[connection] id=A Journey | type=802-11-wireless
[802-11-wireless] ssid=A Journey | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/om mani padme hung]] (600 root)
[connection] id=om mani padme hung | type=802-11-wireless
[802-11-wireless] ssid=om mani padme hung | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/H239]] (600 root)
[connection] id=H239 | type=802-11-wireless
[802-11-wireless] ssid=H239 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TonNam Villa 0]] (600 root)
[connection] id=TonNam Villa 0 | type=802-11-wireless
[802-11-wireless] ssid=TonNam Villa 0 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AirJaldi-Esukhia]] (600 root)
[connection] id=AirJaldi-Esukhia | type=802-11-wireless
[802-11-wireless] ssid=AirJaldi-Esukhia | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rainbow_Free_WIFI]] (600 root)
[connection] id=Rainbow_Free_WIFI | type=802-11-wireless
[802-11-wireless] ssid=Rainbow_Free_WIFI | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/English Department]] (600 root)
[connection] id=English Department | type=802-11-wireless
[802-11-wireless] ssid=English Department | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WeCafe_2]] (600 root)
[connection] id=WeCafe_2 | type=802-11-wireless
[802-11-wireless] ssid=WeCafe_2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Katabeach]] (600 root)
[connection] id=Katabeach | type=802-11-wireless
[802-11-wireless] ssid=Katabeach | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DREAM-LAND-2]] (600 root)
[connection] id=DREAM-LAND-2 | type=802-11-wireless
[802-11-wireless] ssid=DREAM-LAND-2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-TENNOR-2]] (600 root)
[connection] id=ESUKHIA-TENNOR-2 | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-TENNOR-2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/jimmys-wifi]] (600 root)
[connection] id=jimmys-wifi | type=802-11-wireless
[802-11-wireless] ssid=jimmys-wifi | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/salad house_B2]] (600 root)
[connection] id=salad house_B2 | type=802-11-wireless
[802-11-wireless] ssid=salad house_B2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Friendly Planet]] (600 root)
[connection] id=Friendly Planet | type=802-11-wireless
[802-11-wireless] ssid=Friendly Planet | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ycds8888]] (600 root)
[connection] id=ycds8888 | type=802-11-wireless
[802-11-wireless] ssid=ycds8888 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sonya 1]] (600 root)
[connection] id=Sonya 1 | type=802-11-wireless
[802-11-wireless] ssid=Sonya 1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RCINN]] (600 root)
[connection] id=RCINN | type=802-11-wireless
[802-11-wireless] ssid=RCINN | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dqua4]] (600 root)
[connection] id=dqua4 | type=802-11-wireless
[802-11-wireless] ssid=dqua4 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MintResidence41]] (600 root)
[connection] id=MintResidence41 | type=802-11-wireless
[802-11-wireless] ssid=MintResidence41 | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Asia/Bangkok (based on set time zone)

country TH:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

eth1      32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.437 GHz (Channel 6)
```

```
##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)

eth1      Scan completed :
          Cell 01 - Address: <MAC 'NOOTOU' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NOOTOU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'praija' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"praija"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Bee' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Bee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MANISORN' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"MANISORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HENRI' [AC5]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HENRI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/wl.ko
srcversion:     F07ACEAAE49236EAB96169B
depends:        cfg80211,lib80211
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.5.0-61-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     74571C7FA6F4E9D34760CDF
depends:        
intree:         Y
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
bbswitch
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/bbswitch.conf]
blacklist nouveau
options bbswitch load_state=0

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x12d1:0x14db (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

##### dmesg #############################

[   15.846308] r8169 0000:07:00.0: eth0: link down
[   15.846636] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   16.476872] Bluetooth: firmware loaded
[ 1816.042364] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############
```

to be clear, the "NOOTOU" there is network A, the main home network. "NOOTOU 2" is the network my phone connects to anytime, but my computer only SOMETIMES recognizes.

---

### Post by jeremy31 on 2015-12-02
I would change NOOTOU 2 to channel 11 instead of whatever it is on now and make sure the encryption is WPA2-AES only with no WEP or TKIP

---

### Post by sgriggly on 2015-12-03
sorry i'm long-time user, but still pretty noob-y. can u plz post instructions for: 

> **jeremy31 said:**
> change NOOTOU 2 to channel 11 instead of whatever it is on now

Where or how do i change the channel? I don't find it in my network settings, and didn't turn up any clear instructions by google search... 

NOOTOU 2 is already set to "WPA & WPA2 Personal" in Wireless Network Settings.

---

### Post by jeremy31 on 2015-12-03
Those are wifi router settings and since you live in an apartment complex, it is unlikely that you can change them

---

### Post by Hadaka on 2015-12-03
Hi,one way to make it "see" NOOTOU 2  is to put the mac address of
NOOTOU 2 in the network manager configuration. see attached.
to find the mac address of NOOTOU 2 please do..
```
sudo iwlist eth1 scan
```
find NOOTOU 2 and then put it's mac address in the BSSID field..see attached.
my example is for a connection called "linksys"
[ATTACH=CONFIG]265908[/ATTACH]
To add the mac address to the BSSID field, click the wireless icon
then click Edit Connections >>Wireless>>NOOTOU 2>>Edit
then enter the mac address in the BSSID field.
click SAVE then close. boot and test.
*You may also want to ask whoever maintaines the the network
to add an underscor_2 or eliminate the space in NOOTOU 2 .
linux doesnt like spaces in ssid's. its like saying grep nootoo 2
from a file with nootoo ,nootoo 1 ,nootoo 2....you will get them all
because it only reads up to the space.

---

### Post by sgriggly on 2015-12-03
ok. the network started working again (around midnight, i'm wondering if it is exactly 1 day on, 1 day off?). i grabbed the info using the technique you described and rebooted, network is still working. let's see if it lasts! fingers crossed, thank you...

---

### Post by slickymaster on 2015-12-04
> **sgriggly said:**
> ok. the network started working again (around midnight, i'm wondering if it is exactly 1 day on, 1 day off?). i grabbed the info using the technique you described and rebooted, network is still working. let's see if it lasts! fingers crossed, thank you...

If everything is still working as expected, please mark the thread as solved, so other people searching the forums know that it provides a working solution (at least to the original poster) for the problem.

---

### Post by sgriggly on 2015-12-05
hey guys, thanks! yes, i'll be sure to mark the thread "solved" once it is... 

unfortunately, the problem cropped up again for me. from midnight last night until noon today, i was without NOOTOU 2 (tho i was connected on my phone during this intermittent period).

---

### Post by sgriggly on 2015-12-07
to be clear, i took the steps suggested by Hadaka: 

> **Hadaka said:**
> Hi,one way to make it "see" NOOTOU 2  is to put the mac address of
NOOTOU 2 in the network manager configuration. see attached.
to find the mac address of NOOTOU 2 please do..
```
sudo iwlist eth1 scan
```
find NOOTOU 2 and then put it's mac address in the BSSID field..see attached.
my example is for a connection called "linksys"
[ATTACH=CONFIG]265908[/ATTACH]
To add the mac address to the BSSID field, click the wireless icon
then click Edit Connections >>Wireless>>NOOTOU 2>>Edit
then enter the mac address in the BSSID field.
click SAVE then close. boot and test.
*You may also want to ask whoever maintaines the the network
to add an underscor_2 or eliminate the space in NOOTOU 2 .
linux doesnt like spaces in ssid's. its like saying grep nootoo 2
from a file with nootoo ,nootoo 1 ,nootoo 2....you will get them all
because it only reads up to the space.

NOOTOU 2's mac address is now in the BSSID field; the connections still works intermittently, but will disappear for 12 or 24 hours at a time... so the issue remains unresolved.

---

### Post by sgriggly on 2015-12-10
hey guys! thread is still active. issue is unresolved.

---

### Post by sgriggly on 2015-12-11
Hey guys. There are two connections at my apartment, NOOTOU and NOOTOU 2. My WiFi *always* recognizes NOOTOU (along with many other networks in range), but only *sometimes* recognizes NOOTOU 2. However, I know that NOOTOU 2 is alive and well b/c my phone has no trouble *always* recognizing and connecting to NOOTOU 2. 

I have attempted the following: 

I opened /etc/default/crda and changed REGDOMAIN=00 to REGDOMAIN=TH, since I'm currently in Thailand. 

```
iw reg get
```

returns "TH". This didn't resolve the issue. 

Next, I scanned for NOOTOU 2's mac address using:
```
sudo iwlist eth1 scan
```

... and added this to the BSSID field in the connection settings. The connection still works, but still only intermittently. This didn't resolve the problem. 

I have run ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```

Here are the results: 

```
########## wireless info START ##########

Report from: 02 Dec 2015 18:46 ICT +0700

Booted last: 02 Dec 2015 18:16 ICT +0700

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise

##### kernel ############################

Linux 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell Device [1028:0652]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 0b05:5480 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
mxm_wmi                13022  0 
wmi                    19257  2 dell_wmi,mxm_wmi
wl                   4108704  0 
cfg80211              208382  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop

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

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22789 errors:0 dropped:0 overruns:0 frame:33881
          TX packets:19020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20143663 (20.1 MB)  TX bytes:3947179 (3.9 MB)
          Interrupt:18 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"NOOTOU"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'NOOTOU' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1

##### resolv.conf #######################

nameserver 127.0.0.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1319     1  0 18:16 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth1  [NOOTOU] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Speed:           13 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    praija:          Infra, <MAC 'praija' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    MANISORN:        Infra, <MAC 'MANISORN' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA
    *NOOTOU:         Infra, <MAC 'NOOTOU' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Almali 3:        Infra, <MAC 'Almali 3' [AN4]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    Almali 2:        Infra, <MAC 'Almali 2' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HAPPYHOUSE:      Infra, <MAC 'HAPPYHOUSE' [AN6]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Bee:             Infra, <MAC 'Bee' [AC3]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AUX]] (600 root)
[connection] id=AUX | type=802-11-wireless
[802-11-wireless] ssid=AUX | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Goldenjade]] (600 root)
[connection] id=Goldenjade | type=802-11-wireless
[802-11-wireless] ssid=Goldenjade | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/black-tent-cafe-wifi]] (600 root)
[connection] id=black-tent-cafe-wifi | type=802-11-wireless
[802-11-wireless] ssid=black-tent-cafe-wifi | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LingCaiHotel]] (600 root)
[connection] id=LingCaiHotel | type=802-11-wireless
[802-11-wireless] ssid=LingCaiHotel | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Oldtown2nd_Floor1]] (600 root)
[connection] id=Oldtown2nd_Floor1 | type=802-11-wireless
[802-11-wireless] ssid=Oldtown2nd_Floor1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Seeds-Cafe]] (600 root)
[connection] id=Seeds-Cafe | type=802-11-wireless
[802-11-wireless] ssid=Seeds-Cafe | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JLWBG—207]] (600 root)
[connection] id=JLWBG—207 | type=802-11-wireless
[802-11-wireless] ssid=74;76;87;66;71;226;128;148;50;48;55; | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-OFFICE]] (600 root)
[connection] id=ESUKHIA-OFFICE | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-OFFICE | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ELCI.WIFI]] (600 root)
[connection] id=ELCI.WIFI | type=802-11-wireless
[802-11-wireless] ssid=ELCI.WIFI | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/salad houes_A2]] (600 root)
[connection] id=salad houes_A2 | type=802-11-wireless
[802-11-wireless] ssid=salad houes_A2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Black Canyon Coffee]] (600 root)
[connection] id=Black Canyon Coffee | type=802-11-wireless
[802-11-wireless] ssid=Black Canyon Coffee | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/COFFEE-MEAL]] (600 root)
[connection] id=COFFEE-MEAL | type=802-11-wireless
[802-11-wireless] ssid=COFFEE-MEAL | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/aeea]] (600 root)
[connection] id=aeea | type=802-11-wireless
[802-11-wireless] ssid=aeea | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tony2]] (600 root)
[connection] id=Tony2 | type=802-11-wireless
[802-11-wireless] ssid=Tony2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RATTANASIN_2]] (600 root)
[connection] id=RATTANASIN_2 | type=802-11-wireless
[802-11-wireless] ssid=RATTANASIN_2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU 3]] (600 root)
[connection] id=NOOTOU 3 | type=802-11-wireless
[802-11-wireless] ssid=NOOTOU 3 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU]] (600 root)
[connection] id=NOOTOU | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=NOOTOU | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Budgetroom]] (600 root)
[connection] id=Budgetroom | type=802-11-wireless
[802-11-wireless] ssid=Budgetroom | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU 2]] (600 root)
[connection] id=NOOTOU 2 | type=802-11-wireless
[802-11-wireless] ssid=NOOTOU 2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-TENNOR-1]] (600 root)
[connection] id=ESUKHIA-TENNOR-1 | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-TENNOR-1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CARPEDIEM]] (600 root)
[connection] id=CARPEDIEM | type=802-11-wireless
[802-11-wireless] ssid=CARPEDIEM | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Indy Tattoo ]] (600 root)
[connection] id=Indy Tattoo  | type=802-11-wireless
[802-11-wireless] ssid=Indy Tattoo  | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JLWBG-204]] (600 root)
[connection] id=JLWBG-204 | type=802-11-wireless
[802-11-wireless] ssid=JLWBG-204 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZTE-ddda2a]] (600 root)
[connection] id=ZTE-ddda2a | type=802-11-wireless
[802-11-wireless] ssid=ZTE-ddda2a | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pacific Coffee]] (600 root)
[connection] id=Pacific Coffee | type=802-11-wireless
[802-11-wireless] ssid=Pacific Coffee | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/A Journey]] (600 root)
[connection] id=A Journey | type=802-11-wireless
[802-11-wireless] ssid=A Journey | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/om mani padme hung]] (600 root)
[connection] id=om mani padme hung | type=802-11-wireless
[802-11-wireless] ssid=om mani padme hung | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/H239]] (600 root)
[connection] id=H239 | type=802-11-wireless
[802-11-wireless] ssid=H239 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TonNam Villa 0]] (600 root)
[connection] id=TonNam Villa 0 | type=802-11-wireless
[802-11-wireless] ssid=TonNam Villa 0 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AirJaldi-Esukhia]] (600 root)
[connection] id=AirJaldi-Esukhia | type=802-11-wireless
[802-11-wireless] ssid=AirJaldi-Esukhia | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rainbow_Free_WIFI]] (600 root)
[connection] id=Rainbow_Free_WIFI | type=802-11-wireless
[802-11-wireless] ssid=Rainbow_Free_WIFI | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/English Department]] (600 root)
[connection] id=English Department | type=802-11-wireless
[802-11-wireless] ssid=English Department | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WeCafe_2]] (600 root)
[connection] id=WeCafe_2 | type=802-11-wireless
[802-11-wireless] ssid=WeCafe_2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Katabeach]] (600 root)
[connection] id=Katabeach | type=802-11-wireless
[802-11-wireless] ssid=Katabeach | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DREAM-LAND-2]] (600 root)
[connection] id=DREAM-LAND-2 | type=802-11-wireless
[802-11-wireless] ssid=DREAM-LAND-2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-TENNOR-2]] (600 root)
[connection] id=ESUKHIA-TENNOR-2 | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-TENNOR-2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/jimmys-wifi]] (600 root)
[connection] id=jimmys-wifi | type=802-11-wireless
[802-11-wireless] ssid=jimmys-wifi | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/salad house_B2]] (600 root)
[connection] id=salad house_B2 | type=802-11-wireless
[802-11-wireless] ssid=salad house_B2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Friendly Planet]] (600 root)
[connection] id=Friendly Planet | type=802-11-wireless
[802-11-wireless] ssid=Friendly Planet | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ycds8888]] (600 root)
[connection] id=ycds8888 | type=802-11-wireless
[802-11-wireless] ssid=ycds8888 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sonya 1]] (600 root)
[connection] id=Sonya 1 | type=802-11-wireless
[802-11-wireless] ssid=Sonya 1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RCINN]] (600 root)
[connection] id=RCINN | type=802-11-wireless
[802-11-wireless] ssid=RCINN | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dqua4]] (600 root)
[connection] id=dqua4 | type=802-11-wireless
[802-11-wireless] ssid=dqua4 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MintResidence41]] (600 root)
[connection] id=MintResidence41 | type=802-11-wireless
[802-11-wireless] ssid=MintResidence41 | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Asia/Bangkok (based on set time zone)

country TH:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

eth1      32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)

eth1      Scan completed :
          Cell 01 - Address: <MAC 'NOOTOU' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NOOTOU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'praija' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"praija"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Bee' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Bee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MANISORN' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"MANISORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HENRI' [AC5]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HENRI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/wl.ko
srcversion:     F07ACEAAE49236EAB96169B
depends:        cfg80211,lib80211
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.5.0-61-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     74571C7FA6F4E9D34760CDF
depends:        
intree:         Y
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
bbswitch
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/bbswitch.conf]
blacklist nouveau
options bbswitch load_state=0

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x12d1:0x14db (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

##### dmesg #############################

[   15.846308] r8169 0000:07:00.0: eth0: link down
[   15.846636] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   16.476872] Bluetooth: firmware loaded
[ 1816.042364] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############
```

---

### Post by Hadaka on 2015-12-11
Hi, please do not post multiple treads for the same problem.
[http://ubuntuforums.org/showthread.php?t=2304874&page=2&p=13402953#post13402953](http://ubuntuforums.org/showthread.php?t=2304874&page=2&p=13402953#post13402953)
You state that "other" devices,computers,phone do not have a problem connecting to NOTOO 2
that is because these devices are not Ubuntu linux. as i stated in post#17 in the above link linux
does not do well with spaces in the SSID search feild...NOTOO 2. Please copy and paste the following to demonstrate what is happening.
```
echo -e "NOTOO\nNOTOO 2\nNOTOO 3"  > sgriggly
```
*view the file
```
cat sgriggly
```
*Emulate trying to connect to NOTOO 2
```
grep NOTOO 2 sgriggly
```
*Output
```
grep: 2: No such file or directory
sgriggly:NOTOO
sgriggly:NOTOO 2
sgriggly:NOTOO 3

```
*Notice the confusion,it first attempts to "grep" "connect" to 2 because of the space- and reports No such file
yet it outputs the entire contents of the file with NOTOO being first because there is no space.
this is why you keep trying to connect to NOTOO instead of NOTOO 2
*The following is an example that may or may not help.
```
grep "NOTOO 2" sgriggly
```
*Output
```
NOTOO 2
```
this worked because we put double quotes around "NOTOO 2"
Ciick the Network manager ..wifi signal icon.upper right..then click Edit connections , Wireless [at this point DELETE any ssid you do not want
to connect to ] then NOTOO 2,  EDIT
```
# insert quotes around NOTOO 2
..."NOTOO 2'
```see attached
[ATTACH=CONFIG]266095[/ATTACH]
*Place only around connection name...not ssid
cick save and close,boot and test.
the only other solution is to have the admin. eliminate the spaces.
*reminder..the other devices are not ubuntu linux
Beyond this i have nothing further to add.
goood luck

---

### Post by sgriggly on 2015-12-11
> **Hadaka said:**
> Hi, please do not post multiple treads for the same problem.

yes. i realize the rule for this; however, it seems once a thread hits multiple pages, it simply dies out and nobody bothers replying. i condensed the entire thread to one post.

> linux does not do well with spaces in the SSID search field...

interesting. and your example 'works' for me (in that it works properly only with the quotes). 

unfortunately, your solution does not solve my problem. (the funny thing is, there are a few OTHER networks that show up in my available networks list that have spaces; "NOOTOU 2" is not one of them at the moment [though, as i said before, sometimes it is! and it's not on reboot. it will drop in or out while i'm sitting there online]). 

> *Place only around connection name...not ssid
cick save and close,boot and test.
the only other solution is to have the admin. eliminate the spaces.
*reminder..the other devices are not ubuntu linux
Beyond this i have nothing further to add.
goood luck

again, tried your suggestion. no go. 

and yes, i know this is an ubuntu linux problem. hence why i'm posting to this forum. i mention that other devices work to show that this isn't a network problem. that is, to rule it out... ;)

---

### Post by Hadaka on 2015-12-11
If you are still seeking resolution to your issue, then bump your original thread
after 24 hours of no activity, rather than posting a new thread, your original thread
[http://ubuntuforums.org/showthread.php?t=2304874&page=2&p=13402953#post13402953](http://ubuntuforums.org/showthread.php?t=2304874&page=2&p=13402953#post13402953)
had activity one day go and has been viewed 453 times, I have no idea why there has not
been any additional suggestions from others. good luck

---

### Post by sgriggly on 2015-12-11
i bumped it once 6 days ago. 
i bumped it again 2 days later (4 days ago). 
the activity you mention is when i bumped it 24 hours ago. 

there are no helpful suggestions on that thread except yours, which was a week ago now. 

i actually don't think it's unreasonable to start a new thread after 3 bumps and a full week of no replies. having no reliable internet connection for a FULL WEEK kind of sucks, man...

---

### Post by Bucky Ball on 2015-12-11
*Threads merged.*

> **Hadaka said:**
> Hi, please do not post multiple treads for the same problem.

^^^
This. Just bump the thread after twelve hours, as suggested.

---

### Post by sgriggly on 2015-12-13
:rolleyes:
BUMP 

guys, now when i select NOOTOU, the network comes up with a little arrow (just as the VPN Connections > Configure VPN)... NOOTOU > NOOTOU / NOOTOU 1 (yes, now when i select "NOOTOU" i have to choose between "NOOTOU" and "NOOTOU 1") 

i have no idea where this came from, it just gave the option for the first time today .... of course, it's still not showing NOOTOU 2 (and i'm still connected to NOOTOU 2 on my phone).

---

### Post by Hadaka on 2015-12-13
Hi, I keep going over your wireless info file looking for a possible solution.
While you are convinced this is a Ubuntu problem, because it behaves differently than windows and whatever operating
system your cell phone uses,does not make your Ubuntu operating system faulty. Mercedes and Tesla are automobiles,
both have 4 tires,and seating for passengers,both are great automobiles. While the Tesla is much faster, its operating system
requires electrical power. The Mercedes requires petrol fuels. Both cars do the same thing but you cannot interchange the power
source they require to operate. 
I have found one item in your wireless report that is probably not causing the issue,but is likely adding to it.
A some point you blacklisted "bbswitch". bbswitch is a kernel module which automatically detects the required ACPI calls 
for two kinds of Optimus laptops. NVIDIA Optimus. Graphics. So it is blacklisted but it is also in /etc/modules.
this means. /etc/modules loads it then the blacklist file haults it,then the /etc/module file reloads it this is constantly happening
and is not good as graphic problems tend to disrupt wireless cards.
##### /etc/modules ######################

lp
rtc
bbswitch
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/bbswitch.conf]
blacklist nouveau
options bbswitch load_state=0
you also have multiple lp,rtc module calls. So Let's fix that.. Open a terminal and do..
```
echo -e "lp\nrtc" | sudo tee /etc/modules
```
this re-writes the file with a single lp and rtc call.

next is the linux TKIP issue , just like spaces in ssid names...linux does not do well and will usually fail with a TKIP
setting in the definitions of the access points...ALL your access points have that definition TKIP, linux prefers WPA2
Only the administrator of the system and owner of the routers can change those feilds, just like the spacing issue.
eth1      Scan completed :
          Cell 01 - Address: <MAC 'NOOTOU' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NOOTOU"[COLOR=#ff0000]<-This is where you were connected when this report was generated.[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK

Do all the NOOTOU'S  have the same password???
if not...then dont include anything but NOOTOU 2 in your
connection list.
I dont have a magic answer for you, since you dont own the network ,its difficult to make the changes needed
for your Ubuntu system to run correctly. Without those changes your Tesla will refuse to run on gasoline.
good luck

---

### Post by sgriggly on 2015-12-23
> **Hadaka said:**
> Hi, I keep going over your wireless info file looking for a possible solution.
While you are convinced this is a Ubuntu problem, because it behaves differently than windows and whatever operating
system your cell phone uses,does not make your Ubuntu operating system faulty. Mercedes and Tesla are automobiles,
both have 4 tires,and seating for passengers,both are great automobiles. While the Tesla is much faster, its operating system
requires electrical power. The Mercedes requires petrol fuels. Both cars do the same thing but you cannot interchange the power
source they require to operate. 

Is that the metaphor? The fact that NOOTOU 2 works SOMETIMES ruins your metaphor, b/c that means I could SOMETIMES put petrol into my Tesla, and it would work perfectly. The next day, it wouldn't. That doesn't make sense. 

> **Hadaka said:**
> I have found one item in your wireless report that is probably not causing the issue,but is likely adding to it.
A some point you blacklisted "bbswitch". bbswitch is a kernel module which automatically detects the required ACPI calls 
for two kinds of Optimus laptops. NVIDIA Optimus. Graphics. So it is blacklisted but it is also in /etc/modules.
this means. /etc/modules loads it then the blacklist file haults it,then the /etc/module file reloads it this is constantly happening
and is not good as graphic problems tend to disrupt wireless cards.
##### /etc/modules ######################

lp
rtc
bbswitch
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/bbswitch.conf]
blacklist nouveau
options bbswitch load_state=0
you also have multiple lp,rtc module calls. So Let's fix that.. Open a terminal and do..
```
echo -e "lp\nrtc" | sudo tee /etc/modules
```
this re-writes the file with a single lp and rtc call. 

Ok done. Didn't fix it, but the length of time increased after this... (it used to work for about a day, not work for about a day... now it's several days not working, several days working).

> **Hadaka said:**
> next is the linux TKIP issue , just like spaces in ssid names...linux does not do well and will usually fail with a TKIP
setting in the definitions of the access points...ALL your access points have that definition TKIP, linux prefers WPA2
Only the administrator of the system and owner of the routers can change those feilds, just like the spacing issue.
eth1      Scan completed :
          Cell 01 - Address: <MAC 'NOOTOU' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NOOTOU"[COLOR=#ff0000]<-This is where you were connected when this report was generated.[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK

Do all the NOOTOU'S  have the same password???

Yes. All the NOOTOUs have the same password. But you're right, unless I went to my landlord and made strange requests, I can't change the TKIP or spacing of the network. 

> **Hadaka said:**
> I dont have a magic answer for you, since you dont own the network ,its difficult to make the changes needed
for your Ubuntu system to run correctly. Without those changes your Tesla will refuse to run on gasoline.
good luck

But my Tesla is running on gasoline as we speak... It didn't for a couple days before now, which is why I haven't been able to post a reply. Now it does... :)

---

### Post by Hadaka on 2015-12-23
Glad to hear you solved your problem, please 
mark your thread solved by logging in, going to
your first post,click TOOLS then SOLVED.
thanks.

---

### Post by sgriggly on 2015-12-23
> **Hadaka said:**
> Glad to hear you solved your problem, please 
mark your thread solved by logging in, going to
your first post,click TOOLS then SOLVED.
thanks.

Sorry, to be clear, the issue isn't "solved." The problem is intermittent. It is working today, but it has NOT been working for the past 4 days. I did nothing in these last 4 days to solve it... In fact, I thought the last step I took was what kept it from coming back for so long... But, it showed up again out of the blue. If past experience is any indication, it will disappear again for no apparent reason. 

Not solved.

---

### Post by Bucky Ball on 2015-12-23
In that case, this is a bit ambiguous. 

> **sgriggly said:**
> 

But my Tesla is running on gasoline as we speak... It didn't for a couple days before now, which is why I haven't been able to post a reply. Now it does... :)

As it is currently working, post back if it stops. If it hangs in there for two or three days, solved. You can 'unsolve' a 'solved' thread if it breaks in a week (same way you mark a thread 'solved'). ;)

---

### Post by sgriggly on 2015-12-26
> **Bucky Ball said:**
> In that case, this is a bit ambiguous. 

As it is currently working, post back if it stops. If it hangs in there for two or three days, solved. You can 'unsolve' a 'solved' thread if it breaks in a week (same way you mark a thread 'solved'). ;)

it stopped working again. 

sorry, but with all due respect, it's not ambiguous. if you read the thread from the beginning, you'd know that this has been an intermittent problem from the beginning.

---

### Post by sgriggly on 2015-12-26
Hey guys. There are two connections at my apartment, NOOTOU and NOOTOU 2. My WiFi always recognizes NOOTOU (along with many other networks in range), but only sometimes recognizes NOOTOU 2. However, I know that NOOTOU 2 is alive and well b/c my phone has no trouble always recognizing and connecting to NOOTOU 2. 

I have attempted the following: 

I opened /etc/default/crda and changed REGDOMAIN=00 to REGDOMAIN=TH, since I'm currently in Thailand. 

```
iw reg get
returns "TH". This didn't resolve the issue. 
```

Next, I scanned for NOOTOU 2's mac address using:

```
sudo iwlist eth1 scan
```

... and added this to the BSSID field in the connection settings. The connection still works, but still only intermittently. This didn't resolve the problem. 

I have run

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```

Here are the results: 

```
########## wireless info START ##########

Report from: 02 Dec 2015 18:46 ICT +0700

Booted last: 02 Dec 2015 18:16 ICT +0700

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise

##### kernel ############################

Linux 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell Device [1028:0652]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 0b05:5480 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
mxm_wmi                13022  0 
wmi                    19257  2 dell_wmi,mxm_wmi
wl                   4108704  0 
cfg80211              208382  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop

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

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22789 errors:0 dropped:0 overruns:0 frame:33881
          TX packets:19020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20143663 (20.1 MB)  TX bytes:3947179 (3.9 MB)
          Interrupt:18 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"NOOTOU"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'NOOTOU' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1

##### resolv.conf #######################

nameserver 127.0.0.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1319     1  0 18:16 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth1  [NOOTOU] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Speed:           13 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    praija:          Infra, <MAC 'praija' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    MANISORN:        Infra, <MAC 'MANISORN' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA
    *NOOTOU:         Infra, <MAC 'NOOTOU' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Almali 3:        Infra, <MAC 'Almali 3' [AN4]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    Almali 2:        Infra, <MAC 'Almali 2' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HAPPYHOUSE:      Infra, <MAC 'HAPPYHOUSE' [AN6]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Bee:             Infra, <MAC 'Bee' [AC3]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AUX]] (600 root)
[connection] id=AUX | type=802-11-wireless
[802-11-wireless] ssid=AUX | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Goldenjade]] (600 root)
[connection] id=Goldenjade | type=802-11-wireless
[802-11-wireless] ssid=Goldenjade | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/black-tent-cafe-wifi]] (600 root)
[connection] id=black-tent-cafe-wifi | type=802-11-wireless
[802-11-wireless] ssid=black-tent-cafe-wifi | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LingCaiHotel]] (600 root)
[connection] id=LingCaiHotel | type=802-11-wireless
[802-11-wireless] ssid=LingCaiHotel | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Oldtown2nd_Floor1]] (600 root)
[connection] id=Oldtown2nd_Floor1 | type=802-11-wireless
[802-11-wireless] ssid=Oldtown2nd_Floor1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Seeds-Cafe]] (600 root)
[connection] id=Seeds-Cafe | type=802-11-wireless
[802-11-wireless] ssid=Seeds-Cafe | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JLWBG&#8212;207]] (600 root)
[connection] id=JLWBG&#8212;207 | type=802-11-wireless
[802-11-wireless] ssid=74;76;87;66;71;226;128;148;50;48;55; | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-OFFICE]] (600 root)
[connection] id=ESUKHIA-OFFICE | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-OFFICE | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ELCI.WIFI]] (600 root)
[connection] id=ELCI.WIFI | type=802-11-wireless
[802-11-wireless] ssid=ELCI.WIFI | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/salad houes_A2]] (600 root)
[connection] id=salad houes_A2 | type=802-11-wireless
[802-11-wireless] ssid=salad houes_A2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Black Canyon Coffee]] (600 root)
[connection] id=Black Canyon Coffee | type=802-11-wireless
[802-11-wireless] ssid=Black Canyon Coffee | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/COFFEE-MEAL]] (600 root)
[connection] id=COFFEE-MEAL | type=802-11-wireless
[802-11-wireless] ssid=COFFEE-MEAL | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/aeea]] (600 root)
[connection] id=aeea | type=802-11-wireless
[802-11-wireless] ssid=aeea | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tony2]] (600 root)
[connection] id=Tony2 | type=802-11-wireless
[802-11-wireless] ssid=Tony2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RATTANASIN_2]] (600 root)
[connection] id=RATTANASIN_2 | type=802-11-wireless
[802-11-wireless] ssid=RATTANASIN_2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU 3]] (600 root)
[connection] id=NOOTOU 3 | type=802-11-wireless
[802-11-wireless] ssid=NOOTOU 3 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU]] (600 root)
[connection] id=NOOTOU | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=NOOTOU | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Budgetroom]] (600 root)
[connection] id=Budgetroom | type=802-11-wireless
[802-11-wireless] ssid=Budgetroom | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOOTOU 2]] (600 root)
[connection] id=NOOTOU 2 | type=802-11-wireless
[802-11-wireless] ssid=NOOTOU 2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-TENNOR-1]] (600 root)
[connection] id=ESUKHIA-TENNOR-1 | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-TENNOR-1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CARPEDIEM]] (600 root)
[connection] id=CARPEDIEM | type=802-11-wireless
[802-11-wireless] ssid=CARPEDIEM | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Indy Tattoo ]] (600 root)
[connection] id=Indy Tattoo  | type=802-11-wireless
[802-11-wireless] ssid=Indy Tattoo  | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JLWBG-204]] (600 root)
[connection] id=JLWBG-204 | type=802-11-wireless
[802-11-wireless] ssid=JLWBG-204 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZTE-ddda2a]] (600 root)
[connection] id=ZTE-ddda2a | type=802-11-wireless
[802-11-wireless] ssid=ZTE-ddda2a | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pacific Coffee]] (600 root)
[connection] id=Pacific Coffee | type=802-11-wireless
[802-11-wireless] ssid=Pacific Coffee | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/A Journey]] (600 root)
[connection] id=A Journey | type=802-11-wireless
[802-11-wireless] ssid=A Journey | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/om mani padme hung]] (600 root)
[connection] id=om mani padme hung | type=802-11-wireless
[802-11-wireless] ssid=om mani padme hung | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/H239]] (600 root)
[connection] id=H239 | type=802-11-wireless
[802-11-wireless] ssid=H239 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TonNam Villa 0]] (600 root)
[connection] id=TonNam Villa 0 | type=802-11-wireless
[802-11-wireless] ssid=TonNam Villa 0 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AirJaldi-Esukhia]] (600 root)
[connection] id=AirJaldi-Esukhia | type=802-11-wireless
[802-11-wireless] ssid=AirJaldi-Esukhia | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rainbow_Free_WIFI]] (600 root)
[connection] id=Rainbow_Free_WIFI | type=802-11-wireless
[802-11-wireless] ssid=Rainbow_Free_WIFI | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/English Department]] (600 root)
[connection] id=English Department | type=802-11-wireless
[802-11-wireless] ssid=English Department | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WeCafe_2]] (600 root)
[connection] id=WeCafe_2 | type=802-11-wireless
[802-11-wireless] ssid=WeCafe_2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Katabeach]] (600 root)
[connection] id=Katabeach | type=802-11-wireless
[802-11-wireless] ssid=Katabeach | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DREAM-LAND-2]] (600 root)
[connection] id=DREAM-LAND-2 | type=802-11-wireless
[802-11-wireless] ssid=DREAM-LAND-2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESUKHIA-TENNOR-2]] (600 root)
[connection] id=ESUKHIA-TENNOR-2 | type=802-11-wireless
[802-11-wireless] ssid=ESUKHIA-TENNOR-2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/jimmys-wifi]] (600 root)
[connection] id=jimmys-wifi | type=802-11-wireless
[802-11-wireless] ssid=jimmys-wifi | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/salad house_B2]] (600 root)
[connection] id=salad house_B2 | type=802-11-wireless
[802-11-wireless] ssid=salad house_B2 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Friendly Planet]] (600 root)
[connection] id=Friendly Planet | type=802-11-wireless
[802-11-wireless] ssid=Friendly Planet | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ycds8888]] (600 root)
[connection] id=ycds8888 | type=802-11-wireless
[802-11-wireless] ssid=ycds8888 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sonya 1]] (600 root)
[connection] id=Sonya 1 | type=802-11-wireless
[802-11-wireless] ssid=Sonya 1 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RCINN]] (600 root)
[connection] id=RCINN | type=802-11-wireless
[802-11-wireless] ssid=RCINN | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dqua4]] (600 root)
[connection] id=dqua4 | type=802-11-wireless
[802-11-wireless] ssid=dqua4 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MintResidence41]] (600 root)
[connection] id=MintResidence41 | type=802-11-wireless
[802-11-wireless] ssid=MintResidence41 | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Asia/Bangkok (based on set time zone)

country TH:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

eth1      32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)

eth1      Scan completed :
          Cell 01 - Address: <MAC 'NOOTOU' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NOOTOU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'praija' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"praija"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Bee' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Bee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MANISORN' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"MANISORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HENRI' [AC5]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HENRI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/wl.ko
srcversion:     F07ACEAAE49236EAB96169B
depends:        cfg80211,lib80211
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.5.0-61-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     74571C7FA6F4E9D34760CDF
depends:        
intree:         Y
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
bbswitch
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/bbswitch.conf]
blacklist nouveau
options bbswitch load_state=0

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x12d1:0x14db (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

##### dmesg #############################

[   15.846308] r8169 0000:07:00.0: eth0: link down
[   15.846636] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   16.476872] Bluetooth: firmware loaded
[ 1816.042364] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############[/QUOTE]

Lastly, I have tried: 

[CODE]echo -e "lp\nrtc" | sudo tee /etc/modules
```

per Hadaka's suggestion. 

[QUOTE]I have found one item in your wireless report that is probably not causing the issue,but is likely adding to it.
A some point you blacklisted "bbswitch". bbswitch is a kernel module which automatically detects the required ACPI calls 
for two kinds of Optimus laptops. NVIDIA Optimus. Graphics. So it is blacklisted but it is also in /etc/modules.
this means. /etc/modules loads it then the blacklist file haults it,then the /etc/module file reloads it this is constantly happening
and is not good as graphic problems tend to disrupt wireless cards.
##### /etc/modules ######################

lp
rtc
bbswitch
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/bbswitch.conf]
blacklist nouveau
options bbswitch load_state=0
you also have multiple lp,rtc module calls. So Let's fix that.. Open a terminal and do..
Code:
echo -e "lp\nrtc" | sudo tee /etc/modules[/code]

Now, I don't know if this is coincidence or not. But my system was intermittently recognizing NOOTOU 2 on a cycle of about 24-36 hrs "on" (recognizing & connecting) and 24-36 hrs "off". Ever since this last code (above, "echo -e "lp\nrtc" | sudo tee /etc/modules"), the length of this cycle has increased! Now I have no internet for 3-4 days, followed by connection for a few days.

---

### Post by Hadaka on 2015-12-26
Hi, as you can see above from your last post, you had bbswitch black listed  and also in
/etc/modules along with dual entries of lp and rtc. As stated in /etc/modules, it is the place
holder for modules you want loaded at boot time.

 #RTC means telling your kernel whether or not the hardware clock is set to gmt time.
 #rtc = real time clock
 #lp = file printer or in unix/minix line printer

you dont need rtc to be in /etc/modules as it is already in the kernel and your computer is set to
local time and not GMT.

Here is mine.  
```
hadaka:~$ cat /etc/modules
lp

```
a single lp entry only.
you can view yours with..
```
cat /etc/modules
#to edit - gksudo /etc/modules
```
*The changes you did to /etc/modules had no effect on your situation.

---

