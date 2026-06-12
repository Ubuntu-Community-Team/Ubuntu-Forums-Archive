---
title: "Wireless issues - prompting for encryption keys/slow speeds"
date: 2020-12-29
forum: Networking &amp; Wireless
---

### Post by sauk42 on 2020-12-29
I am experiencing constant prompts to update encryption keys and/or experiencing slow network speeds.  I am running Ubuntu 20.04.1 LTS on a Dell Inspiron N7110.  

I did recently edit /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf to below[connection]
#wifi.powersave = 3
wifi.powersave = 2/g
but I still get prompted for encryption keys.  

My wireless hardware is as follows. 
*-network                 
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 34
       serial: xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-58-generic firmware=18.168.6.1 ip=x.x.x.x latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:34 memory:d0600000-d0601fff


Any assistance is appreciated and if more information is need, please let me know.

---

