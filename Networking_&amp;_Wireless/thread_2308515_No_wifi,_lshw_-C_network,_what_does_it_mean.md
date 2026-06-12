---
title: "No wifi, lshw -C network, what does it mean?"
date: 2016-01-03
forum: Networking &amp; Wireless
---

### Post by kiandrajayne on 2016-01-03
I just got a new laptop and installed Ubuntu 14.04.3 and I can't seem to get wireless working. I checked with lshw -C network, and this is what came up:

```
*-network UNCLAIMED
      description: Network controller
      product: Intel Corporation
      vendor: Intel Corporation
      physical id: 0
      bus info: pci@0000:02:00.0
      version: 81
      width: 64 bits
      clock: 33Mhz
      capabilities: pm msi pciexpress cap_list
      configuration: latency=0
      resources: memory:90500000-90501fff
```

From what I can tell by searching the web, the configuration is not supposed to say latency=0, nor is the network supposed to say UNCLAIMED, but I don't know how to fix it. Any help would be greatly appreciated.

---

### Post by kiandrajayne on 2016-01-09
I've been trying to fix this problem all day, but I still haven't come up with a result. If anyone needs me to post additional information, please let me know. As I'm new to Ubuntu, I'm not sure what information will help.

---

### Post by jeremy31 on 2016-01-09
Post the result of ```
lspci -nnk | grep -iA2 net; uname -a
```
Unclaimed usually means a kernel module is not loaded but since you have Intel wifi it can be fixed

---

### Post by kiandrajayne on 2016-01-09
Here's the result of the above command:
```
02:00.0 [COLOR=#ff0000]Net[/COLOR]work controller [0280]: Intel Corporation Device [8086:3165] (rev 81)
        Subsystem: Intel Corporation Device [8086:4010]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
Linux myubuntu 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
If it makes any difference, the coloured Net was as it is here in the result.

---

### Post by Bucky Ball on 2016-01-09
Welcome. Have you plugged in an ethernet cable and done an update, then pulled the cable and rebooted and, if the card still isn't working, checked Additional Drivers?

Odd as the majority of Intel cards work 'out of the box'. No doubt jeremy31 will have further clues ...

---

### Post by chili555 on 2016-01-09
The Intel 3165 probably can't be made to work before kernel version 4.2 and later. My esteemed colleague jeremy31 will probably suggest that you install Ubuntu 15.10 as I would also suggest.

---

### Post by kiandrajayne on 2016-01-09
@Bucky Ball: My laptop doesn't have an ethernet port, so I'm hoping I won't have to do that as I don't have an adapter.

@chili555: I'll install 15.10 and see if that helps. Also, love the quote in your signature; I'm a big BBT fan :)

---

### Post by kiandrajayne on 2016-01-09
Update: SOLVED. I updated to 15.10 and straight away my laptop connected to the modem. Thank you so much for the help.

---

