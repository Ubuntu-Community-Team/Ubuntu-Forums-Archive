---
title: "ndiswrapper not replacing driver"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by Frijole on 2007-10-18
I have gone through the entire ndiswrapper sequence

```

frijole@theBean:~$ cd /home/frijole/Desktop/driver
frijole@theBean:~/Desktop/driver$ sudo ndiswrapper -i net8185.inf
[sudo] password for frijole:
driver net8185 is already installed
frijole@theBean:~/Desktop/driver$ sudo ndiswrapper -m
module configuration already contains alias directive

frijole@theBean:~/Desktop/driver$ gksu gedit /etc/modules
frijole@theBean:~/Desktop/driver$ 
```

but in hardware manager it still states driver as rtl8180

Im lost....

---

### Post by Frijole on 2007-10-18
here is more

```
 description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:01:0a.0
                logical name: wlan0
                version: 20
                serial: 00:18:e7:28:0b:7d
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 latency=32 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g

```

is that the correct driver? on the cd that came with the modem the files are called: net8185.inf and rtl8185.sys, but this still says 8180 is installed? I have no idea what is going on

---

