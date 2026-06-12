---
title: "wireless issue Toshiba A205-S4577 ubuntu 7.10"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by NoEsAlAzar on 2007-12-15
Hello,

I have a Toshiba Satellite A205-S4577 working with Ubuntu 7.10 but I can't setup my wireless connection. This is the info of the card:

                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 02
                serial: 00:19:d2:b5:f2:bb
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated

If I go to System, Administration, Network tools, configure eth1 device, everything is disabled, so I can't setup my wireless connection.

any help will be highly appreciated!

---

### Post by NoEsAlAzar on 2007-12-16
Just for other owners of Toshiba Satellite A205-S4577. The mentioned card finally worked. I had to apply all the 7.10 updates AND there was a problem with router 2wire. For some reason I could never make it to work with Linux devices (tried with Ubuntu and Kubuntu). So instead I changed the router not to ask for authentification, but to limit user access by not broadcasting ESSID and blocking MAC addresses.

Saludos!

NoEsAlAzar

---

### Post by Edho on 2007-12-16
Hello NoEsAlAzar ,

Just for info.

I have the same card...and Ub 7.10 , router is Netgear Wrg614.
Worked out of box.
Question:
Do you managed Wpa security with the 3945 ?

---

