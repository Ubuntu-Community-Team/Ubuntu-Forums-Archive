---
title: "Wireless card not working after upgrade"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by valkyrie on 2007-05-28
I have a StarTech.com CB555WG wireless card (RaLink 2500 chipset) which worked out of the box under 6.06.  I was planning to upgrade, but there was a crash mid-upgrade and I couldn't figure out what went wrong, so I ended up doing a clean install instead.  Now I've got Feisty 7.04 running, but the wireless card isn't working.

Symptoms:
[LIST][*]Lights come on.
[*]Roaming mode can "see" networks (e.g. my home network, my neighbor's router, other networks when I'm downtown)
[*]It appears to try connecting, but almost never manages to complete a connection
[*]When it does get a connection, there's no DNS (can't ping external URL's, can't ping local 192.168 network)
[*]Behavior is the same regardless of whether network uses WEP or not
[*]Entering the wrong passwords for a WEP-encrypted network results in the same behavior as a correct password[/LIST]

Problems are pretty much the same whether I go through the automatic roaming, or try to manually configure the card.

Here's the relevant part of lspci -v :
```
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: RaLink Unknown device 2560
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at 24000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
```

I don't have the laptop hooked up to any network right now, so please avoid requesting any extremely long output -- I have to type it in by hand :D

---

### Post by valkyrie on 2007-05-28
Output from iwconfig:
```
lo     no wireless extensions

eth0   no wireless extensions

irda0  no wireless extensions

ra0    RT2500 Wireless  ESSID:""
       Mode:Managed  Frequency=2.412 GHz  Bit Rate: 11 Mb/s   Tx-Power: -2 dBm

       RTS thr:off   Fragment thr:off
       Link Quality=0/100  Signal level=-120 dBm  Noise level: -203 dBm
       Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0  Missed beacon:0
```

---

