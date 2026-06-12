---
title: "Broadcom BCM4313"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by violetalisboa on 2013-12-12
Some info.

madalena@Mada:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 07)
madalena@Mada:~$ sudo modprobe -r hp-wmi
[sudo] password for madalena: 
madalena@Mada:~$ sudo rfkill unblock all
madalena@Mada:~$ cigano2013
cigano2013: command not found
madalena@Mada:~$ sudo modprobe -r hp-wmi
madalena@Mada:~$ sudo rfkill unblock all
madalena@Mada:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
madalena@Mada:~$ sudo modprobe -r wl
FATAL: Module wl not found.
madalena@Mada:~$ sudo modprobe brcmsmac
madalena@Mada:~$ sudo rfkill unblock all
madalena@Mada:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
madalena@Mada:~$ sudo modprobe -r wl
FATAL: Module wl not found.
madalena@Mada:~$ sudo modprobe brcmsmac
madalena@Mada:~$ sudo rfkill unblock all
madalena@Mada:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2013-12-12
And your question is what?? What is your wireless doing or not doing? Which version of Ubuntu are you running?```
lsb_release -d
```

---

