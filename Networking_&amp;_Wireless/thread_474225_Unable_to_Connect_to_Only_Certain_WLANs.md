---
title: "Unable to Connect to Only Certain WLANs"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by rmcgibbo on 2007-06-14
There are two _unsecured_ wireless networks accessible from my home. Linksys (my neighbors network) and BearGrylls, my own. I'm not sure what the type of router "Linksys" is using (besides the brand of course). BearGrylls is using a Netgear WNR834B (pre-N), but i turned it to just b/g mode trying to troubleshoot this issue.

The issue:
In WinXP i can connect to Linksys and BearGrylls. They work great.
In Feisty Fawn i can connect to Linksys and NOT BearGrylls. BearGrylls doesn't usualyl appear in the network-manager drop down menu after i book, but after trying to connect to it through "connect to other wireless network" (and failing) it does sometimes show up in the network-manager drop down menu, but usually with a really low signal strength. WinXP on the other hand shows a pretty good signal strength. When i click on BearGrylls to try to connect to it, or use "connect to other wireless network" to try the same, it tries for about 30 seconds to connect and then fails.

My configuration:
Wireless Card: Linksys WMP11 v1 PCI (Prism 2.5 Wavelan chipset)
In order to get the card running, prism2_pci is blacklisted.

SSID is being broadcast on BearGrylls.

Any ideas?

---

### Post by tturrisi on 2007-06-14
Understanding wifi cards:

Cards are built w/ certain specs such as miliwatts (input-output strength). and these specs vary from card to card.  It is the **driver** that utilizes a card's capabilities.  Your "issue" just means that the windows driver utilizes the card's capabilities better than the linux drive can, that's all.  The linux wireless-tools program IWLIST is what is used to scan for available networks.  This iwlist is used by network manager apps.  Open a term & type:
iwlist ethX scan
(where ethX - name of your card) & see all networks that have been detected.  If all you see is your own wlan then that means that there are no other wlans IN RANGE of your card while being run with the linux driver.

---

### Post by rmcgibbo on 2007-06-15
I am much much closer to the BearGrylls, the network which linux won't detect, than i am to linksys, the one it will. Windows confirms this, showing much higher signal strength for beargrylls than linksys.

Why should the linux driver only let me connect to certain networks and not other, closer networks?

---

### Post by tturrisi on 2007-06-15
Reported signal strength is unreliable at best.
Do
iwlist ethX scan
where ethX = your device name, either eth0, eth1, eth2, wlan0, wlan1, etc.
Post the results of the scan.

---

### Post by Drenormous on 2007-06-17
I have the same or similar problem (Xubuntu Dapper, WPC54Gv4).

I can see my own (unencrypted) network in the iwlist scan (usually, although sometimes it doesn't show up for whatever reason), but if I try to connect to it with either the System>Networking manager or by setting the essid or ap with iwconfig, it won't connect.  But it works fine with the neighbor's network, intermitantly (the neighbors are far away so the signal is only so-so).

Heck if I know what to do about it, though...
--------
Address: 00:14:BF:F9:D6:4B
                    ESSID:"this one works fine (I'm posting from it now)"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

Address: 00:12:17:04:CB:01
                    ESSID:"this one doesn't work"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by tturrisi on 2007-06-17
Go to the AP control panel via browser & change the channel the AP uses from 6 to another channel, such as 10 or 11.  There's interference on your channel 6.  And set the AP to use Both B & G modes instead of just G mode.

Address: 00:12:17:04:CB:01
ESSID:"this one doesn't work"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:0/100 Signal level:-73 dBm Noise level:-256 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0

Here's mine.  As you can see the Noise level is good, as is the Signal level.  But the reported signal level is bogus cause I',m 6' from my AP.

v240:~# iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0F:B5:9F:DD:04
                    ESSID:"8724"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/94  Signal level=-48 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

---

### Post by Drenormous on 2007-06-18
Yeah, that seems to have fixed it.  Thanks.

---

### Post by tturrisi on 2007-06-18
You're welcome & very well done.

---

