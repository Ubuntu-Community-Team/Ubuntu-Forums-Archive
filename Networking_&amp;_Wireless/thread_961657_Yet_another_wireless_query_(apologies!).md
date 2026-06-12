---
title: "Yet another wireless query (apologies!)"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by kenny99 on 2008-10-28
Sorry guys, I know there are a million posts out there already on this subject but i've followed them as far as i can, but being a newbie to Linux i am not sure where to go from here other than ask for help from the forums!

I have a Fujitsu Siemens Amilo 2735 with Intel® PRO/Wireless 3945ABG integrated Wireless LAN. I installed Ubuntu Hardy Heron and wiped Vista (intentionally). I am on a wired connection at the moment as the Network Manager does not seem to be registering the wireless driver. 

I installed ndiswrapper and followed a list of commands which i've come across on other posts. 

If anyone can help, that would be great. I'm hoping the following output might help someone to see where i'm going wrong.

```

nicky@nicky-laptop:~$ dmesg | grep wlan
nicky@nicky-laptop:~$ dmesg | grep Wireless
[   29.426513] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   29.426657] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
nicky@nicky-laptop:~$ dmesg | grep 3945
[   29.426513] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   29.426516] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.426657] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   30.277809] iwl3945: Radio Frequency Kill Switch is On:
[   30.282059] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.292086] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.312033] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.339324] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.359256] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
nicky@nicky-laptop:~$ dmesg | grep eth
[   18.238001] eth0: RTL8101e at 0xf887a000, 00:1f:16:00:85:ac, XID 34200000 IRQ 220
[   19.146816] Driver 'sd' needs updating - please use bus_type methods
[   19.148962] Driver 'sr' needs updating - please use bus_type methods
[   33.919597] r8169: eth0: link down
[   41.501059] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.207562] r8169: eth0: link up
[   56.211224] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   58.648963] eth0: no IPv6 routers present
nicky@nicky-laptop:~$ dmesg | grep ndis
nicky@nicky-laptop:~$ dmesg | grep ndis
nicky@nicky-laptop:~$ 
nicky@nicky-laptop:~$ dmesg | grep wl
[   29.426513] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   29.426516] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.426657] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   30.277809] iwl3945: Radio Frequency Kill Switch is On:
[   30.282059] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.292086] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.312033] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.339324] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.359256] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
nicky@nicky-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:16:00:85:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.2 latency=0 module=r8169 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945


```

---

### Post by kenny99 on 2008-11-01
I've also checked BIOS and wireless is enabled. Anyone have any ideas?

---

### Post by kenny99 on 2008-11-06
Still struggling to find a solution, so trying one final bump...

---

