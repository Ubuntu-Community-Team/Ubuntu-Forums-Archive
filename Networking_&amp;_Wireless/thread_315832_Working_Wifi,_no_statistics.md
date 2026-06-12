---
title: "Working Wifi, no statistics?"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by voltagex on 2006-12-09
I'm posting this from a working wifi connection in Ubuntu Edgy, except for one strange problem. There's no statistics or status, from the GUI or the command line.

iwconfig:
```


rausb0    RT2500USB WLAN  ESSID:"wireless"  
          Mode:Managed  Frequency=2.412 GHz  Access Point:00:16:38:C6:FD:E0   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-37 dBm  Noise level:-208 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The card is an MSI mini-PCI using the rt2750 driver provided with Ubuntu

```

Bus 004 Device 002: ID 0db0:6865 Micro Star International 
  idVendor           0x0db0 Micro Star International
  idProduct          0x6865 
  bcdDevice            0.01
  iManufacturer           1 Ralink
  iProduct                2 802.11g WLAN + Pen Drive

```

Note this is only since a clean install of Edgy. On 6.06 it was fine. As well as the statistics problem, iwlist scan turns up nothing either (kismet works fine)

---

