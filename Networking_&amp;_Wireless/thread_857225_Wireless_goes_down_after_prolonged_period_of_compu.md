---
title: "Wireless goes down after prolonged period of computer shutdown, needs restart"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by KingNeil on 2008-07-12
I'm running a Dell XPS M1530 and the wireless works fine, but if I leave it for prolonged period of time, it switches off and thus I have to restart the computer. Mine is the Intel ABG3945 btw, with the iwl driver

I think this must be something to do with power management, like when I was running Vista on this same machine.

Does anyone have any ideas on how I can prevent this problem. Pretty much whenever I start up the computer, the wireless is down and I have to reboot. It's damn annoying.

This is a bit of extra info if it helps (after I entered sudo lshw -C network into the terminal):

> 
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:17:92:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.67 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


---

### Post by KingNeil on 2008-07-12
bump

---

### Post by KingNeil on 2008-07-12
Bump

---

