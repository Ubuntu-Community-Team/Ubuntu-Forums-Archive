---
title: "ndiswrapper - installs ok, wlan0 there, sees the AP, won't connect"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by CamB on 2005-11-14
Ok, yet another ndiswrapper question...

P4 with 686 kernel, USB is a generic one with PRISMA02.inf from its CD used for the driver. The card/driver definitely works in Hoary on a different machine, but here is the problem on this machine in Breezy:

ndiswrapper install the driver fine. Its there in the log, as per the ndiswrapper instructions:

```
[4294687.632000] ndiswrapper version 1.5 loaded (preempt=no,smp=no)
[4294687.674000] ndiswrapper: driver prisma02 (GlobespanVirata,01/07/2004, 1.00.8.0) loaded
[4294692.116000] wlan0: vendor: 'PRISM 802.11b/g Adapter (USB)'
[4294692.116000] wlan0: ndiswrapper ethernet device 00:06:f4:07:c2:32 using driver prisma02, 09AA:1000.0.conf
[4294692.116000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[4294692.116000] usbcore: registered new driver ndiswrapper

```

And it's there in iwconfig:

```
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But note the Access Point address being all 00s - the card can see the Access Point - from iwlist wlan0 scan:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:41:71:A4
                    ESSID:"39elizabeth"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-60 dBm  Noise level:-256 dBm
                    Encryption key:off
```

But... the output of iwconfig above does change if I follow the ndiswrapper instructions and use iwconfig wlan0 essid 39elizabeth. Basically, it seems the USB wireless adaptor doesn't want to associate with the AP.

---

### Post by CamB on 2005-11-15
Further info - the bit about wireless extension was bugging me, so I updated that, and uninstalled and re-installed ndiswrapper.

Somewhere in the mix, I did something right, because now it seems to work...

---

### Post by marcel.patoulachi on 2005-11-15
[QUOTE=CamB]Somewhere in the **mix**, I did something right, because now it seems to work...[/QUOTE]

congratulations...it means u're a good dj :p

---

