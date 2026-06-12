---
title: "Wifi not showing networks or option to enable wifi"
date: 2017-03-29
forum: Networking &amp; Wireless
---

### Post by nadermx on 2017-03-29
Currently I have been using ubuntu for a while without any issues, I ran ubuntu's suggested updates and now when I do a `ifconfig` it does not show my wlan0.  It also does not allow me to connect or show any wifi networks.

I found the wireless info script and ran it, the output is bellow would apprecicate any help


```
########## wireless info START ##########

Report from: 29 Mar 2017 14:00 PET -0500

Booted last: 29 Mar 2017 13:54 PET -0500

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-65-generic #86~14.04.1-Ubuntu SMP Fri Feb 24 17:54:46 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, resume=UUID=d1b94543-17f3-4cfd-8144-fa853eaac9f0, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
Bus 002 Device 005: ID 04f3:040d Elan Microelectronics Corp. 
Bus 002 Device 004: ID 2047:0855 Texas Instruments Invensense Embedded MotionApp HID Sensor
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 007: ID abcd:1234 Unknown 
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:11508 (11.5 KB)  TX bytes:11508 (11.5 KB)

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF1]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

virbr0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1010     1  0 13:54 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

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

[[/etc/NetworkManager/system-connections/LA ZONA ]] (600 root)
[connection] id=LA ZONA  | type=802-11-wireless
[802-11-wireless] ssid=LA ZONA  | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Highlands Coffee]] (600 root)
[connection] id=Highlands Coffee | type=802-11-wireless
[802-11-wireless] ssid=Highlands Coffee | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/RED-STB]] (600 root)
[connection] id=RED-STB | type=802-11-wireless
[802-11-wireless] ssid=RED-STB | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TUMARCA]] (600 root)
[connection] id=TUMARCA | type=802-11-wireless
[802-11-wireless] ssid=TUMARCA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Starbucks-Clientes]] (600 root)
[connection] id=Starbucks-Clientes | type=802-11-wireless
[802-11-wireless] ssid=Starbucks-Clientes | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/RED_STB 1]] (600 root)
[connection] id=RED_STB 1 | type=802-11-wireless
[802-11-wireless] ssid=RED_STB | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/.FreeAeropuertoLima]] (600 root)
[connection] id=.FreeAeropuertoLima | type=802-11-wireless
[802-11-wireless] ssid=.FreeAeropuertoLima | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Amis]] (600 root)
[connection] id=Amis | type=802-11-wireless
[802-11-wireless] ssid=Amis | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Free Airport WIFI]] (600 root)
[connection] id=Free Airport WIFI | type=802-11-wireless
[802-11-wireless] ssid=Free Airport WIFI | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/San Francisco]] (600 root)
[connection] id=San Francisco | type=802-11-wireless
[802-11-wireless] ssid=San Francisco | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Totalplay-A474]] (600 root)
[connection] id=Totalplay-A474 | type=802-11-wireless
[802-11-wireless] ssid=Totalplay-A474 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ginos-Clientes]] (600 root)
[connection] id=Ginos-Clientes | type=802-11-wireless
[802-11-wireless] ssid=Ginos-Clientes | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Google Starbucks]] (600 root)
[connection] id=Google Starbucks | type=802-11-wireless
[802-11-wireless] ssid=Google Starbucks | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Mohegansun Wifi]] (600 root)
[connection] id=Mohegansun Wifi | type=802-11-wireless
[802-11-wireless] ssid=Mohegansun Wifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/maclacave]] (600 root)
[connection] id=maclacave | type=802-11-wireless
[802-11-wireless] ssid=maclacave | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/GFT_3]] (600 root)
[connection] id=GFT_3 | type=802-11-wireless
[802-11-wireless] ssid=GFT_3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vintageemporium1]] (600 root)
[connection] id=vintageemporium1 | type=802-11-wireless
[802-11-wireless] ssid=vintageemporium1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SAIGON_INN_FL1]] (600 root)
[connection] id=SAIGON_INN_FL1 | type=802-11-wireless
[802-11-wireless] ssid=SAIGON_INN_FL1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tierra-garat-Jalapa]] (600 root)
[connection] id=Tierra-garat-Jalapa | type=802-11-wireless
[802-11-wireless] ssid=Tierra-garat-Jalapa | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DFB830]] (600 root)
[connection] id=DFB830 | type=802-11-wireless
[802-11-wireless] ssid=DFB830 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hidden]] (600 root)
[connection] id=hidden | type=802-11-wireless
[802-11-wireless] ssid=hidden | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CQ PARROQUIA]] (600 root)
[connection] id=CQ PARROQUIA | type=802-11-wireless
[802-11-wireless] ssid=CQ PARROQUIA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Orange-2C08]] (600 root)
[connection] id=Orange-2C08 | type=802-11-wireless
[802-11-wireless] ssid=Orange-2C08 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GTH_Guest]] (600 root)
[connection] id=GTH_Guest | type=802-11-wireless
[802-11-wireless] ssid=GTH_Guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/MUNDOINKA]] (600 root)
[connection] id=MUNDOINKA | type=802-11-wireless
[802-11-wireless] ssid=MUNDOINKA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SEOplayboy]] (600 root)
[connection] id=SEOplayboy | type=802-11-wireless
[802-11-wireless] ssid=SEOplayboy | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/PANERA]] (600 root)
[connection] id=PANERA | type=802-11-wireless
[802-11-wireless] ssid=PANERA | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/iPhone de Lou]] (600 root)
[connection] id=iPhone de Lou | type=802-11-wireless
[802-11-wireless] ssid=iPhone de Lou | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GesaRepetidor 1]] (600 root)
[connection] id=GesaRepetidor 1 | type=802-11-wireless
[802-11-wireless] ssid=GesaRepetidor | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Megacable WiFi]] (600 root)
[connection] id=Megacable WiFi | type=802-11-wireless
[802-11-wireless] ssid=Megacable WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/hostel3]] (600 root)
[connection] id=hostel3 | type=802-11-wireless
[802-11-wireless] ssid=hostel3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_EE20]] (600 root)
[connection] id=WLAN_EE20 | type=802-11-wireless
[802-11-wireless] ssid=WLAN_EE20 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/infinitum movil]] (600 root)
[connection] id=infinitum movil | type=802-11-wireless
[802-11-wireless] ssid=infinitum movil | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BTOpenzone]] (600 root)
[connection] id=BTOpenzone | type=802-11-wireless
[802-11-wireless] ssid=BTOpenzone | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/cafecustine]] (600 root)
[connection] id=cafecustine | type=802-11-wireless
[802-11-wireless] ssid=cafecustine | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Free@Guest]] (600 root)
[connection] id=Free@Guest | type=802-11-wireless
[802-11-wireless] ssid=Free@Guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/THALYSNET]] (600 root)
[connection] id=THALYSNET | type=802-11-wireless
[802-11-wireless] ssid=THALYSNET | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/STARBUCKS]] (600 root)
[connection] id=STARBUCKS | type=802-11-wireless
[802-11-wireless] ssid=STARBUCKS | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cablevision]] (600 root)
[connection] id=Cablevision | type=802-11-wireless
[802-11-wireless] ssid=Cablevision | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=28:B2:BD:74:A7:7A
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Aloft_Guest]] (600 root)
[connection] id=Aloft_Guest | type=802-11-wireless
[802-11-wireless] ssid=Aloft_Guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/DREAMS_FREE_WIFI]] (600 root)
[connection] id=DREAMS_FREE_WIFI | type=802-11-wireless
[802-11-wireless] ssid=DREAMS_FREE_WIFI | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR31]] (600 root)
[connection] id=NETGEAR31 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR31 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airport Free WiFi]] (600 root)
[connection] id=Airport Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=Airport Free WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SARCLETTI]] (600 root)
[connection] id=SARCLETTI | type=802-11-wireless
[802-11-wireless] ssid=SARCLETTI | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Boingo Hotspot]] (600 root)
[connection] id=Boingo Hotspot | type=802-11-wireless
[802-11-wireless] ssid=Boingo Hotspot | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HMARKAWASI- P2]] (600 root)
[connection] id=HMARKAWASI- P2 | type=802-11-wireless
[802-11-wireless] ssid=HMARKAWASI- P2 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WLAN_232A]] (600 root)
[connection] id=WLAN_232A | type=802-11-wireless
[802-11-wireless] ssid=WLAN_232A | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FREEWIFI BettyBoop AMS]] (600 root)
[connection] id=FREEWIFI BettyBoop AMS | type=802-11-wireless
[802-11-wireless] ssid=FREEWIFI BettyBoop AMS | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WLAN_C36E]] (600 root)
[connection] id=WLAN_C36E | type=802-11-wireless
[802-11-wireless] ssid=WLAN_C36E | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/..Starbucks..]] (600 root)
[connection] id=..Starbucks.. | type=802-11-wireless
[802-11-wireless] ssid=..Starbucks.. | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KPN]] (600 root)
[connection] id=KPN | type=802-11-wireless
[802-11-wireless] ssid=KPN | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/default]] (600 root)
[connection] id=default | type=802-11-wireless
[802-11-wireless] ssid=default | bssid=<MAC address> | mac-address=28:B2:BD:74:A7:7A
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/INFINITUM7421]] (600 root)
[connection] id=INFINITUM7421 | type=802-11-wireless
[802-11-wireless] ssid=INFINITUM7421 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vips-Clientes]] (600 root)
[connection] id=Vips-Clientes | type=802-11-wireless
[802-11-wireless] ssid=Vips-Clientes | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-]] (600 root)
[connection] id=DIRECT- | type=802-11-wireless
[802-11-wireless] ssid=DIRECT- | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CucutaCoffee]] (600 root)
[connection] id=CucutaCoffee | type=802-11-wireless
[802-11-wireless] ssid=CucutaCoffee | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Petit Four cafe]] (600 root)
[connection] id=Petit Four cafe | type=802-11-wireless
[802-11-wireless] ssid=Petit Four cafe | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KAMAKURA COFFEE 2]] (600 root)
[connection] id=KAMAKURA COFFEE 2 | type=802-11-wireless
[802-11-wireless] ssid=KAMAKURA COFFEE 2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/COOKIEMONSTER]] (600 root)
[connection] id=COOKIEMONSTER | type=802-11-wireless
[802-11-wireless] ssid=COOKIEMONSTER | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/To_Caphe]] (600 root)
[connection] id=To_Caphe | type=802-11-wireless
[802-11-wireless] ssid=To_Caphe | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Presidencia]] (600 root)
[connection] id=Presidencia | type=802-11-wireless
[802-11-wireless] ssid=Presidencia | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=802-11-wireless
[802-11-wireless] ssid=FreeWifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Sidrese_SalaJuntas_Pecera]] (600 root)
[connection] id=Sidrese_SalaJuntas_Pecera | type=802-11-wireless
[802-11-wireless] ssid=Sidrese_SalaJuntas_Pecera | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/To_Caphe_T1]] (600 root)
[connection] id=To_Caphe_T1 | type=802-11-wireless
[802-11-wireless] ssid=To_Caphe_T1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GesaRepetidor]] (600 root)
[connection] id=GesaRepetidor | type=802-11-wireless
[802-11-wireless] ssid=GesaRepetidor | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MALLORCACLIENTES]] (600 root)
[connection] id=MALLORCACLIENTES | type=802-11-wireless
[802-11-wireless] ssid=MALLORCACLIENTES | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/orange]] (600 root)
[connection] id=orange | type=802-11-wireless
[802-11-wireless] ssid=orange | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Daybreak_Customers]] (600 root)
[connection] id=Daybreak_Customers | type=802-11-wireless
[802-11-wireless] ssid=Daybreak_Customers | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Passio Free Wifi]] (600 root)
[connection] id=Passio Free Wifi | type=802-11-wireless
[802-11-wireless] ssid=Passio Free Wifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CAFE_EXPRESS-PERU]] (600 root)
[connection] id=CAFE_EXPRESS-PERU | type=802-11-wireless
[802-11-wireless] ssid=CAFE_EXPRESS-PERU | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/vintageemporium2]] (600 root)
[connection] id=vintageemporium2 | type=802-11-wireless
[802-11-wireless] ssid=vintageemporium2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LG X style_4520]] (600 root)
[connection] id=LG X style_4520 | type=802-11-wireless
[802-11-wireless] ssid=LG X style_4520 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HMARKAWASI- P1]] (600 root)
[connection] id=HMARKAWASI- P1 | type=802-11-wireless
[802-11-wireless] ssid=HMARKAWASI- P1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GFT_1]] (600 root)
[connection] id=GFT_1 | type=802-11-wireless
[802-11-wireless] ssid=GFT_1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Stop coffee Floor 1]] (600 root)
[connection] id=Stop coffee Floor 1 | type=802-11-wireless
[802-11-wireless] ssid=Stop coffee Floor 1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NaderPH]] (600 root)
[connection] id=NaderPH | type=802-11-wireless
[802-11-wireless] ssid=NaderPH | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Norwegian Internet Access]] (600 root)
[connection] id=Norwegian Internet Access | type=802-11-wireless
[802-11-wireless] ssid=Norwegian Internet Access | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BW TLC Hotel]] (600 root)
[connection] id=BW TLC Hotel | type=802-11-wireless
[802-11-wireless] ssid=BW TLC Hotel | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/INFINITUM0B20C9]] (600 root)
[connection] id=INFINITUM0B20C9 | type=802-11-wireless
[802-11-wireless] ssid=INFINITUM0B20C9 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dinhvinhlau1 1]] (600 root)
[connection] id=dinhvinhlau1 1 | type=802-11-wireless
[802-11-wireless] ssid=dinhvinhlau1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RED_STB]] (600 root)
[connection] id=RED_STB | type=802-11-wireless
[802-11-wireless] ssid=RED_STB | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Detroit Airport Wi-Fi]] (600 root)
[connection] id=Detroit Airport Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=Detroit Airport Wi-Fi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HOLLYS NTMK]] (600 root)
[connection] id=HOLLYS NTMK | type=802-11-wireless
[802-11-wireless] ssid=HOLLYS NTMK | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/icedtea]] (600 root)
[connection] id=icedtea | type=802-11-wireless
[802-11-wireless] ssid=icedtea | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Stop Coffee Ground Floor]] (600 root)
[connection] id=Stop Coffee Ground Floor | type=802-11-wireless
[802-11-wireless] ssid=Stop Coffee Ground Floor | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LetsGetSpanish]] (600 root)
[connection] id=LetsGetSpanish | type=802-11-wireless
[802-11-wireless] ssid=LetsGetSpanish | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Lima (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

lo        no frequency information.

virbr0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

coretemp

coretemp

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/10_touchpad] (755 root)
case "${1}" in
     resume|thaw)
             rmmod hid_multitouch
             modprobe hid_multitouch
             ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```

---

### Post by jeremy31 on 2017-03-29
I would remove the wireless card and reinstall it and see if it works after that.  Right now the wireless card is not being detected but the bluetooth part is.  Hopefully it is just the result of a bad connection and not the wireless card being broken

---

### Post by nadermx on 2017-03-29
Any specific way I should do that given that the laptop does not have a ethernet port?

---

### Post by jeremy31 on 2017-03-30
You need to physically remove the card from the computer and put it back in

---

