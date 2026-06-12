---
title: "Long passphrase not recognized? Possible problem in nm-applet"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by leandromartinez98 on 2008-04-04
I have Ubuntu installed in a VAIO NR laptop. The wireless card is this one:

6:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
	Subsystem: Foxconn International, Inc. Unknown device e000
	Flags: fast devsel, IRQ 18
	Memory at fa000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

Just to note, I could make it work only with ndiswrapper, not with madwifi. 
The wireless network works
fine at my home, using WPA Personal security password. 

However, at work, where I cannot control the password of the network, I can't get my
wireless to connect. Everything seems fine, the wireless networks are visibile, etc. However,
whenever I try to connect to this network, the passphrase is systematically regected (it keeps asking for it again and again).

The only difference I see relative to my home network is that at work it is a passphrase, that means, it is longer and contains spaces. The network administrator has already tried to configure it without success, so I don't think it is a problem of wrong type of encryption.

The result of iwlist scan is this (not sure if it helps):

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:16:B6:44:77:61
                    ESSID:"redeUFSC Sem Fio"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-67 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:1B:11:92:4E:72
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:13:46:97:D3:5A
                    ESSID:"carbono"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-72 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK

eth0      Interface doesn't support scanning.


I should be connecting to the "carbono" network. I tried to send the passphrase 
with "\" before spaces, between commas, and with all combinations of security
types and encriptions. 

One very specific question is: Which is the file that contains my passphrase information,
saved by the nm-applet? I would like to modify it by hand to see if that solves the problem.

Thanks for any other idea,
Leandro.

---

### Post by leandromartinez98 on 2008-04-04
Just to add: All networks work fine under Windows.

---

