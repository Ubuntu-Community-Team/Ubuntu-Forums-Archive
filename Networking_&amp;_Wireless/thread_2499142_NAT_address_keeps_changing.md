---
title: "NAT address keeps changing"
date: 2024-07-14
forum: Networking &amp; Wireless
---

### Post by temporos on 2024-07-14
Running 22.04.4, fully updated. I noticed that my internet connections keep dropping while browsing the web, streaming videos/music, or gaming. I also noticed this (below) appearing in the system log. It looks like Ubuntu is releasing its IP address and requesting a new one from the router. I don't see a regular interval when this happens. Sometimes it happens 20 minutes apart, sometimes 1 minute apart.

Any idea why Ubuntu is doing this and how to fix it?

```
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: WNM: Disassociation Imminent - Disassociation Timer 60
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: WNM: Preferred List Available
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: SME: Trying to authenticate with xx:xx:xx:xx:8b:ac (SSID='Pikachu' freq=5500 MHz)
Jul 14 17:13:56 host kernel: [ 8246.290982] wlo1: disconnect from AP xx:xx:xx:xx:8b:a8 for new auth to xx:xx:xx:xx:8b:ac
Jul 14 17:13:56 host kernel: [ 8246.358636] wlo1: authenticate with xx:xx:xx:xx:8b:ac
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6601] device (wlo1): supplicant interface state: completed -> authenticating
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6601] device (p2p-dev-wlo1): supplicant management interface state: completed -> authenticating
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6604] device (wlo1): ip:dhcp4: restarting
Jul 14 17:13:56 host kernel: [ 8246.363806] wlo1: send auth to xx:xx:xx:xx:8b:ac (try 1/3)
Jul 14 17:13:56 host gnome-shell[2425]: An active wireless connection, in infrastructure mode, involves no access point?
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: Trying to associate with xx:xx:xx:xx:8b:ac (SSID='Pikachu' freq=5500 MHz)
Jul 14 17:13:56 host kernel: [ 8246.395611] wlo1: authenticated
Jul 14 17:13:56 host kernel: [ 8246.397760] wlo1: associate with xx:xx:xx:xx:8b:ac (try 1/3)
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6936] dhcp4 (wlo1): canceled DHCP transaction
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6936] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6937] dhcp4 (wlo1): state changed no lease
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6937] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6939] device (wlo1): ip:dhcp6: restarting
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6939] dhcp6 (wlo1): canceled DHCP transaction
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6939] dhcp6 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6939] dhcp6 (wlo1): state changed no lease
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6940] dhcp6 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6958] device (wlo1): supplicant interface state: authenticating -> associating
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.6958] device (p2p-dev-wlo1): supplicant management interface state: authenticating -> associating
Jul 14 17:13:56 host kernel: [ 8246.402805] wlo1: RX ReassocResp from xx:xx:xx:xx:8b:ac (capab=0x1011 status=0 aid=22)
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: Associated with xx:xx:xx:xx:8b:ac
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Jul 14 17:13:56 host kernel: [ 8246.410833] wlo1: associated
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.7131] device (wlo1): supplicant interface state: associating -> associated
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.7132] device (p2p-dev-wlo1): supplicant management interface state: associating -> associated
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: WPA: Key negotiation completed with xx:xx:xx:xx:8b:ac [PTK=CCMP GTK=CCMP]
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:8b:ac completed [id=0 id_str=]
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.7290] device (wlo1): supplicant interface state: associated -> completed
Jul 14 17:13:56 host NetworkManager[712]: <info>  [1720991636.7298] device (p2p-dev-wlo1): supplicant management interface state: associated -> completed
Jul 14 17:13:56 host kernel: [ 8246.450389] wlo1: Limiting TX power to 24 (24 - 0) dBm as advertised by xx:xx:xx:xx:8b:ac
Jul 14 17:13:56 host wpa_supplicant[748]: wlo1: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-61 noise=9999 txrate=29200
Jul 14 17:13:57 host NetworkManager[712]: <info>  [1720991637.7341] dhcp6 (wlo1): state changed new lease, address=xxxx:xxxx:xxxx:b550::48
Jul 14 17:13:57 host dbus-daemon[711]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.9' (uid=0 pid=712 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul 14 17:13:57 host systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul 14 17:13:57 host dbus-daemon[711]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 14 17:13:57 host systemd[1]: Started Network Manager Script Dispatcher Service.
Jul 14 17:14:02 host NetworkManager[712]: <info>  [1720991642.0805] dhcp4 (wlo1): state changed new lease, address=192.168.1.250
Jul 14 17:14:02 host avahi-daemon[707]: Withdrawing address record for 192.168.1.249 on wlo1.
Jul 14 17:14:02 host avahi-daemon[707]: Leaving mDNS multicast group on interface wlo1.IPv4 with address 192.168.1.249.
Jul 14 17:14:02 host avahi-daemon[707]: Interface wlo1.IPv4 no longer relevant for mDNS.
Jul 14 17:14:02 host avahi-daemon[707]: Joining mDNS multicast group on interface wlo1.IPv4 with address 192.168.1.250.
Jul 14 17:14:02 host avahi-daemon[707]: New relevant interface wlo1.IPv4 for mDNS.
Jul 14 17:14:02 host avahi-daemon[707]: Registering new address record for 192.168.1.250 on wlo1.IPv4.
Jul 14 17:14:11 host wpa_supplicant[748]: wlo1: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-62 noise=9999 txrate=29200
Jul 14 17:14:12 host systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Jul 14 17:14:15 host wpa_supplicant[748]: wlo1: SME: Trying to authenticate with xx:xx:xx:xx:8b:a8 (SSID='Pikachu' freq=5240 MHz)
Jul 14 17:14:15 host kernel: [ 8264.974461] wlo1: disconnect from AP xx:xx:xx:xx:8b:ac for new auth to xx:xx:xx:xx:8b:a8
Jul 14 17:14:15 host kernel: [ 8265.050384] wlo1: authenticate with xx:xx:xx:xx:8b:a8
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3516] device (wlo1): supplicant interface state: completed -> authenticating
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3516] device (p2p-dev-wlo1): supplicant management interface state: completed -> authenticating
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3516] device (wlo1): ip:dhcp4: restarting
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3517] dhcp4 (wlo1): canceled DHCP transaction
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3517] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3517] dhcp4 (wlo1): state changed no lease
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3517] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3518] device (wlo1): ip:dhcp6: restarting
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3518] dhcp6 (wlo1): canceled DHCP transaction
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3518] dhcp6 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3518] dhcp6 (wlo1): state changed no lease
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3518] dhcp6 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Jul 14 17:14:15 host kernel: [ 8265.054700] wlo1: send auth to xx:xx:xx:xx:8b:a8 (try 1/3)
Jul 14 17:14:15 host wpa_supplicant[748]: wlo1: Trying to associate with xx:xx:xx:xx:8b:a8 (SSID='Pikachu' freq=5240 MHz)
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3843] device (wlo1): supplicant interface state: authenticating -> associating
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.3843] device (p2p-dev-wlo1): supplicant management interface state: authenticating -> associating
Jul 14 17:14:15 host kernel: [ 8265.087585] wlo1: authenticated
Jul 14 17:14:15 host kernel: [ 8265.093600] wlo1: associate with xx:xx:xx:xx:8b:a8 (try 1/3)
Jul 14 17:14:15 host kernel: [ 8265.097519] wlo1: RX ReassocResp from xx:xx:xx:xx:8b:a8 (capab=0x1011 status=0 aid=19)
Jul 14 17:14:15 host wpa_supplicant[748]: wlo1: Associated with xx:xx:xx:xx:8b:a8
Jul 14 17:14:15 host kernel: [ 8265.108436] wlo1: associated
Jul 14 17:14:15 host kernel: [ 8265.108496] wlo1: Limiting TX power to 30 (30 - 0) dBm as advertised by xx:xx:xx:xx:8b:a8
Jul 14 17:14:15 host wpa_supplicant[748]: wlo1: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.4117] device (wlo1): supplicant interface state: associating -> associated
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.4117] device (p2p-dev-wlo1): supplicant management interface state: associating -> associated
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.4195] device (wlo1): supplicant interface state: associated -> 4way_handshake
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.4195] device (p2p-dev-wlo1): supplicant management interface state: associated -> 4way_handshake
Jul 14 17:14:15 host wpa_supplicant[748]: wlo1: WPA: Key negotiation completed with xx:xx:xx:xx:8b:a8 [PTK=CCMP GTK=CCMP]
Jul 14 17:14:15 host wpa_supplicant[748]: wlo1: CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:8b:a8 completed [id=0 id_str=]
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.4269] device (wlo1): supplicant interface state: 4way_handshake -> completed
Jul 14 17:14:15 host wpa_supplicant[748]: wlo1: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-55 noise=9999 txrate=245000
Jul 14 17:14:15 host NetworkManager[712]: <info>  [1720991655.4273] device (p2p-dev-wlo1): supplicant management interface state: 4way_handshake -> completed
Jul 14 17:14:16 host NetworkManager[712]: <info>  [1720991656.4564] dhcp6 (wlo1): state changed new lease, address=xxxx:xxxx:xxxx:b550::48
Jul 14 17:14:16 host dbus-daemon[711]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.9' (uid=0 pid=712 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul 14 17:14:16 host systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul 14 17:14:16 host dbus-daemon[711]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 14 17:14:16 host systemd[1]: Started Network Manager Script Dispatcher Service.
Jul 14 17:14:17 host NetworkManager[712]: <info>  [1720991657.3690] dhcp4 (wlo1): state changed new lease, address=192.168.1.250
Jul 14 17:14:27 host systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
```

---

### Post by currentshaft on 2024-07-15
Likely channel interference. Check the following output:

sudo iwlist wl0 scan |  grep -A5 Cell | sed 's/: ..:..:..:..:../: 00:00:00:00:00/g'

Not sure what NAT has to do with anything, since you only described being disconnected from a wireless AP. Did I miss a detail?

---

### Post by temporos on 2024-07-15
Here is the result of that command...
```
user@host:~$ sudo iwlist wlo1 scan | grep -A5 Cell | sed 's/: ..:..:..:..:../: 00:00:00:00:00/g'
          Cell 01 - Address: 00:00:00:00:00:AC
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Pikachu"
--
          Cell 02 - Address: 00:00:00:00:00:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"NikkiB"
--
          Cell 03 - Address: 00:00:00:00:00:90
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"ATTHwuuBUI"
--
          Cell 04 - Address: 00:00:00:00:00:64
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"iDev"
--
          Cell 05 - Address: 00:00:00:00:00:F4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"CharDee MacDennis"
--
          Cell 06 - Address: 00:00:00:00:00:34
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"ATTsZEDZsb"
--
          Cell 07 - Address: 00:00:00:00:00:30
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"ATT9Pf4GNa"
--
          Cell 08 - Address: 00:00:00:00:00:74
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"ATTw3S42Ia"
--
          Cell 09 - Address: 00:00:00:00:00:74
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Nacho Interwebs!"
--
          Cell 10 - Address: 00:00:00:00:00:75
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Nacho Guest Interwebs!"
--
          Cell 11 - Address: 00:00:00:00:00:54
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ATTzux68Gu"
--
          Cell 12 - Address: 00:00:00:00:00:86
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Verizon_7WVSZT"
--
          Cell 13 - Address: 00:00:00:00:00:74
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"ATTjCs8gcp"
--
          Cell 14 - Address: 00:00:00:00:00:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-3F-HP ENVY 4520 series"
--
          Cell 15 - Address: 00:00:00:00:00:97
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Alpha117"
--
          Cell 16 - Address: 00:00:00:00:00:84
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"ATT3uXYAk6"
--
          Cell 17 - Address: 00:00:00:00:00:84
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ATT9KJIW4V"
--
          Cell 18 - Address: 00:00:00:00:00:A4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Pikachu"
--
          Cell 19 - Address: 00:00:00:00:00:74
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"FBISurveillanceVan"
--
          Cell 20 - Address: 00:00:00:00:00:F4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ATT4fyHNdB"
--
          Cell 21 - Address: 00:00:00:00:00:33
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"ATT9Pf4GNa"
--
          Cell 22 - Address: 00:00:00:00:00:8C
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ATT9KJIW4V"
--
          Cell 23 - Address: 00:00:00:00:00:6C
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"iDev"
--
          Cell 24 - Address: 00:00:00:00:00:8C
                    Channel:132
                    Frequency:5.66 GHz (Channel 132)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ATT3uXYAk6"
--
          Cell 25 - Address: 00:00:00:00:00:8F
                    Channel:132
                    Frequency:5.66 GHz (Channel 132)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
--
          Cell 26 - Address: 00:00:00:00:00:7C
                    Channel:132
                    Frequency:5.66 GHz (Channel 132)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ATTw3S42Ia"
--
          Cell 27 - Address: 00:00:00:00:00:7C
                    Channel:108
                    Frequency:5.54 GHz (Channel 108)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ATTjCs8gcp"
--
          Cell 28 - Address: 00:00:00:00:00:7F
                    Channel:108
                    Frequency:5.54 GHz (Channel 108)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
--
          Cell 29 - Address: 00:00:00:00:00:FC
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"CharDee MacDennis"
--
          Cell 30 - Address: 00:00:00:00:00:F8
                    Channel:56
                    Frequency:5.28 GHz (Channel 56)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"CharDee MacDennis"
--
          Cell 31 - Address: 00:00:00:00:00:A8
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Pikachu"
--
          Cell 32 - Address: 00:00:00:00:00:88
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ATT3uXYAk6"
--
          Cell 33 - Address: 00:00:00:00:00:88
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"ATT9KJIW4V"
--
          Cell 34 - Address: 00:00:00:00:00:87
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Verizon_7WVSZT"
```

My WiFi is called *Pikachu*. It's operating on channels 52 and 161, and it looks like two other WiFi networks (*ATT9Pf4GNa* and *ATT9KJIW4V*)  are operating on channel 161. Unfortunately, AT&T will let  me change router settings only via their Android app, and it won't let  me explicitly set a new channel. I have to let it scan for the "best"  channel, and then it sets what it wants. It currently thinks channel 161  is the "best" channel.

I mentioned "NAT" in the thread title, because I wanted to avoid any misunderstanding that it was my *public* IP that was changing. It's my *local* network IP that's being refreshed repeatedly.

---

