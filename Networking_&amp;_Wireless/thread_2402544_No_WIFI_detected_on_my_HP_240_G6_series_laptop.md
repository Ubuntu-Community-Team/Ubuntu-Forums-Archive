---
title: "No WIFI detected on my HP 240 G6 series laptop"
date: 2018-10-01
forum: Networking &amp; Wireless
---

### Post by smcm2 on 2018-10-01
I'm kind of new on UBUNTU, please I need help, I have this HP 240 G6 series laptop and I had just installed Ubuntu 18.04 LTE, my WIFI is not detected, as far as I know is a Realteck, how can I fix this problem?

---

### Post by praseodym on 2018-10-01
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands
```

lspci -nnk
lsusb
```
Does LAN work?

---

### Post by smcm2 on 2018-10-02
Yes, my LAN is working.

```
root@sergioc-notebook-pc:/# lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5904] (rev 02)
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [103c:831e]
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02)
    Subsystem: Hewlett-Packard Company HD Graphics 620 [103c:831e]
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller [1180]: Intel Corporation Skylake Processor Thermal Subsystem [8086:1903] (rev 02)
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [103c:831e]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP USB 3.0 xHCI Controller [103c:831e]
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP Thermal subsystem [103c:831e]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP CSME HECI [103c:831e]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP SATA Controller [AHCI mode] [103c:831e]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port [8086:9d10] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 [8086:9d15] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 [8086:9d18] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d4e] (rev 21)
    Subsystem: Hewlett-Packard Company Device [103c:831e]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP PMC [103c:831e]
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d71] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP HD Audio [103c:831e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    Subsystem: Hewlett-Packard Company Sunrise Point-LP SMBus [103c:831e]
    Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:831e]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]
    Kernel modules: ndiswrapper
```

```
root@sergioc-notebook-pc:/# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 1bcf:2c9b Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by praseodym on 2018-10-02
Please run

```
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot and deactivate SecureBoot.

---

### Post by smcm2 on 2018-10-09
Desde la primera linea de da problemas:

root@SergioC-Notebook-PC:/# sudo apt-get remove --purge ndisgtk ndiswrapper *
```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete bin
E: No se ha podido localizar el paquete boot
E: No se ha podido localizar el paquete cdrom
E: No se ha podido localizar el paquete dev
E: No se ha podido localizar el paquete etc
E: No se ha podido localizar el paquete home
E: No se ha podido localizar el paquete initrd.img
E: No se pudo encontrar ningún paquete usando «*» con «initrd.img»
E: No se pudo encontrar ningún paquete con la expresión regular «initrd.img»
E: No se ha podido localizar el paquete initrd.img.old
E: No se pudo encontrar ningún paquete usando «*» con «initrd.img.old»
E: No se pudo encontrar ningún paquete con la expresión regular «initrd.img.old»
E: No se ha podido localizar el paquete lib
E: No se ha podido localizar el paquete lib64
E: No se ha podido localizar el paquete lost+found
E: No se pudo encontrar ningún paquete con la expresión regular «lost+found»
E: No se ha podido localizar el paquete media
E: No se ha podido localizar el paquete mnt
E: No se ha podido localizar el paquete proc
E: No se ha podido localizar el paquete root
E: No se ha podido localizar el paquete run
E: No se ha podido localizar el paquete sbin
E: No se ha podido localizar el paquete skype-ubuntu-precise_4.3.0.37-1_i386.deb
E: No se pudo encontrar ningún paquete usando «*» con «skype-ubuntu-precise_4.3.0.37-1_i386.deb»
E: No se pudo encontrar ningún paquete con la expresión regular «skype-ubuntu-precise_4.3.0.37-1_i386.deb»
E: No se ha podido localizar el paquete srv
E: No se ha podido localizar el paquete swapfile
E: No se ha podido localizar el paquete sys
E: No se ha podido localizar el paquete tmp
E: No se ha podido localizar el paquete usr
E: No se ha podido localizar el paquete var
E: No se ha podido localizar el paquete vmlinuz
E: No se ha podido localizar el paquete vmlinuz.old
E: No se pudo encontrar ningún paquete usando «*» con «vmlinuz.old»
E: No se pudo encontrar ningún paquete con la expresión regular «vmlinuz.old»
```

---

### Post by wildmanne39 on 2018-10-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

