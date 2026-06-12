---
title: "Lenovo Wireless"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by Botai on 2010-09-11
I just installed Ubuntu 10.04 LTS on my Lenovo Ideapad Z460 (No previous OS installed). I got very confused with my wireless settings. Somehow I cant connect to wireless networks since I cant even detect them. Do i have to install some driver for this?

Ps. this is my first time using linux so i'm not quite familiar with the UI yet
I have included some information from several tests i did:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

_-$ LSUSB:_
botai@botai-laptop:~$ lsusb
Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 003: ID 04f2:b18a Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

_-$ LSPCI_
botai@botai-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a70 (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

_IWLIST SCAN_
botai@botai-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by Jeanke on 2010-09-11
Connect over cable and then go to System -> Administration -> Hardware drivers. Check if there is a driver available for your wifi card and install it. After reboot PC and try to connect again.

---

### Post by Botai on 2010-09-11
lol i currently don't have a cable at hand, but i do have another computer (win7) that is connected to the internet. Is there a way to download the driver and install it on my ubuntu using usb?

---

### Post by Jeanke on 2010-09-11
This should be possible yes, but it will involve more complicated actions. Chances that things do not go exactly as expected will increase...
If possible I still would suggest to find a cable somewhere.

---

### Post by Jeanke on 2010-09-11
This might also be interesting:

[http://ubuntuforums.org/showthread.php?t=1424280]("http://ubuntuforums.org/showthread.php?t=1424280")

---

### Post by Botai on 2010-09-11
Ok i'll do as you say. thnx for the advice :p

---

