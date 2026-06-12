---
title: "Hardy doesn't recognize attansic gigabit ethernet card"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by tuxfire on 2008-05-25
Hello, my notebook is an acer 6920G-814G32Bn and this is the lspci output:

02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

under Vista i get:

Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller

i tried to install modules included in the distribution such as atl1.ko and atl2.ko but the card is down yet. How to know if mine is l1 o l2??

Any help? Without the net i must use Vista :(

(The audio is also down but this is the minor problem)

I'm desperated


thanks

---

### Post by chili555 on 2008-05-25
How about letting us see:```
sudo lshw -C network
```Thanks.

---

### Post by tuxfire on 2008-05-25
> **chili555 said:**
> How about letting us see:```
sudo lshw -C network
```Thanks.

no new useful infos with that command:

*-network UNCLAIMED
    description: Ethernet controller
    product:  Attansic Technology Corp.
    vendor:  Attansic Technology Corp.
    physical id: 0
    bus info:  pci@0000:02:00.0
    version:  b0
    width:  64 bits
    clock:  33 mhz
    capabilites: pm msi pciexpress vpd bus_master cap_limit
    configuration:  latency=0

thanks

---

### Post by tuxfire on 2008-05-25
solved:

[http://ubuntuforums.org/showthread.php?t=770173&highlight=no+ethernet+acer](http://ubuntuforums.org/showthread.php?t=770173&highlight=no+ethernet+acer)

thank you very much

---

