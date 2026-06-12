---
title: "ubuntu 20.04 latest cannot find my wifi network"
date: 2020-11-06
forum: Networking &amp; Wireless
---

### Post by pyramation on 2020-11-06
I just bought a new machine and put the latest Ubuntu on there, and cannot see my WiFi. `nmcli` showed only localhost and ethernet... no WiFi at all.


I've searched high and low, and at least have found the commands that I can run to hopefully help you help me ;)


Looks like it's getting error code `-110` on  `iwlwifi`, and the commands I ran show that the network is `UNCLAIMED`, not sure if that's a clue. 


I downloaded the AX200 driver from [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html) and `cp`'d the file into `/lib/firmware`, and followed [https://askubuntu.com/questions/990363/how-to-load-iwlwifi-driver](https://askubuntu.com/questions/990363/how-to-load-iwlwifi-driver). I'm not sure if there is supposed to be a confirmation if you build this correctly?

Another attempt: I reinstalled Ubuntu with "Install 3rd party software for graphics and wifi hardware" checkbox... still no dice.


Any help greatly appreciated!


Here is the `dmesg` to give us some clues:


```
username@myhostname:~$ sudo dmesg | grep wifi
[    4.935758] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    5.015538] iwlwifi: probe of 0000:06:00.0 failed with error -110
 
```
 
Here is the `lspci` info to get the hardware info:


```
username@myhostname:~$ lspci -knn | grep Net -A3; rfkill list
06:00.0 Network controller [0280]: Intel Corporation Wi-Fi 6 AX200 [8086:2723] (rev 1a)
    Subsystem: Intel Corporation Wi-Fi 6 AX200 [8086:0084]
    Kernel modules: iwlwifi
07:00.0 Ethernet controller [0200]: Intel Corporation Intel(R) Ethernet Controller I225-V [8086:15f3] (rev 02)
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```


Here is the `uname` info:


```
username@myhostname:~$ uname -a
Linux myhostname 5.4.0-42-generic #46-Ubuntu SMP Wed Oct 21 22:29:16 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
 ```
 
This shows the `UNCLAIMED` network for the WiFi:


```
username@myhostname:~$ sudo lshw -C network
  *-network UNCLAIMED       
       description: Network controller
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fc400000-fc403fff
  *-network
       description: Ethernet interface
       product: Intel(R) Ethernet Controller I225-V
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 02
       serial: 24:4b:fe:56:e0:c7
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=0.0.1-k duplex=full ip=192.168.1.228 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:38 memory:fc200000-fc2fffff memory:fc300000-fc303fff
```

---

### Post by kc1di on 2020-11-08
What does the command ```
rfkill list
``` show?

---

### Post by pyramation on 2020-11-08
Thanks for the response!

[COLOR=#000000]0: hci0: Bluetooth[/COLOR]
[COLOR=#000000]Soft blocked: no[/COLOR]
[COLOR=#000000]Hard blocked: no[/COLOR]

---

### Post by kc1di on 2020-11-09
Make sure you have fast boot turned off in bios  also what is the output of ```
uname -r
```

---

### Post by pyramation on 2020-11-09
Thank you again for the help! Here is the uname info:

[COLOR=#000000]username@myhostname:~$ uname -a[/COLOR]
[COLOR=#000000]Linux myhostname 5.4.0-42-generic #46-Ubuntu SMP Wed Oct 21 22:29:16 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

---

### Post by praseodym on 2020-11-09
Driver is loaded?
```

sudo modprobe -v iwlwifi
dmesg | grep iwl
```

---

### Post by pyramation on 2020-11-13
> **praseodym said:**
> Driver is loaded?
```

sudo modprobe -v iwlwifi
dmesg | grep iwl
```

Currently it's empty. 

How to load the driver?

---

