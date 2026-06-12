---
title: "UBUNTU 12.0.4 LTS freezes on wireless occassionaly"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by venkatesh20 on 2015-04-26
[COLOR=#111111][FONT=Ubuntu]This happens only when I connect to wifi, the system freezes and would not respond at all (ctrl+alt+f7 also does not work). Restarting the system is the only option. But the annoying thing is even if I restart, sometimes it freezes again with in minutes. Please help me to get this resolved
Here are my system details

> venki@venki-HP-248-G1-Notebook-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:   precise

kernel info
> venki@venki-HP-248-G1-Notebook-PC:~$ uname -a
Linux venki-HP-248-G1-Notebook-PC 3.13.0-49-generic #81~precise1-Ubuntu SMP Wed Mar 25 16:32:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Wireless info
> venki@venki-HP-248-G1-Notebook-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5227 (rev 01)


[/FONT][/COLOR]
cross posted in askubutu: [http://askubuntu.com/questions/613489/ubuntu-12-0-4-lts-freezes-on-wireless-occassionaly](http://askubuntu.com/questions/613489/ubuntu-12-0-4-lts-freezes-on-wireless-occassionaly)

---

### Post by jeremy31 on 2015-04-26
What driver version do you have ```
dpkg -l | grep bcmwl
```

---

### Post by venkatesh20 on 2015-04-26
Here is the driver details
> venki@venki-HP-248-G1-Notebook-PC:~$ dpkg -l | grep bcmwl
ii  bcmwl-kernel-source                         6.20.155.1+bdcom-0ubuntu0.0.2                       Broadcom 802.11 Linux STA wireless driver source


---

### Post by jeremy31 on 2015-04-26
I wonder if [http://packages.ubuntu.com/trusty-updates/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/trusty-updates/amd64/bcmwl-kernel-source/download) might work better with the 3.13 kernel

---

### Post by venkatesh20 on 2015-04-26
unable to install it due to failed dependencies

---

