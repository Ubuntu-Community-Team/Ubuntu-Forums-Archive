---
title: "Dapper Drake will not recognise ethernet adapter"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by silversurfer on 2006-07-18
Hi

I am a newbie and this is my first posting so please bear with me.

I have dual boot up with Dapper Drake and Windows ME (yeah I know!). Dapper was installed about 3 weeks ago, ever since then 
I have been trying to get on the internet with Dapper. 

I took the advice from several people posting on these forums, to get a router and connect to an ethernet card, of which I did.

I bought a Netgear DG384UK router. I also had to buy an ethernet adapter, it is generic but it shows up in windows as "IC Plus IP100 10/100 Fast Ethernet Adapter".

I've managed to get everything working with ME but, alas not with Dapper Drake.

In Dapper's Network Settings -> Connections, is: 
                        Modem connection
               The interface ppp0 is not configured

According to Help it should read: 
                     Ethernet LAN card eth0
                     Wireless LAN card eth1

I've tried various commands and this is what I got.

$ sudo ifconfig eth0
eth0: error fetching interface information: Device not found.

$ lspci | grep Eth
0000:00:09.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 (rev31)

(Is Dapper reading the "IC Plus IP 100 10/100 Fast Ethernet Adapter" in Windows, as "Sundance Technology Inc"? Or is this something different?)

$ sudo gedit /etc/network/interfaces

auto lo
iface to inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

$ sudo gedit /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

$ sudo gedit /etc/iftab5
(The window is blank.)

My computer has an AMD Duron 800MHz processor, 640MB memory and 30GHz hard drive.

If somebody can help me. I would be very grateful.

silversurfer

---

### Post by cracker on 2006-07-22
I have this same problem. There is no driver loaded for the ethernet adapter. Mine is onboard ethernet on an Abit NF7-S2. I'm currently looking for a driver, but may have to fall back on ndiswrapper.

---

### Post by cracker on 2006-07-22
Update:

After an hour of googling, I found nothing. I decided to install Nvidia.com's nforce 1/2 chipset driver their way. After getting all the necessary packages installed (binutils, gcc, kernel sources, headers, etc) it succeeded. However, I still can't get the networking to work. There is no eth0. I've tried modprobe nvnet, tried adding it to /etc/modules and rebooting, but still no ethernet. I need help!

---

### Post by cracker on 2006-07-22
Well, I gave up on it. I installed an [Encore ENLGA-1320 Gigabit PCI NIC](http://www.newegg.com/Product/Product.asp?Item=N82E16833180026) and it worked immediately.

---

### Post by Sef on 2006-07-22
> Well, I gave up on it. I installed an Encore ENLGA-1320 Gigabit PCI NIC and it worked immediately.

Sometimes that is the best thing to do.  Not every piece of hardware will work with GNU/Linux. (And not every piece will work with Microsoft software either.)

---

### Post by zwilrich on 2006-08-11
There is a driver at
[http://www.icplus.com.tw/driver-pp-IP100A.html](http://www.icplus.com.tw/driver-pp-IP100A.html)
I was able to get this driver to work with Gentoo Linux.  I haven't been able to figure out how to get it to work with Ubuntu yet.

---

### Post by Danieliozzi on 2006-09-17
for me the Solution was to compile the Encore Drivers for the "ENL832-TX-ICNT" (sundance) after making 2 lines modification in the source.
It seems to be a problem with the kernel 2.6.15-26 and the module that comes with the distro.
To be able to do that u need to

1.Modify sundance_main.c
1.a = line 1400 "pci_dma_sync_single" --> "pci_dma_sync_single_for_cpu"
2.b = line 1653, comment the line
Original = strcpy(info.bus_info, np->pci_dev->slot_name);
Correct = /* strcpy(info.bus_info, np->pci_dev->slot_name); */

3.To compile succesfully u need to intstall the packages from your Ubuntu CD from K/X/ubuntu 6.06.1 i386\pool\main" only if u dont have internet conection other way u can do it online with the package manager tool.

4.copy the sundance.ko module that u make to lib/modules/2.6.15-26-386/kernel/drivers/net "Yes overwrite it".

5.Uninstall the module first ."rmmod sundance"

6.Install the module ."insmod sundance" or maybe "insmod lib/modules/2.6.15-26-386/kernel/drivers/net/sundance.ko"

7.and finnaly bring up the card with "ifconfig eth0 192.168.0.1" or whatever your ethx or ip addres is, or maybe u can use the xwindows system confriguration tool that u have or u like .

I have to say that the main clue for the solution comes from "http://bazar2.conectiva.com.br/pipermail/linux-br/2006-June/040211.html"
but is in brazilian portuguese.

---

