---
title: "How to set default wireless network for all users?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by drucer on 2008-10-13
Hi,

ok here's my problem. I'm using Ubuntu 8.10 on Lenovo Thinkpad T61 and I am able to configure my wireless network (it is hidden wireless network requiring WEP 40/128 key) and connect to it, but what I don't like is Ubuntu discovers 5 other networks that are not mine and I have no intent to use so, how can I disable this "discovery" feature and configure Ubuntu to use my _one and only_ wireless connection?

Idea situation is - no matter who logs in - the network is there immediately without the need to enter any password or select the network.

---

### Post by drucer on 2008-10-13
Info:

       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:08:65:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless

---

### Post by surj08 on 2008-10-13
Im not using ubuntu right now(so i cant be very specific) but if you goto network settings ( i think you right click the network thing and togo manual config or somthing) then you can select your wireless and take if off roaming mode and put in all the info for your wireless and it will auto connect.

I do not know how to turn off the discovery though.

---

### Post by surj08 on 2008-10-13
Im not using ubuntu right now(so i cant be very specific) but if you goto network settings ( i think you right click the network thing and togo manual config or somthing) then you can select your wireless and take if off roaming mode and put in all the info for your wireless and it will auto connect.

I do not know how to turn off the discovery though.

---

### Post by drucer on 2008-10-13
> **surj08 said:**
> Im not using ubuntu right now(so i cant be very specific) but if you goto network settings ( i think you right click the network thing and togo manual config or somthing) then you can select your wireless and take if off roaming mode and put in all the info for your wireless and it will auto connect.

Yes, you were right. Right clicking the network icon (on top right) gave me options to manually set default wireless network. Thank you!

---

