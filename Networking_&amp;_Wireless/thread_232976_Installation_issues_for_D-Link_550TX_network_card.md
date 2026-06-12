---
title: "Installation issues for D-Link 550TX network card"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by CalcMaster86 on 2006-08-09
Hi everyone,

I've been a long time linux user for school, but this is my first time doing an install on a machine. I recently acquired an 800 Mhz P3 machine, which I initially installed Fedora 5 on--since I was having issues with it, I switched to Ubuntu.

Both Fedora and Ubuntu do not recognize my network adapter, which is a D-Link DFE 550TX PCI network card. D-Link says that it is fully functional with Red Hat Enterprise (I think 7), and it should be "easy" to install on other linux variants.

I've searched these forums for about an hour... and tried doing a sudo modprobe sundance... (which I found in another post) which didn't do anything (I'm certain that the network adapter uses the sundance drivers).

I've also tried following the instructions with the drivers D-Link provided... however, I get errors, saying that there are dependent files not found in the default directory--some of these files are on my computer, but in different directories. There are multiple files with these names (but they appear to be different), and then there are files that aren't on my computer at all.

The D-Link Linux driver can be found at [http://support.dlink.com/products/view.asp?productid=DFE%2D550TX#](http://support.dlink.com/products/view.asp?productid=DFE%2D550TX#) (click the linux checkmark). I'd be very appreciative of any help you guys can give me.

---

### Post by Danieliozzi on 2006-09-17
for me Solution was to compile the Encore Drivers for the "ENL832-TX-ICNT" after making 2 lines modification in the source.
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

### Post by Dramian on 2008-01-03
I'm a Fedora user and I'm trying to set up an Ubuntu distro for a friend. He is having the same problem (or, rather, I am). I tried to follow the instructions given above but the 'make' command still gives a massive string of errors. I don't suppose there is a nice, neat .deb package of this driver? :)

btw: Ubuntu seems to be a nice distro (6.06 being used here) but why isn't there a dvd of it with all the useful stuff already on it?

---

