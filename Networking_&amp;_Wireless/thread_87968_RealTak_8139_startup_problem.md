---
title: "RealTak 8139 startup problem"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by Era_Russland on 2005-11-09
Hello
I have linux pc with realtek intergrated network card. I have install ubuntu 5.1 on this box and when system start up I have not network.
--lspci--
000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
--dmesmg|grep 8139--
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
8139cp: pci dev 0000:02:0d.0 (id 10ec:8139 rev 10) is not an 8139C+  chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
eth0: RealTek RTL8139 at 0xb800, 00:0c:6e:f0:80:52, IRQ 17
eth0:  Identified 8139 chip type 'RTL-8101'
8139too Fast Ethernet driver 0.9.27
eth0: RealTek RTL8139 at 0xb800, 00:0c:6e:f0:80:52, IRQ 17
eth0:  Identified 8139 chip type 'RTL-8101'
---lsmod--after ifup eth0---
8139too                25504  0
mii                     5696  1 8139too
---

After login I type --ifup eth0-- and my network is working fine. What should I do to have my network work at startup? 
thx
As I understood I have some missunderstood with order of loading kernel modules.

---

### Post by mips on 2005-11-10
Have you come right ?

Go to System->Administration->Networking

Does the card appear there ? If it does click on Activate.

---

### Post by jahLux on 2005-11-11
[QUOTE=Era_Russland]Hello
I have linux pc with realtek intergrated network card. I have install ubuntu 5.1 on this box and when system start up I have not network.
--lspci--
000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
--dmesmg|grep 8139--
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
8139cp: pci dev 0000:02:0d.0 (id 10ec:8139 rev 10) is not an 8139C+  chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
eth0: RealTek RTL8139 at 0xb800, 00:0c:6e:f0:80:52, IRQ 17
eth0:  Identified 8139 chip type 'RTL-8101'
8139too Fast Ethernet driver 0.9.27
eth0: RealTek RTL8139 at 0xb800, 00:0c:6e:f0:80:52, IRQ 17
eth0:  Identified 8139 chip type 'RTL-8101'
---lsmod--after ifup eth0---
8139too                25504  0
mii                     5696  1 8139too
---

After login I type --ifup eth0-- and my network is working fine. What should I do to have my network work at startup? 
thx
As I understood I have some missunderstood with order of loading kernel modules.[/QUOTE]

May I suggest you start over, reinstall. This time, at the FIRST boot prompt when the installation is about to begin - type 'linux acpi=off' (without the quote marks), hit enter.
Your installation will proceed smoothly and normally, your integrated network card will be configured under DHCP (without any intervention on your part) and you'll join the happy group of Ubuntu 5.10 users.

---

