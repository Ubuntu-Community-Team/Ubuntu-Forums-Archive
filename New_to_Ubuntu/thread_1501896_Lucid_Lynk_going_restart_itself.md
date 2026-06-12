---
title: "Lucid Lynk going restart itself"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by JenakaRia on 2010-06-04
Hello Anybody,

Could you helpme, I am just try to install ubuntu 10.04, but some time our lucid going reboot itself, sometime i browsing to speedtest.net and try to test bandwidht but befor finish our lucid going reboot itself, why? Whats wrong? What can I do?


This is lspci


$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

many Thanks for your help

---

### Post by cariboo on 2010-06-04
Are you using a laptop? If so check cpu temps by opening a terminal and typing:

```
sensors
```

The above command will display your cpu temps.

---

### Post by teward on 2010-06-04
Thermal events (overheats) will trigger a shutdown and/or restart in the BIOS to protect the components.  Check the temperature sensors just to make sure :)

---

### Post by JenakaRia on 2010-06-05
Thank you,

Problem couse is FAN in our PC not running.

NOW is solve.

---

