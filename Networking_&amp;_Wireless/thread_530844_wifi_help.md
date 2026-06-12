---
title: "wifi help"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by cryo4.rm on 2007-08-20
Wireless has never really worked for me in ubuntu but now less than ever...

 something i have done (and long enough ago now that i dont know WHAT) has removed the wireless option from my networking menu,,,,

 In 

 lshw

 shows my wireless device

*-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945 latency=0
                resources: iomemory:ff2ff000-ff2fffff irq:17

and 

lsmod

 shows the driver is loaded

ipw3945               118816  0 


but 

ifconfig

doesnt show the device (eth1)

joe@stan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


what can i do???

 any help? please .. thankyou

---

