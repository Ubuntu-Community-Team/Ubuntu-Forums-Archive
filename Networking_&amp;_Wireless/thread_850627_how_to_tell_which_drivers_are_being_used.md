---
title: "how to tell which drivers are being used?"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by ieee488 on 2008-07-05
I bought a D-Link DWL-G630 rev C2 on eBay and spent all afternoon trying to get it to work.

Nothing worked.

I shutdown my laptop and went to eat some dinner.
I get back from dinner, boot up the laptop, and lo and behold the wireless card is working.

I think I last tried using ndiswrapper, but I am not sure.

Is there a way to check which driver is being used?

I'm using Ubuntu 5.10.

---

### Post by chili555 on 2008-07-05
Please do:```
sudo lshw -C network
```One device will probably be ethernet and one will be wireless. The driver will be shown like this:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:c2:1b:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=iwl3945** ip=192.168.1.104 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by ieee488 on 2008-07-05
I guess Ubuntu 5.10 doesn't support the -C, but running just *sudo lshw* worked.

Thanks!

---

### Post by xcesarfrancox on 2008-07-05
Why are you still using Ubuntu 5.10???

---

### Post by ieee488 on 2008-07-05
Because the CD drive on this laptop doesn't read burned CDs.

I'll need to find a Ubuntu CD that is commercially produced.

---

### Post by xcesarfrancox on 2008-07-06
Try ordering free ubuntu cds from shipit: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by ieee488 on 2008-07-06
Yes, someone else suggested the same thing when I asked about upgrading 5.10.

I am too impatient to wait 10 weeks for a CD, so it will have to be a book with a CD.

---

### Post by kevdog on 2008-07-06
lsmod also gives a list of loaded kernel modules.  One of the modules in the list will be your driver.  Other modules however will be listed.

---

