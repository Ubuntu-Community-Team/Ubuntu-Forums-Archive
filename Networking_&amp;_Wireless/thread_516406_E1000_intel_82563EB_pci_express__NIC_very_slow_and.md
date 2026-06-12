---
title: "E1000 intel 82563EB pci express  NIC very slow and unstable"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by scramatte on 2007-08-03
Hello,

We have just installed 2 same supermicro servers 

- Processor XEON Core Duo 2
- Motherboard X7DBE+
- Raid controller 3WARE 9650SE pci express
- 4 Gb of RAM DDR2 667 ECC
- 8 x 500Gb x 7200rpm Seagate Hard Drives  (RAID 5 array)
- 2 NICs intel 82563EB pci express E1000
- Linux Ubuntu Feisty 7.04 + Kernel 2.6.20

- Switch Gigabit LinkSys SRW2016 Manageable
- 5E certified wire

We use this server to store MPEG-2 videos  (files + or - > 2Gb)
When we try to transfer data from/to a windows client  using samba, ftp, scp or any other protocol ...
The network controller give us very poor performance and jump from 0 to 20Mbits without stop ...

Seems that the network controller can't find is cruse speed ... but doesn't seems to be negotiation problem
because doesn't loose packets ... It's just extremely slow and bandwidth unstable ! I've try with 2.6.22.1 kernel and
I've got the same problem.

I've got here 2 others servers with another kind of motherboard (asus, msi) and 
In the same condition (config,distribution, same raid controller, hard drives, ...)  I've obtain throughtput of 600Mbits ... 


I can't see any errors when I do an ifconfig
No collisions, No TX/RX errors

The e1000 driver detect the controller without problem. 
I don't have any error message on bootup  ( "dmesg" ).

I've flashed the supermicro's servers with the latest bios

Any tips or ideas ?



Regards

---

### Post by noob12 on 2007-08-03
Can you post the output of ```
sudo lshw -C network
``` and ```
sudo ethtool eth0
```, replacing the interface name by the actual one if it is not eth0.
Also
```
ifconfig -a
```

---

