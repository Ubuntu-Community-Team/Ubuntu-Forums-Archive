---
title: "Linksys WRT54G Router Problems"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by duckysrmyfriends on 2007-09-12
Hi. First let me say that I'm a complete and total noob to Ubuntu. I've seen a few tutorials around for this issue, but none that work specifically for me. 

I'm having a problem connecting wirelessly to my Linksys WRT54G V8 router. It recognizes all the wireless networks around here, and prompts me to put in the encryption key for our network. However, it just cycles until timeout, unable to connect to the network. The key is correct, and I didn't have any problems connecting to an earlier version of this router (my old roommate took it, so i bought a new one). 

I also don't have any problems connecting to wireless at my university, or at local coffee shops, just my home network. The router was set up using WinXP on my current roommate's computer, and I can connect just fine when I boot to WinXP. It also works fine in Ubuntu when wired with an ethernet cable. 

I'd just like to be able to connect wirelessly at home. What should I do?

Anne

---

### Post by noob12 on 2007-09-12
By any chance were you using WEP before but are now using WPA?  

Can you post the output of these:
```

sudo lshw -C network

sudo iwlist scan

iwconfig

```

---

### Post by duckysrmyfriends on 2007-09-20
> *sudo lshw -C network*

  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ba:c3:9b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=full ip=192.168.1.103 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:43:37:fd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.1 firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:faffd000-faffdfff irq:5

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:4C:B9:87
                    ESSID:"Gemeine-Ente"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=99/100  Signal level=-23 dBm
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: 00:11:24:5F:A2:C3
                    ESSID:"Steakhouse WiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=84/100  Signal level=-46 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 176ms ago
          Cell 03 - Address: 00:18:39:78:6F:16
                    ESSID:"federer"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=68/100  Signal level=-59 dBm
                    Extra: Last beacon: 204ms ago
          Cell 04 - Address: 00:14:6C:F9:19:C0
                    ESSID:"ApfelschorleDrei"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=35/100  Signal level=-79 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 44ms ago
          Cell 05 - Address: 00:14:BF:E7:34:F6
                    ESSID:"charles"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=39/100  Signal level=-77 dBm
                    Extra: Last beacon: 16ms ago
          Cell 06 - Address: 00:16:01:92:EC:DA
                    ESSID:"HarryPotterDies"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=51/100  Signal level=-70 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8ms ago
          Cell 07 - Address: 00:18:39:CC:D7:7C
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=29/100  Signal level=-82 dBm
                    Extra: Last beacon: 2720ms ago
          Cell 08 - Address: 00:18:39:B6:C7:83
                    ESSID:"Speedway"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:8
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=48/100  Signal level=-72 dBm
                    Extra: Last beacon: 2324ms ago
          Cell 09 - Address: 00:1C:10:8D:00:2E
                    ESSID:"binrobert"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=37/100  Signal level=-78 dBm
                    Extra: Last beacon: 788ms ago
          Cell 10 - Address: 00:1B:2F:08:38:5C
                    ESSID:"John Galt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=39/100  Signal level=-77 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 100ms ago
          Cell 11 - Address: 00:1C:B3:AB:32:C7
                    ESSID:"Lomar"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=27/100  Signal level=-83 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2208ms ago
          Cell 12 - Address: 00:02:6F:35:31:B1
                    ESSID:"TRK-EMS"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:3
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=51/100  Signal level=-82 dBm
                    Extra: Last beacon: 1112ms ago
          Cell 13 - Address: 00:0E:9B:24:EB:5C
                    ESSID:"481a"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=27/100  Signal level=-83 dBm
                    Extra: Last beacon: 6260ms ago
          Cell 14 - Address: 00:18:3F:28:60:59
                    ESSID:"2WIRE509"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54
                    Quality=33/100  Signal level=-80 dBm
                    Extra: Last beacon: 1344ms ago
          Cell 15 - Address: 00:18:39:6A:01:B0
                    ESSID:"bunchies"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=39/100  Signal level=-77 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 76ms ago
          Cell 16 - Address: 00:14:51:75:E9:2D
                    ESSID:"tie-dye dolphins"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=41/100  Signal level=-76 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 492ms ago
          Cell 17 - Address: 00:0C:41:F3:CF:18
                    ESSID:"shanenet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=31/100  Signal level=-81 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8244ms ago
          Cell 18 - Address: 00:1B:5B:95:5C:89
                    ESSID:"2WIRE776"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54
                    Quality=29/100  Signal level=-82 dBm
                    Extra: Last beacon: 3540ms ago
          Cell 19 - Address: 00:90:4C:7E:00:6E
                    ESSID:"; )"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=37/100  Signal level=-78 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 472ms ago

sit0      Interface doesn't support scanning.



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





I'm connected via wired connection now. 

Both the old and new connection use the same security format. I believe they're WEP. (In order to access the wireless network we needed a 26-digit code). 

Thanks for your help!

---

### Post by dannemil on 2007-09-20
> **duckysrmyfriends said:**
> I'm connected via wired connection now. 

Both the old and new connection use the same security format. I believe they're WEP. (In order to access the wireless network we needed a 26-digit code). 

Thanks for your help!

Here is part of the problem:

iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSID: off/any
Mode:Managed Channel=0 Access Point: Not-Associated
Bit Rate=0 kb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thr: off Fragment thr: off
Power Management: off
Link Quality: 0 Signal level:0 Noise level: 0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

You need to know the ESSID (network name) of the wireless router that you want to connect to. Look in that long list of cells that showed up when you scanned for wireless networks and find the one that is your router. Write down or copy it's ESSID.

Then edit your interfaces file as root (like: sudo nano /etc/network/interfaces). Find the section that corresponds to your wireless interface (it looks here like it is eth1). Then make sure that section looks like this:

auto eth1
iface eth1 inet dhcp
wireless-essid <insert the name of your ESSID here - no brackets, no quotes>
wireless-key <insert your wireless encryption key here - also no brackets>

Save the interfaces file.
Restart networking: sudo /etc/init.d/networking restart

You should be good to go.

---

### Post by duckysrmyfriends on 2007-09-25
Actually, I think I realized what the problem is, and I'm looking around to see if I can figure out the solution. 

It turns out my wireless has gone from WEP to WPA. And network manager doesn't let me select WPA when it prompts me to enter the passphrase. I could switch the network back to WEP on my roommate's computer, but I was hoping there was some way I could access my network through WPA. I use Network Manager because my university has a specific security certificate needed for the network, and the default network connect doesn't support that. I try "connect to other wireless network" and put in my network name and select "WPA personal" and the code, but it doesn't want to connect.

We'll see if I can find  solution to it. Thanks for all your help. :)

---

