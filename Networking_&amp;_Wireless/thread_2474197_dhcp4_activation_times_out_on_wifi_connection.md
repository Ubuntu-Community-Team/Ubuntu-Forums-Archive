---
title: "dhcp4 activation times out on wifi connection"
date: 2022-04-23
forum: Networking &amp; Wireless
---

### Post by gigabyte56 on 2022-04-23
I have a dual boot desktop, Windows 10 / Ubuntu 20.04, and for some reason unknown to me, ubuntu recently stopped connecting to my network router using wifi, whilst windows continued to work as before. All other devices (phones, tablet, tv, etc) continue to connect to the router ok. 

I have spent days looking for ways how to troubleshoot this, with little success. Not knowing much about networking hasn't helped. The problem started shortly after updating windows, but I myself can't see why that should be relevant. Certainly, I hadn't updated the ubuntu system manually for a while, although I do now note that 'Snap package updates are ... installed automatically' by the Software Updater (in case that's relevant).

I've since update the device driver (from [https://github.com/morrownr/8812au-20210629](https://github.com/morrownr/8812au-20210629)), but that hasn't helped. Any clues on how to resolve this issue would be greatly appreciated.

When I try to make a wifi connection, I get the following output from journalctl:

[FONT=courier new]root@ubuntu:~# journalctl -f -u NetworkManager -u wpa_supplicant

-- Logs begin at Sun 2021-11-28 18:19:37 GMT. --
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7580] device (wlan0): Activation: starting connection 'PLUSNET-3Q72H' (57653bb8-2b82-4d86-a980-a37d03059af3)
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7581] audit: op="connection-activate" uuid="57653bb8-2b82-4d86-a980-a37d03059af3" name="PLUSNET-3Q72H" pid=3110 uid=1000 result="success"
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7583] device (wlan0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7586] manager: NetworkManager state is now CONNECTING
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7591] device (wlan0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7595] device (wlan0): Activation: (wifi) access point 'PLUSNET-3Q72H' has security, but secrets are required.
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7595] device (wlan0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7633] device (wlan0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7639] device (wlan0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7644] device (wlan0): Activation: (wifi) connection 'PLUSNET-3Q72H' has security, and secrets exist.  No new secrets needed.
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7645] Config: added 'ssid' value 'PLUSNET-3Q72H'
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7645] Config: added 'scan_ssid' value '1'
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7645] Config: added 'bgscan' value 'simple:30:-70:86400'
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7645] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK'
Apr 23 19:49:20 ubuntu NetworkManager[1248]: <info>  [1650739760.7645] Config: added 'psk' value '<hidden>'
Apr 23 19:49:23 ubuntu NetworkManager[1248]: <info>  [1650739763.3410] device (wlan0): supplicant interface state: disconnected -> scanning
Apr 23 19:49:23 ubuntu NetworkManager[1248]: <info>  [1650739763.3411] device (p2p-dev-wlan0): supplicant management interface state: disconnected -> scanning
Apr 23 19:49:26 ubuntu wpa_supplicant[1296]: wlan0: Trying to associate with d8:d7:75:b9:c4:dd (SSID='PLUSNET-3Q72H' freq=5240 MHz)
Apr 23 19:49:26 ubuntu wpa_supplicant[1296]: wlan0: CTRL-EVENT-STARTED-CHANNEL-SWITCH freq=5240 ht_enabled=1 ch_offset=-1 ch_width=80 MHz cf1=5210 cf2=0
Apr 23 19:49:26 ubuntu NetworkManager[1248]: <info>  [1650739766.8348] device (wlan0): supplicant interface state: scanning -> associating
Apr 23 19:49:26 ubuntu NetworkManager[1248]: <info>  [1650739766.8348] device (p2p-dev-wlan0): supplicant management interface state: scanning -> associating
Apr 23 19:49:26 ubuntu wpa_supplicant[1296]: wlan0: Associated with d8:d7:75:b9:c4:dd
Apr 23 19:49:26 ubuntu wpa_supplicant[1296]: wlan0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Apr 23 19:49:26 ubuntu wpa_supplicant[1296]: wlan0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=GB
Apr 23 19:49:26 ubuntu NetworkManager[1248]: <info>  [1650739766.9434] device (wlan0): supplicant interface state: associating -> associated
Apr 23 19:49:26 ubuntu NetworkManager[1248]: <info>  [1650739766.9435] device (p2p-dev-wlan0): supplicant management interface state: associating -> associated
Apr 23 19:49:26 ubuntu NetworkManager[1248]: <info>  [1650739766.9831] device (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 23 19:49:26 ubuntu NetworkManager[1248]: <info>  [1650739766.9832] device (p2p-dev-wlan0): supplicant management interface state: associated -> 4-way handshake
Apr 23 19:49:27 ubuntu wpa_supplicant[1296]: wlan0: WPA: Key negotiation completed with d8:d7:75:b9:c4:dd [PTK=CCMP GTK=CCMP]
Apr 23 19:49:27 ubuntu wpa_supplicant[1296]: wlan0: CTRL-EVENT-CONNECTED - Connection to d8:d7:75:b9:c4:dd completed [id=0 id_str=]
Apr 23 19:49:27 ubuntu wpa_supplicant[1296]: bgscan simple: Failed to enable signal strength monitoring
Apr 23 19:49:27 ubuntu NetworkManager[1248]: <info>  [1650739767.0153] device (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 23 19:49:27 ubuntu NetworkManager[1248]: <info>  [1650739767.0154] device (wlan0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful. Connected to wireless network "PLUSNET-3Q72H"
Apr 23 19:49:27 ubuntu NetworkManager[1248]: <info>  [1650739767.0155] device (p2p-dev-wlan0): supplicant management interface state: 4-way handshake -> completed
Apr 23 19:49:27 ubuntu NetworkManager[1248]: <info>  [1650739767.0160] device (wlan0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Apr 23 19:49:27 ubuntu NetworkManager[1248]: <info>  [1650739767.0174] dhcp4 (wlan0): activation: beginning transaction (timeout in 45 seconds)
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <warn>  [1650739812.0765] dhcp4 (wlan0): request timed out
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.0766] dhcp4 (wlan0): state changed unknown -> timeout
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.0767] device (wlan0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.0782] manager: NetworkManager state is now DISCONNECTED
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <warn>  [1650739812.0814] device (wlan0): Activation: failed for connection 'PLUSNET-3Q72H'
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.0822] device (wlan0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.1050] dhcp4 (wlan0): canceled DHCP transaction
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.1051] dhcp4 (wlan0): state changed timeout -> done
Apr 23 19:50:12 ubuntu wpa_supplicant[1296]: wlan0: CTRL-EVENT-DISCONNECTED bssid=d8:d7:75:b9:c4:dd reason=3 locally_generated=1
Apr 23 19:50:12 ubuntu wpa_supplicant[1296]: wlan0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <warn>  [1650739812.1262] sup-iface[0x561238325920,wlan0]: connection disconnected (reason -3)
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.1263] device (wlan0): supplicant interface state: completed -> disconnected
Apr 23 19:50:12 ubuntu NetworkManager[1248]: <info>  [1650739812.1263] device (p2p-dev-wlan0): supplicant management interface state: completed -> disconnected

[/FONT]

Some info about my system:

[FONT=courier new]root@ubuntu:/etc/NetworkManager/system-connections# sudo uname -a; mokutil --sb-state; lsusb; rfkill list all; dkms status; iw dev

Linux ubuntu 5.4.0-81-generic #91-Ubuntu SMP Thu Jul 15 19:09:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
EFI variables are not supported on this system
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:a811 Realtek Semiconductor Corp. RTL8811AU 802.11a/b/g/n/ac WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:c211 HP, Inc Deskjet 2540 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
nvidia, 390.144, 5.4.0-73-generic, x86_64: installed
nvidia, 390.144, 5.4.0-81-generic, x86_64: installed
rtl8821au, 5.12.5.2, 5.4.0-81-generic, x86_64: installed
phy#0
    Interface wlan0
        ifindex 3
        wdev 0x1
        addr 00:e0:4c:3d:a4:d9
        type managed
        txpower 42949572.96 dBm
[/FONT]

---

### Post by gigabyte56 on 2022-04-26
Is there any help available, or should I buy another wifi adapter?

---

### Post by chili555 on 2022-04-26
Please check my troubleshooting steps here: [https://askubuntu.com/questions/1353705/ubuntu-20-04-wifi-keeps-dropping/1353723#1353723](https://askubuntu.com/questions/1353705/ubuntu-20-04-wifi-keeps-dropping/1353723#1353723)

---

### Post by gigabyte56 on 2022-04-28
Thanks for getting back to me, but I have now routed some cable around the house giving me a reliable wired connection. No more tedious wifi problems on ubuntu!

---

