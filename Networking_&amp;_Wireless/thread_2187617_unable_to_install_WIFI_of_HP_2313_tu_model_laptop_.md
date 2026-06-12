---
title: "unable to install WIFI of HP 2313 tu model laptop in ubuntu 12.04 32 bit"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by himadric91 on 2013-11-13
Hi,

i installed ubuntu 12.04 in my hp 2313 tu model laptop but its unable to install WIFI driver. so WIFI is not working in ubuntu 12.04.

please suggest.

thanks 

Himadri

---

### Post by Bucky Ball on 2013-11-13
Welcome.

Please open a terminal and post the output of these two commands:
```

sudo lshw -C network
iwconfig
```

Also, can you get online with an ethernet cable? That will make things a lot easier if so.

When online, do an update and then check Additional Drivers. Anything in there relating to wireless drivers?

---

### Post by himadric91 on 2013-11-13
Hi,

I checked two commands output is "no wireless extension"

Ethernet interface is  RTL8101E/RTL8102E PCI fast Ethernet controller.

need help.

Thanks,

Himadri

---

### Post by himadric91 on 2013-11-13
Hi,
i am online with Ethernet and checked with additional drivers option also. it shows no additional drivers are there and i already system update also.

---

### Post by Bucky Ball on 2013-11-13
```

sudo lshw -C network
iwconfig
```

Post the FULL output of these two commands when online with a cable, thanks.

---

### Post by himadric91 on 2013-11-13
Hi,

Please find the above two command output details in below:

1> Command: sudo lshw -C network
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 88:51:fb:cc:6d:af
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.33 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:c2404000-c2404fff memory:c2400000-c2403fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2510000-c251ffff

2> Command:iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.

---

### Post by Bucky Ball on 2013-11-13
Your card appears to be an RT3290 which are known to be problematic in 12.04/12.10 but work 'out of the box' with 13.04 and up.

You can try compiling the driver yourself which does work for some by following the official site guide down the page here:

[http://www.ubuntuask.com/q/answers-how-do-i-get-a-ralink-rt3290-wireless-card-working-253632.html](http://www.ubuntuask.com/q/answers-how-do-i-get-a-ralink-rt3290-wireless-card-working-253632.html)

Or you can install the 3.9 kernel and it should work when you boot into it by following the guide here:

[http://linuxg.net/how-to-install-3-9-kernel-on-ubuntu-13-04-12-10-12-04-and-linux-mint-15-14-13/](http://linuxg.net/how-to-install-3-9-kernel-on-ubuntu-13-04-12-10-12-04-and-linux-mint-15-14-13/)

Just copy/paste the instructions for either 32bit system or 64bit. You MUST be online for this to work.

 When done, reboot and when the menu screen comes up you should see the 3.9 kernel there. Choose that and log in.

---

### Post by himadric91 on 2013-11-14
Hi,

Solved.. 

Thank U
Himadri

---

### Post by Bucky Ball on 2013-11-14
Please share with the community how you solved the issue (always do this please) and mark the thread as solved by following the link in my signature. Thanks. ;)

---

