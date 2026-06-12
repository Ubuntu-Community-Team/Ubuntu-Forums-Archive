---
title: "Atheros Wireless Failed"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Iglu Sitar on 2008-04-02
I have an Atheros Communications AR5006EG wireless interface which was running fine up until yesterday, when it stopped scanning/connecting. I have tried connecting to my access point manually, with no success. I include some information:

lshw lists the device as disabled:
```
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:06:30:b7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.45+,06/21/2007,5.3.0.56 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

lsmod lists ndiswrapper as loaded.

iwconfig:
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Any help on this would be very much appreciated. Thanks.

---

