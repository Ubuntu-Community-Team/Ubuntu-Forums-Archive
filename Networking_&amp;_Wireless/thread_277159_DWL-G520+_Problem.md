---
title: "DWL-G520+ Problem"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by Haegin on 2006-10-14
I have just installed dapper on a pc and the wireless card (which worked in hoary!) no longer works. Ubuntu picks it up but it can't seem to find the wireless network (even when it is less than a meter away) in network manager.
I have tried using ndiswrapper for it but to no avail and so I resorted to commandline tools. The output is all here

lspci -v
```

0000:02:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: D-Link System Inc DWL-G520+ Wireless PCI Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at ff9fe000 (32-bit, non-prefetchable) [size=8K]
        Memory at ff9c0000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <available only to root>

```

lspci -n
```

0000:02:0a.0 0280: 104c:9066

```

iwconfig wlan0
```

wlan0     IEEE 802.11b+/g+  ESSID:"STA147438"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:52/100  Signal level:34/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan
```

wlan0     Scan completed :
          Cell 01 - Address: FF:FF:00:0F:3D:B9
                    ESSID:""
                    Mode:Master
                    Channel:0
                    Quality=63/100  Signal level=49/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:2 Mb/s

```

If there is anything else anybody needs please say and I will happily give it to you (root password not included) but I am getting annoyed with this now.

Note - the essid of my home network is langside and its encrypted with 64bit wep.

---

