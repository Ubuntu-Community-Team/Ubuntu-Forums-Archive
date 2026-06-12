---
title: "wifi key problem at each reboot of Hardy Heron"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by byulent on 2008-09-28
I am a new user of linux and ubuntu. My wifi connection work but each time I reboot the computer, I am asked for the key and security option. After a while it gets disturbing. When I entered to network icon -> edit wirless networks, the key and the security option is are set to some default values as "WEB 64/128 HEX" and "641d26d85ba5f62cbfed81c521" respectively. Once I change these options and exit the menu and reenter they are reset to these values again.  

Below are my right connection options except the key :)

Security: WEB 64/128-bit ASCII
Authentication: Open System
 
So how can I make the network options saved?  

I don't know whether it will be of any use but here is the outcome of the command "lshw -C network" that I learned from another thread:

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:39:27:93
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical   ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=***.***.***.*** latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


Thank you.

---

### Post by byulent on 2008-09-30
After some googling and forum searching, I found out that it is possible to replace the buggy default network manager with wicd. Now everything is fine. 

p.s. I do not understand why such a simple and obvious problem is not resolved up to know, I discovered many people suffering from the same keyring problem. Though there comes a new version of the network manager, I am not sure whether it will solve the problem. I suggest and hope that ubuntu community (or decision makers) will set wicd as the default network tool.

---

### Post by pterandon on 2008-09-30
> **byulent said:**
> 
p.s. I do not understand why such a simple and obvious problem is not resolved up to know, I discovered many people suffering from the same keyring problem. Though there comes a new version of the network manager, I am not sure whether it will solve the problem. I suggest and hope that ubuntu community (or decision makers) will set wicd as the default network tool.

I complained loudly about it in 7.04.

---

