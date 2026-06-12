---
title: "Belkin F5D7000 (Rev 7) - RTL8185L - PLEASE HELP"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by dmosses on 2007-09-20
Hi

I've been trying to get this wireless card to work and am getting nowhere fast.  Can someone help me please.

I've downloaded, built and installed the latest version of ndiswrapper, and am trying to use the drivers from realtek website for the RTL8185L chipset but to no avail.

Actually - the first time I tried it worked :
 - built and installed ndiswrapper
 - ndiswrapper -l listed driver and card present.
 - went straight to /etc/network/interfaces and defined wireless-essid and wireless-key values
 - did a sudo ifup wlan0 and my router assigned me an ip address - all well and good.

Restarted - did't work any more.

In an attempt to simplify the problem I've turned on 'show ssid' and disabled wep, and MAC access control on my router.  I then removed the settings from /etc/network/interfaces, but still not joy.

lshw -C network shows me

```

*-network:1 DISABLED
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 5
       bus info: pci@02:05.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:31:2e:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.48+Realtek,11/22/2006,5.1094.1 latency=32 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: ioport:ac00-acff iomemory:df001000-df0011ff irq:10
```

Please, can anyone help me?

---

### Post by dmosses on 2007-09-20
Anyone?

If it's relevant I'm running Feisty 7.04 Server.  Would the fact that it's the server kernel affect this at all?


Here's some more output if it helps...

sudo iwconfig wlan0:

```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr=2432 B   Fragment thr=2432 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig does not display an entry for wlan0

---

### Post by jay3712 on 2007-09-21
Well you certainly got much further than I did with that card. I just gave up and bought a D-Link WDA-2320 and it simply works straight out of the box. I wish you luck, and a little bump for your thread.

---

