---
title: "No Network interfaces after Ubuntu driver update"
date: 2022-07-09
forum: Networking &amp; Wireless
---

### Post by federikowsky on 2022-07-09
before running the nvidia driver update everything worked. After the reboot, the interfaces disappeared. I haven't run any terminal commands I've used
applications-> software and update -> additional drivers -> Nvidia-driver-470 and restart, then, the pc no longer detects neither wifi nor ethernet.
with the ifconfig command nothing is displayed, if I try the command "sudo systemctl status NetworkManager" it says active but reports these warnings:


```
<warn> ifupdown: the interfaces / etc / network / interfaces file does not exist
<warn> Error: Open / run / network / ifstate failed
```


EDIT:


output of "sudo lshw -C network" command:


```
  *-network UNCLAIMED
       description: Network controller
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fc400000-fc403fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fc200000-fc2fffff memory:fc300000-fc303fff


```


what's going on here ?

Ps. sorry for the lack of information, if you need a particular command output please ask

EDIT:
the problem here after long internet searches seems to be that when i updated the Nvidia driver it somehow deleted the network adapter drivers, how can i restore them without internet connection?

---

### Post by praseodym on 2022-07-11
Can you revert it when downgrading the NVIDIA driver?

---

