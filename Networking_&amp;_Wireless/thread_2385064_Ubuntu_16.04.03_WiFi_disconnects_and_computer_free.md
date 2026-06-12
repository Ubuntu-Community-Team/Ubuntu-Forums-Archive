---
title: "Ubuntu 16.04.03 WiFi disconnects and computer freezes"
date: 2018-02-15
forum: Networking &amp; Wireless
---

### Post by functionalburrito on 2018-02-15
Sometimes, my WiFi randomly disconnects and the computer freezes. Well, to be accurate, the computer doesn't completely "freeze", but rather the mouse freezes and everything runs super slowly. The keyboard still works, but it's sluggish and bash commands take forever to run.

Ubuntu version is 16.04.03
Kernel version is 4.13.0-32-generic
I've already tried switching between various kernel versions, and it doesn't fix the issue. 

Here is the result for lshw (network section)
```

  *-network               
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wls8
       version: 79
       serial: 84:ef:18:66:72:f9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-32-generic firmware=29.610311.0 ip=10.101.6.70 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:286 memory:d1000000-d1001fff

```

lsusb
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 2386:3111  
Bus 001 Device 006: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 0bda:58c2 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

iwconfig
```

wls8      IEEE 802.11  ESSID:"ssid"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 64:F6:9D:AB:40:14   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:326   Missed beacon:0


lo        no wireless extensions.

```

Any suggestions on what I should do to find the issue/fix the issue?

---

### Post by mörgæs on 2018-02-17
Hi, welcome to the fora.

This is far from 'freeze'. Sounds just like a process is putting a heavy workload on the processor.

Does **top** show any greedy processes running when it happens?

---

### Post by praseodym on 2018-02-17
Sounds like a VGA issue?!
```
lspci -nnk | grep -iA2 VGA
lsmod
```

---

