---
title: "installed a new kernel and now ubuntu 14.04 can't find wifi"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by chris_sabin on 2015-07-03
I downloaded a copy of the Linux kernel from this link [http://kernelnewbies.org/OutreachyfirstpatchSetup?action=show&redirect=OPWfirstpatchSetup](http://kernelnewbies.org/OutreachyfirstpatchSetup?action=show&redirect=OPWfirstpatchSetup) and after installation Ubuntu was unable to connect to the internet. WiFi networks are not listed and even the Ethernet cable(I think that's what its called) won't connect me to the internet. 

I'm running Ubuntu 14.04 on Acer aspire 5560.

After installing the kernel I got a message when I booted the computer that said "the disk drive for dev/mapper/cryptswap1is not ready yet or not present". I followed some vague mysterious instructions from somewhere to fix this and the new message "the disk drive for UUID=(very long number thing) is not ready or not present" and so I followed these instructions to fix the second problem [https://debmintux.wordpress.com/2013/03/24/the-disk-drive-for-uuid-is-not-ready-yet-or-not-present-continue-to-wait-or-press-s-to-skip/](https://debmintux.wordpress.com/2013/03/24/the-disk-drive-for-uuid-is-not-ready-yet-or-not-present-continue-to-wait-or-press-s-to-skip/). 

I am not sure if either of these messages were related to the WiFi problem

I think the following might be useful but I'm not sure

chris@chris-Aspire-5560:~$ sudo lshw -C network 
[sudo] password for chris: 
  *-network                
       description: Ethernet interface 
       product: NetLink BCM57785 Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 10 
       serial: 20:6a:8a:4c:fa:32 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:16 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:f0300000-f03007ff 
  *-network 
       description: Network controller 
       product: BCM43227 802.11b/g/n 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=bcma-pci-bridge latency=0 
       resources: irq:18 memory:f0100000-f0103fff

---

### Post by Pilot6 on 2015-07-04
You can run

sudo apt-get install bcmwl-kernel-source

to install the driver.

If it does not work, there is an alternative one

sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer

---

### Post by chris_sabin on 2015-07-04
Thank you for your response, After running the first one the last line of text it gave me was 'possible missing firmware /lib/firmware/radeon/TAHITI_vce.bin for module Radeon. I was not able to connect to the WiFi after this. 

I ran the second two commands and then I noticed that when I click the internet connections icon on the desktop it now gives me an option for connection information which wasn't there before but there still weren't any options to connect to the internet.

---

### Post by chris_sabin on 2015-07-04
Never mind the second one did work my WiFi is working again, thank you so much! Am I supposed to edit the title of this forum with the word "solved"?

---

