---
title: "Intermittent loss of ethernet network connectivity with Broadcom BCM5761"
date: 2019-02-07
forum: Networking &amp; Wireless
---

### Post by Briasaurus Rex on 2019-02-07
Hey folks,

Here's my issue in a nutshell: a few weeks after updating to 18.04 from 16.04, I began to have issues with ethernet network connectivity. Occasionally, my connection to both the internet and other devices on the LAN will be dropped. Packet transmission doesn't go totally to zero, but oscillates around ~0.5 - 7 KiB/s. Toggling the network connection off and on through the Network Manager successfully re-establishes the connection, but the connection will inevitably be lost again. I haven't been able to determine what triggers the disconnect and the duration of network uptime is seemingly random. Sometimes it'll last a few seconds, other times it will last ~30 minutes. I'm also not sure exactly what caused the problem to appear in the first place. Probably an update/upgrade at some point after the move to 18.04, but it's hard to pinpoint.

Here's the output of ```
lspci -knn | grep Eth -A3
```

```
06:00.0 [COLOR=#EF2929]**Eth**[/COLOR]ernet controller [0200]: Broadcom Limited NetXtreme BCM5761 Gigabit [COLOR=#EF2929]**Eth**[/COLOR]ernet PCIe [14e4:1681] (rev 10)
    Subsystem: Dell NetXtreme BCM5761 Gigabit [COLOR=#EF2929]**Eth**[/COLOR]ernet PCIe [1028:026d]
    Kernel driver in use: tg3
    Kernel modules: tg3
07:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]

```

I'm using kernel 4.15.0-45-generic. I've run ye olde apt-cache update / upgrade, rebooted, and dug around extensively through different forums to no avail. Any ideas would be appreciated.

---

### Post by Briasaurus Rex on 2019-02-11
Update: based on the output of ```
journalctl  /usr/sbin/NetworkManager
``` it looks like the ethernet is reporting  a time out error, re-establishing the CONNECTED_SITE status, but then  returning to time outs.

---

