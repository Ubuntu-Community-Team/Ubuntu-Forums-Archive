---
title: "Ubuntu 12.04 LTS - No Wifi with Intel Wireless AC 3160"
date: 2021-01-20
forum: Networking &amp; Wireless
---

### Post by pmwill on 2021-01-20
Hello,
I'm brand new to linux - trying to setup Ubuntu 12.04 LTS to run research software with specific packages: [http://www.ncorr.com/](http://www.ncorr.com/)

I am trying to connect an offline computer (home build) to a wireless network via an Intel wireless AC 3160 card.
I was able to establish wifi connection, but doing System Settings>> Additional Drivers >> Update and reboot has since left me without the ability to connect.

I was trying to follow this thread, but I cannot connect via ethernet, so I wasn't able to finish all of the steps: [https://ubuntuforums.org/archive/index.php/t-2244058.html](https://ubuntuforums.org/archive/index.php/t-2244058.html)


Here are the outputs requested in that thread:

```

```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: 70:85:c2:28:69:d1
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:88 memory:fb400000-fb41ffff memory:fb435000-fb435fff ioport:f020(size=32)
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 70:85:c2:06:56:b9
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.0.5-k firmware=0. 4-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:fb300000-fb31ffff ioport:d000(size=32) memory:fb320000-fb323fff
  *-network
       description: Network controller
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:19 memory:fb200000-fb201fff


verispellis@verispellis-desktop:~$ lspci -nn | egrep '0200|0280':
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1] (rev 05)
05:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)




verispellis@verispellis-desktop:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no




verispellis@verispellis-desktop:~$ uname -mr
3.13.0-117-generic x86_64
verispellis@verispellis-desktop:~$ lsb_release -d
Description:    Ubuntu 12.04.5 LTS
```

```


Any help is appreciated!
Let me know if you need more info.

---

### Post by CelticWarrior on 2021-01-20
Welcome.

Ubuntu 12.04 reach EoL (End of Life) status in April 2017. 
Please do your backups and install a supported release. The current LTS - 5 years of support - is Ubuntu 20.04.

---

### Post by howefield on 2021-01-20
Thread closed.

You'd most likely be better off installing a supported version of Ubuntu. Few will care enough about an End of Life 12.04 to troubleshoot it..

---

