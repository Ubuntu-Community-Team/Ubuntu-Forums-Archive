---
title: "Netgear AC1200 Dual Band Wi-Fi USB 3.0 Adapter"
date: 2015-02-12
forum: Networking &amp; Wireless
---

### Post by wetzel-dc on 2015-02-12
I have a Netgear*** AC1200 Dual Band Wi-Fi USB 3.0 Adapter - ***model A6210.  From searching I have found that it uses a*MediaTek chipset, MT7612U (0846:9053). *I have downloaded the drivers from Mediatek.  The downloaded file is: 7612U_DPO_LinuxSTA_3.0.0.1_20140718.tar.bz2.  The Ubuntu Windows Wireless Drivers application wants a .inf file which I cannot find or produce from the downloaded file.
I did install the wireless adaptor in a Windows computer from the supplied CD - that worked fine, but I still could not find a .inf file on that Windows machine.  I have run the Install programs from Mediateck and Netgear using Wine but nothing seemed to happen and I could not access the Wine C drive to look for an .inf file.  Any help would be appreciated.

---

### Post by Bucky Ball on 2015-02-13
*Thread moved to **Networking & Wireless**.*

Welcome. You may have more luck here. With the device plugged in, please open a terminal and issue this command:

```
sudo lshw -C network
```

Post the output back here between [code] tags (see the last link in my signature for how).

---

### Post by wetzel-dc on 2015-02-13
Failed to mention I'm running Ubuntu 14.10 (updates are current)
```

david@No2:~$ sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: f4:6d:04:90:ac:61
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:53 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff memory:bfa00000-bfa1ffff
david@No2:~$ 


```

---

### Post by chili555 on 2015-02-13
Bucky also wants to see:```
lsusb
```

---

### Post by wetzel-dc on 2015-02-13
```

david@No2:~$ sudo lsusb
[sudo] password for david: 
Bus 002 Device 005: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 007: ID 04a9:1765 Canon, Inc. 
Bus 002 Device 006: ID 04a9:173e Canon, Inc. MP560
Bus 002 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0846:9053 NetGear, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
david@No2:~$ 


```

---

### Post by chili555 on 2015-02-13
Bucky now hopes you will observe this: [https://wikidevi.com/wiki/Netgear_A6210](https://wikidevi.com/wiki/Netgear_A6210)> Probable Linux driver
unknownAnd this:[https://www.linuxquestions.org/questions/linux-newbie-8/trying-to-get-netgear-wireless-usb-adapter-to-work-4175531331/](https://www.linuxquestions.org/questions/linux-newbie-8/trying-to-get-netgear-wireless-usb-adapter-to-work-4175531331/)> But, yeah, am I hearing that I should try to return it?

---

### Post by wetzel-dc on 2015-02-13
I'm running an up-to-date Ubuntu 14.10 system.
I downloaded a Linux driver for a wireless adaptor from Mediatek for my wireless adaptor, a Netgear, model A6210.  The chipset is MT7612U.
The download is named: MT7612U_DP_LinuxSTA_3.0.0.1_20140718.tat.bz2
What are the steps to install the software and get this thing working?

---

### Post by chili555 on 2015-02-13
There are no steps that I know of. Ordinarily, you would:```
sudo apt-get install build-essential linux-headers-generic
```Then, on your desktop, you'd right-click the tar.bz2 and 'Extract Here.' Then, back to the terminal:```
cd ~/Desktop/DPO
make
```Then you'd see all of this; known in Chili's house as a train wreck:> /home/chili/7612/DPO/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_giwrate’:
/home/chili/7612/DPO/os/linux/../../sta/sta_cfg.c:7534:25: warning: unused variable ‘rate_count’ [-Wunused-variable]
     int rate_index = 0, rate_count = 0;
                         ^
/home/chili/7612/DPO/os/linux/../../sta/sta_cfg.c:7534:9: warning: unused variable ‘rate_index’ [-Wunused-variable]
     int rate_index = 0, rate_count = 0;
         ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/chili/7612/DPO/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/chili/7612/DPO/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1345: recipe for target '_module_/home/chili/7612/DPO/os/linux' failed
make[1]: *** [_module_/home/chili/7612/DPO/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-30-generic'
Makefile:390: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
Then you'd post a question here and ask what to do.  I suggest you either get a different device or email Mediatek and ask them why it doesn't compile.

---

### Post by Bucky Ball on 2015-02-13
*Threads merged*. 

Please do not duplicate post. Thanks.

---

### Post by wetzel-dc on 2015-02-13
Sent email to Mediatek.

---

### Post by wetzel-dc on 2015-02-24
Have not received a response form Mediatek.

Did get a response from Netgear about the problem and asking if I had the right chipset info:
   **Response from NETGEAR**
 Hi David, 

I have looked into your case and I apologize, but we are not in the position to disclose that since it is considered proprietary information. Moreover, our adapters only work with Windows and MAC OS and do not support Linux OS. 

I suggest that you return the device to the store for a replacement. 

Again, thank you for choosing NETGEAR.  


Returned it and bought a Linksys AC1200 model WUSB6300 which is now installed and running fine.

Close case.

---

### Post by Bucky Ball on 2015-02-24
Nice to hear you perservered and got it resolved. Please mark thread as solved. See the second link in my signature for how. ;)

---

### Post by rjsec4ever on 2015-02-27
> **wetzel-dc said:**
> Have not received a response form Mediatek.

Did get a response from Netgear about the problem and asking if I had the right chipset info:
   **Response from NETGEAR**
 Hi David, 

I have looked into your case and I apologize, but we are not in the position to disclose that since it is considered proprietary information. Moreover, our adapters only work with Windows and MAC OS and do not support Linux OS. 

I suggest that you return the device to the store for a replacement. 

Again, thank you for choosing NETGEAR.  


Returned it and bought a Linksys AC1200 model WUSB6300 which is now installed and running fine.

Close case.

Wetzel, do you happen to recommend the Linksys adapter? I am having the same issue you had.
I'm giving my Netgear to a different PC in the home that is Redmond-only.
I also have to buy two: one for my dual-boot Win8.1/Ubu14.10, another for a Kubu14.04 LAN server.

---

### Post by Nicolas_Frenay on 2015-12-07
Any chance a dev can look at this to implement the driver?

Apparently this device is using MediaTek's MT7612U chipset, which has sources online.

Thanks!

---

### Post by Bucky Ball on 2015-12-08
> **Nicolas_Frenay said:**
> Any chance a dev can look at this to implement the driver?

You are asking in the wrong place. We are all here voluntarily, staff included, and it is rare a dev or Canonical employee would ever visit here. :)

This is an old, solved thread so let's put it back to sleep.

*Thread closed.*

---

