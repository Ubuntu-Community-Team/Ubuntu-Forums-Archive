---
title: "wireless help"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by mainframe1987 on 2010-08-23
hello
 
i am new to unbuntu and i am running 10.4 and its not recognizing my wireless aany suggestions.my machine is a acer aspire 5517 dual boot with windows 7

---

### Post by gandaran on 2010-08-23
> **mainframe1987 said:**
> hello
 
i am new to unbuntu and i am running 10.4 and its not recognizing my wireless aany suggestions.my machine is a acer aspire 5517 dual boot with windows 7
probably you need to install the wireless card drivers, if you can connect to internet using Ethernet cable run the software update command in terminal then check in system » administration » hardware drivers
```
sudo apt-get update
``` 
if there is a driver available there install it.

if you cant connect to internet then post the result of this command so we can check what brand of wireless card and help you install one.
```
lspci
```

---

### Post by _0R10N on 2010-08-23
> **gandaran said:**
> probably you need to install the wireless card drivers, if you can connect to internet using Ethernet cable run the software update command in terminal then check in system » administration » hardware drivers
```
sudo apt-get update
```if there is a driver available there install it.

if you cant connect to internet then post the result of this command so we can check what brand of wireless card and help you install one.
```
lspci
```

Additionally, you may take a look in the Drivers Manager window and check whether Ubuntu has already detected an appropriate driver for your wireless card, and is waiting for you to activate it.

---

### Post by mainframe1987 on 2010-08-23
> **_0R10N said:**
> Additionally, you may take a look in the Drivers Manager window and check whether Ubuntu has already detected an appropriate driver for your wireless card, and is waiting for you to activate it.sence i can not connect to the net i will post the results of the lspci 
 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
 
further more the status says disconnected.
 
thanks for your time

---

### Post by gandaran on 2010-08-24
> 02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
you need to install the Broadcom driver, google "Broadcom Corporation BCM4312 802.11b/g", you will find a lot of information on how to install the driver.

---

### Post by lkraemer on 2010-08-24
Try:

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom)

Posting #1 or Posting #6.  Either should work fine.

here is another link:
[http://ubuntuforums.org/showthread.php?t=1559749](http://ubuntuforums.org/showthread.php?t=1559749)

lk

---

