---
title: "Atheros AR928x"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by AelricTheMad on 2008-11-02
I recently installed Ubuntu 8.1, and am having trouble getting my wireless card to work, an Atheros using the AR928x chipset. I have installed the ath9k drivers, and the card is recognized and iwconfig gets me this output
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=27 dBm                                          
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
and lspci gets
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a3b:1067
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k
but I have no way of connecting to a wireless netwok. What do I do?

---

### Post by Zerimas on 2008-12-27
I believe I am in position similar to you.  Any help is much appreciated.

---

### Post by Nopposan on 2009-01-10
Same here.

---

