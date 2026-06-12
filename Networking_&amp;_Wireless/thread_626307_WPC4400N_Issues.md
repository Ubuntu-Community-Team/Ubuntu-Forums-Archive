---
title: "WPC4400N Issues"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by afk on 2007-11-28
i seem to be having an issue with any distro in getting this card to work i knows its an N draft card 300mbps i have windows drivers but ndiswrapper never opens


0b:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a02 (rev 03)

0b:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a02 (rev 03)
        Subsystem: Linksys Unknown device 0065
        Flags: 66MHz, medium devsel, IRQ 17
        Memory at 58000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Memory at 58010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2


Any help with getting this to work would be great :)

---

### Post by afk on 2008-06-26
so i got bored today and tried again and managed to get this card working at 260MB/s on hardy. sure beats 54mb G cards for network transfers!

i am also using wpa2 
heres the output.

wlan1     IEEE 802.11g  ESSID:"eh-ef-kay"  
Mode:Managed  Frequency:2.452 GHz  Access Point: 00:14:BF:BE:E7:2F   
Bit Rate=260 Mb/s   Sensitivity=-200 dBm  
RTS thr=2346 B   Fragment thr=2346 B   
Power Management:off
Link Quality:92/100  Signal level:-52 dBm  Noise level:-96 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

