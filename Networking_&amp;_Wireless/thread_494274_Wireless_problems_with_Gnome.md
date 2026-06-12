---
title: "Wireless problems with Gnome"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by jbaerbock on 2007-07-06
Well I have been dual booting WinXP and Mint for awhile now and my driver for Mint works perfectly for wireless. For some reason the gnome networkmanager that comes with Gnome doesnt like to connect to the wireless network I want to connect to. Sometimes it does and sometimes not. In windows i connect always no problem. My thought is that the problem comes from the fact that there are two wireless points called linksys (We from a few apartments share wireless so I cannot change the essid). The one I want to connect to has no encryption, the other called linksys has encryption. How can I force the network manager to connect to the one I want? When using KDE Linux distros I have no problems but even when I download the K network managers to gnome it still doesnt work well. Anyway to fix this. Attached will be the iwlist sessions output, the last one (in green) is the one I want to connect to. Please help as I love Gnome and dislike KDE so would rather use Gnome.

wlan0 Scan completed :
Cell 01 - Address: 00:16:B6:CD:50:AA
ESSID:"linksys"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:29/100 Signal level:-77 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Cell 02 - Address: 00:18:F8:78:EE:B0
ESSID:"linksys"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:14/100 Signal level:-87 dBm Noise level:-96 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
Cell 03 - Address: 00:17:3F:03:66:16
ESSID:"sarajenisarah"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:14/100 Signal level:-87 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
[COLOR="Lime"]Cell 04 - Address: 00:18:39:71:E4:D2
ESSID:"linksys"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:17/100 Signal level:-85 dBm Noise level:-96 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0[/COLOR]

---

### Post by spd106 on 2007-07-07
You are probably going to have to go into gconf and edit the bssid list to include just your AP's.
See [https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28)

---

### Post by jbaerbock on 2007-07-07
Resolved this problem by downloading and using Kwlan program for managing my network connections, works well in conjunction with firestarter for shared internet too.

---

