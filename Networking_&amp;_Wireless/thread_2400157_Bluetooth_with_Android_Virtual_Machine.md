---
title: "Bluetooth with Android Virtual Machine"
date: 2018-09-03
forum: Networking &amp; Wireless
---

### Post by GirishSharma on 2018-09-03
I have below setup and devices :


One android phone. Computer with wifi receiver.
Host OS is Ubuntu 18.04 LTS.
I enables hotspot in my android phone and connects to the internet.
Oracle Virtual box which have Windows 10 virtual machines.
My PC don't have bluetooth on mother board because when I says :
```

girish@gk:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 13ba:0018 PCPlay Barcode PCP-BCG4209
Bus 003 Device 002: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
girish@gk:~$ 

```
So, there is no bluetooth device with Host machine. 
How can I access bluetooth in windows 10 (Virtual Machine) with above hardwars and setup/environment.
Can I use my phone's bluetooth to work as send and receive file from Whatsapp to/from phone vs windows 10 or I have to buy
a bluetooth dongle for VMs?

---

