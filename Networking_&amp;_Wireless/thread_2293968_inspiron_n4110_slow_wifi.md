---
title: "inspiron n4110 slow wifi"
date: 2015-09-08
forum: Networking &amp; Wireless
---

### Post by irongolem0982 on 2015-09-08
so just installed ubuntu on my inspirion n4110 laptop. everything works great except for my wireless. i can connect to my network (which is 802.11g) and it holds the connection but the speed is so slow even watching youtube on 240p is impossible. although i get a 5mbps on speedtest.net (it should show 15mbps) i still cant figure out what is the problem...

info about the card:
*-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 34
       serial: 58:91:cf:58:be:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-25-generic firmware=18.168.6.1 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:32 memory:d0600000-d0601fff


*** also when i plugged it into Ethernet. everything worked just fine!!!!! and the speed was where it should be... have restarted the computer just to make sure its not that.... 

please help!!!!

---

### Post by jeremy31 on 2015-09-08
You may want to try ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot

If it doesn't help read the sticky post "before posting in networking and wireless" and post the results of the wireless script

---

### Post by irongolem0982 on 2015-09-08
just tried a command from another site that basically did the same thing (disable 802.11n) tried it once. didnt work. tried it the second time and the computer froze and we had to shut it down. on reboot it is showing a full 15mbps through the wireless card. not sure what happened! :P thanks!

---

### Post by jeremy31 on 2015-09-08
the 11n_disable=8 doesn't disable 802.11n at all, it actually enable the agg tx and increases speed.  I would ```
sudo gedit /etc/modprobe.d/iwlwifi.conf
``` and delete any line with options iwlwifi 11n_disable=1 then save and reboot

---

