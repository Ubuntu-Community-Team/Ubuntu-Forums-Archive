---
title: "ubuntu not finiding wireless??"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by djbenny on 2007-05-19
it says its there in hardware info thing but it wont work at connecting through it at all its not on the list theres only wired.


EDIT:

INSTALLED SOME WIRELESS APPLICATIONS AND IT DECIDED TO WORK!

---

### Post by ola on 2007-05-19
Hi,

What happens if you run the command iwconfig in a terminal? Does it find your card there?

---

### Post by djbenny on 2007-05-20
i typed that in the terminal and the response was no wireless connections or something, i cant remember but there were two devices that showed up there.

if this heps i have a toshiba satellite pro 100-pspa4e

---

### Post by Kobalt on 2007-05-20
What is your wifi card model ? Can you please post the output of ```
sudo lshw -C network
```

---

### Post by djbenny on 2007-05-20
description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:8c100000-8c100fff irq:17


was the responce as well as the cable ethernet

---

### Post by djbenny on 2007-05-20
i need it urgently sorry about this but i need to get this sorted!

---

### Post by bukwirm on 2007-05-20
What's the output of "iwlist scan"?
Can you give information about the network you're trying to connect to? (essid, encryption type, etc.)

---

### Post by djbenny on 2007-05-20
there is no encryption or anything, the wireless is now down so i cannot test this..should be up within a few days :(

the output of iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by bukwirm on 2007-05-22
It appears that your wireless device is not enabled.
What is the output of "sudo lshw -C network"?

---

