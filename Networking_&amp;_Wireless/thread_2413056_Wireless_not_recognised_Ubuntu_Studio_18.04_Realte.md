---
title: "Wireless not recognised Ubuntu Studio 18.04 Realtek Wireless hardware"
date: 2019-02-20
forum: Networking &amp; Wireless
---

### Post by pabra708 on 2019-02-20
I installed Ubuntu Studio 18.04 on my HP  Laptop a couple months ago. The main problem that I have been having is that I can't connect to the wireless. I can however connect using an Ethernet cable. Since then I have been trying to fix the problem. I installed Larry W finger's driver and the system told me that it was successfully installed however the computer still does not recognize the existence of WiFi. It almost seems like there is some other setting on the computer that needs to changed but I don't know the first thing about what that might be. Does anyone have any recommendations?

---

### Post by praseodym on 2019-02-22
Please show the outputs of these commands:
```

lspci -nnk
lsusb
```

---

### Post by pabra708 on 2019-02-23
```
lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5904] (rev 08)
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [103c:832a]
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 620 [8086:5917] (rev 07)
    Subsystem: Hewlett-Packard Company UHD Graphics 620 [103c:832a]
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 08)
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [103c:832a]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:08.0 System peripheral [0880]: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model [8086:1911]
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model [103c:832a]
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP USB 3.0 xHCI Controller [103c:832a]
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP Thermal subsystem [103c:832a]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP CSME HECI [103c:832a]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP SATA Controller [AHCI mode] [103c:832a]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 [8086:9d15] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E [8086:9d4e] (rev 21)
    Subsystem: Hewlett-Packard Company Device [103c:832a]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP PMC [103c:832a]
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d71] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP HD Audio [103c:832a]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP SMBus [103c:832a]
    Kernel modules: i2c_i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:832a]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]

```
```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f3:250e Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0bda:58ed Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by praseodym on 2019-02-23
Install the driver via cable

```
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot and deactivate SecureBoot

---

### Post by pabra708 on 2019-03-06
I followed the instructions and my computer went not even displaying that wi-fi was an option to saying "Wireless Networks device not managed." I still can't connect to wireless is checked the rfkill list command and its not either hard or soft blocked. I also saw in the terminal that secure boot is already disabled. I've looked for a hardware switch that turns wi-fi on and off. There doesn't seem to be one. Any idea what else is going on here?

---

