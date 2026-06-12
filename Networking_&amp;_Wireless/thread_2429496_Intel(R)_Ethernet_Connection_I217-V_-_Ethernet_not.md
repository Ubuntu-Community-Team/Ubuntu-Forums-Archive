---
title: "Intel(R) Ethernet Connection I217-V - Ethernet not recognized - Ubuntu 18.04 LTS"
date: 2019-10-18
forum: Networking &amp; Wireless
---

### Post by andidandi on 2019-10-18
Dear all, 

I would like to abandon Windows for good and switch to linux once for all.

I am a total new comer to linux. 

I have tried to install ubuntu 18.04 LTS a few months ago but, once the installation was complete, there were issues with the network card: I could not connect to my LAN. Since the computer is quite old I was pretty sure that the hardware should have been recognised easily, but apparently this was not the case. 

My hardware is the following one: 

```
Summary
        Operating System
            Windows 10 Pro 64-bit
        CPU
            Intel Core i5 4670 @ 3.40GHz    55 °C
            Haswell 22nm Technology
        RAM
            16,0GB Dual-Channel DDR3 @ 644MHz (9-9-9-24)
        Motherboard
            ASUSTeK COMPUTER INC. GRYPHON Z87 (SOCKET 1150)    34 °C
        Graphics
            Standard Monitor (1440x900@32Hz)
            2047MB NVIDIA GeForce RTX 2060 (Gigabyte)    68 °C
        Storage
            238GB Samsung SSD 840 PRO Series (SATA (SSD))    26 °C
            931GB Western Digital WDC WD10EFRX-68PJCN0 (SATA )    27 °C
        Optical Drives
            No optical disk drives detected
        Audio
            Realtek High Definition Audio
```

Here below please find some details about the networking hardware:

```
Adapters List
                Enabled
                        Broadcom 802.11ac Network Adapter
                         
                        Intel(R) Ethernet Connection I217-V
```

At the time, when I first tried to install ubuntu, I was stuck as I did not have any idea on how to install the correct driver for the [I217-V controller]("https://ark.intel.com/content/www/us/en/ark/products/70831/intel-ethernet-connection-i217-v.html"). I also have a wireless card an [Asus PCE-A56]("https://www.asus.com/us/Networking/PCEAC56/specifications/") (PCI-Ex1, 866mbit/s, 320 mbit/s) which uses a broadcom chip. From a [quick search on the internet]("https://wikidevi.com/wiki/ASUS_PCE-AC56") it appears that even this broadcom chip is not supported out of the box by ubuntu. 

This is why I am now asking for help to install at least the ethernet controller driver. My idea is to download the drivers while windows is still on, transfer them to an usb stick and only then, install ubuntu. Once ubuntu is installed I should copy over the driver and proceed with the installation of the correct driver.

The first thing I looked for is the driver: [link.]("https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCIe-Intel-Gigabit-Ethernet-Network-Connections-Under-Linux-?product=70831") Hopefully it is the correct one. 

Is there anyone which could kindly illustrate me on how to proceed with the "manual" installation of the driver?  

Thanks a lot. 

andi

---

### Post by chili555 on 2019-10-18
The driver *e1000e* is already present in recent Ubuntu versions including 18.04. 

Can you try a live session of Ubuntu and tell us what this terminal command has to report?```
dmesg | grep e100
```

---

### Post by andidandi on 2019-10-19
@chili555, hello and thank you for your quick answer. 

Please have a look:

```

ubuntu@ubuntu:~$ dmesg|grep e100
[    5.347631] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    5.347632] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    5.348979] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    5.426875] e1000e 0000:00:19.0 0000:00:19.0 (uninitialized): registered PHC clock
[    5.495230] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) e0:3f:49:7e:41:ab
[    5.495231] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    5.495271] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    5.495751] e1000e 0000:00:19.0 eno1: renamed from eth0
ubuntu@ubuntu:~$ 
```

Thanks!

---

### Post by webaake on 2019-10-19
e1000e 0000:00:19.0 eno1

There's your network card name: **eno1** and it all seems ok driverwise. You just need to configure it. Look into your "Settings" menu or "System" menu for Network manager (or the like, I don't know your flavour of Ubuntu). From there it should be easy to configure the IPV4 network settings.

As a side note: on Linux almost no driver installation is ever needed. In most cases the drivers are already in the Kernel.

---

### Post by chili555 on 2019-10-19
> **webaake said:**
> e1000e 0000:00:19.0 eno1

There's your network card name: **eno1** and it all seems ok driverwise. You just need to configure it. Look into your "Settings" menu or "System" menu for Network manager (or the like, I don't know your flavour of Ubuntu). From there it should be easy to configure the IPV4 network settings.

As a side note: on Linux almost no driver installation is ever needed. In most cases the drivers are already in the Kernel.I agree entirely. 

With a known good ethernet cable, Network Manager ought to connect automagically. If not, check:```
dmesg | grep eno1
```

---

