---
title: "[SOLVED] Ethernet problem with Attansic L2 100 Mbit Ethernet"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by manadi on 2008-09-23
I cannot connect to the internet. Although the driver is not in the main kernel yet, I got it as external module and insmoded it.

Few details are as follows:

anadi@anadi-desktop:~/Desktop/atl2-2.0.5$ ifconfig
eth0      Link encap:Ethernet  HWaddr 11:11:11:11:11:11(changed)
          inet addr:158.144.65.86  
	  Bcast:158.144.65.127  
	  Mask:255.255.255.128

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:11310226 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:459 errors:0 dropped:0 overruns:0 carrier:2
         collisions:0 txqueuelen:1000 
         RX bytes:1259846239 (1.1 GB)  TX bytes:0 (0.0 B)

         Memory:dbfc0000-dc000000 

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3462 (3.3 KB)
          TX bytes:3462 (3.3 KB)

anadi@anadi-desktop:~/Desktop/atl2-2.0.5$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
	description: Ethernet interface
        product: L2 100 Mbit Ethernet Adapter
        vendor: Attansic Technology Corp.
        physical id: 0
       bus info: pci@0000:02:00.0
        logical name: eth0
       version: a0
        serial: 11:11:11:11:11:11(changed)
        width: 64 bits
       clock: 33MHz
        capabilities: bus_master cap_list ethernet physical
        configuration: broadcast=yes driver=atl2 driverversion=2.0.5 firmware=L2 ip=158.144.65.86 latency=0 module=atl2 multicast=yes

dmesg:  [  287.067362] ACPI: PCI interrupt for device 0000:02:00.0 disabled
	[  305.634460] Atheros(R) L2 Ethernet Driver - version 2.0.5
	[  305.634466] Copyright (c) 2007 Atheros Corporation.
	[  305.634564] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
	[  305.634577] PCI: Setting latency timer of device 0000:02:00.0 to 64
	**[  307.235504] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>**

Any pointers to the cause will be gr8. Thanks.

---

### Post by manadi on 2008-09-23
now this is disappointing..........heard so much about ubuntu community support and no one is curious about my 3rd(all unanswered) question......pleeeeeeeeeeeeeeeeeeeeeeeeeeezzzzzz  help.

---

### Post by manadi on 2008-09-23
At last got a workaround after losing sleep for two days.

Never heard of anything like this before:

As the linux kernel does not have a driver for this particular card, I am using atl2 driver developed by Chris Snook which is still new. But strangely that is not the problem here. Dan says its the firmware that is the pain.I have dual boot XP/ubuntu. Take a look.

[http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04541.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04541.html)

anyways sorry for my above post.....I was really frustated.

---

