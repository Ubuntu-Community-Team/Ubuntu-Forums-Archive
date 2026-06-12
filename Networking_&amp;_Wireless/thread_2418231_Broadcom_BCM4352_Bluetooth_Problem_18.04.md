---
title: "Broadcom BCM4352 Bluetooth Problem 18.04"
date: 2019-05-03
forum: Networking &amp; Wireless
---

### Post by spode2 on 2019-05-03
I am using a Toshiba Sat-Pro A300 with a combined wifi/bluetooth card BCM4352 and Lubuntu 18.04.

No problems with the wifi, but I cannot get the bluetooth to work. I have copied firmware BCM20702A1-413c-8143.hcd to /lib/firmware/brcm/BCM.hcd and it seems to load, but I am not sure. There are multiple errors in dmesg, and I would be grateful if someone can tell me what they mean.

Thanks.

---

### Post by praseodym on 2019-05-04
Lets see

```
lspci -nnk
lsusb
usb-devices
hciconfig --all
lsmod
```

---

### Post by spode2 on 2019-05-04
Thanks for the reply. I am not sure what the convention is for formatting this information, but here it is:

```
~$ lspci -nnk

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
    Subsystem: Toshiba America Info Systems Mobile PM965/GM965/GL960 Memory Controller Hub [1179:ff1c]
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)
    Subsystem: Toshiba America Info Systems Mobile GM965/GL960 Integrated Graphics Controller (primary) [1179:ff1c]
    Kernel driver in use: i915
    Kernel modules: i915, intelfb
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 03)
    Subsystem: Toshiba America Info Systems Mobile GM965/GL960 Integrated Graphics Controller (secondary) [1179:ff1c]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) USB UHCI Controller [1179:ff1c]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) USB UHCI Controller [1179:ff1c]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) USB2 EHCI Controller [1179:ff1c]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) HD Audio Controller [1179:ff1c]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) USB UHCI Controller [1179:ff1c]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) USB UHCI Controller [1179:ff1c]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) USB UHCI Controller [1179:ff1c]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) USB2 EHCI Controller [1179:ff1c]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Toshiba America Info Systems 82801HM (ICH8M) LPC Interface Controller [1179:ff1c]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
    Subsystem: Toshiba America Info Systems 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [1179:ff1c]
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
    Subsystem: Toshiba America Info Systems 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [1179:ff1c]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Toshiba America Info Systems 82801H (ICH8 Family) SMBus Controller [1179:ff1c]
    Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Toshiba America Info Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1179:ff1c]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0017]
    Kernel driver in use: wl
    Kernel modules: bcma, wl
06:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
    Subsystem: Toshiba America Info Systems R5C832 IEEE 1394 Controller [1179:ff1c]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci
06:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
    Subsystem: Toshiba America Info Systems R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1179:ff1c]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci
06:06.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
    Subsystem: Toshiba America Info Systems R5C592 Memory Stick Bus Host Adapter [1179:ff1c]
    Kernel driver in use: r592
    Kernel modules: r592
06:06.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
    Subsystem: Toshiba America Info Systems xD-Picture Card Controller [1179:ff1c]
    Kernel driver in use: r852
    Kernel modules: r852

```
```
~$ lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 009: ID 413c:8143 Dell Computer Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.15
S:  Manufacturer=Linux 4.15.0-48-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.15
S:  Manufacturer=Linux 4.15.0-48-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.15
S:  Manufacturer=Linux 4.15.0-48-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.15
S:  Manufacturer=Linux 4.15.0-48-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.15
S:  Manufacturer=Linux 4.15.0-48-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.15
S:  Manufacturer=Linux 4.15.0-48-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.15
S:  Manufacturer=Linux 4.15.0-48-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 14 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=413c ProdID=8143 Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM20702A0
S:  SerialNumber=20689D1FADD0
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=btusb
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

```
~$ hciconfig --all

```
~$ lsmod

Module                  Size  Used by
cmac                   16384  0
rfcomm                 77824  0
bnep                   20480  2
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  15 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           24576  1 bluetooth
input_leds             16384  0
i915                 1617920  3
joydev                 24576  0
serio_raw              16384  0
wl                   6447104  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
r852                   20480  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
sm_common              16384  1 r852
nand                   77824  2 r852,sm_common
snd_hda_intel          40960  3
nand_ecc               16384  1 nand
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
nand_bch               16384  1 nand
drm_kms_helper        167936  1 i915
bch                    20480  1 nand_bch
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
mtd                    57344  3 nand,sm_common,nand_bch
r592                   20480  0
drm                   401408  5 drm_kms_helper,i915
memstick               16384  1 r592
cfg80211              622592  1 wl
lpc_ich                24576  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
i2c_algo_bit           16384  1 i915
snd_timer              32768  1 snd_pcm
fb_sys_fops            16384  1 drm_kms_helper
snd                    81920  14 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
soundcore              16384  1 snd
sysimgblt              16384  1 drm_kms_helper
shpchp                 36864  0
toshiba_acpi           45056  0
sparse_keymap          16384  1 toshiba_acpi
industrialio           69632  1 toshiba_acpi
wmi                    24576  1 toshiba_acpi
mac_hid                16384  0
video                  45056  2 toshiba_acpi,i915
sch_fq_codel           20480  3
coretemp               16384  0
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
firewire_ohci          40960  0
firewire_core          65536  1 firewire_ohci
sdhci_pci              32768  0
psmouse               147456  0
ahci                   40960  1
libahci                32768  1 ahci
pata_acpi              16384  0
r8169                  86016  0
sdhci                  49152  1 sdhci_pci
crc_itu_t              16384  1 firewire_core
mii                    16384  1 r8169
```

---

### Post by praseodym on 2019-05-04
Is there an output for this command?

```
modprobe -c | grep -i "413c.*8143"
```

If not, the device is not supported. You can update the driver via

```
sudo apt-get install --reinstall dkms build-essential linux-headers-$(uname -r) git
git clone https://github.com/vignesh0025/bcm2070a0-bluetooth
cd bcm2070a0-bluetooth
sudo mkdir /usr/src/bcm2070a0-1.0
sudo cp -r * /usr/src/bcm2070a0-1.0
sudo dkms add -m bcm2070a0 -v 1.0
sudo dkms build -m bcm2070a0 -v 1.0
sudo dkms install -m bcm2070a0 -v 1.0
```

---

### Post by spode2 on 2019-05-04
Nothing from the modprobe command.

I get an error response from  sudo apt-get install --reinstall dkms build-essential linux-headers-$(uname -r) git

---

### Post by praseodym on 2019-05-05
Ok, remove it
```

sudo dkms remove -m bcm2070a0 -v 1.0 --all
sudo rm -r /usr/src/bcm2070a0-1.0
```
Delete the folder bcm2070a0-bluetooth and try it with the new branch

```
git clone -b v4.8 https://github.com/vignesh0025/bcm2070a0-bluetooth
```

---

### Post by spode2 on 2019-05-05
Thanks for your persistence praseodym. I get errors from the build command now.
Please note that I have little understanding of what I am doing. I followed your delete instructions and entered the git clone command, followed by the rest of the command lines as before.

---

### Post by praseodym on 2019-05-05
Ok, can you contact the maintainer of that github repo?

[https://github.com/vignesh0025](https://github.com/vignesh0025)

---

### Post by spode2 on 2019-05-06
> **praseodym said:**
> Ok, can you contact the maintainer of that github repo?

[https://github.com/vignesh0025](https://github.com/vignesh0025)

Done that, and thanks for your help. I will post any reply I get.

---

### Post by spode2 on 2019-05-07
The maintainer says that his code is not needed for newer kernels and, if just adding the firmware file does not work, I should try a clean install of the OS.

I would prefer to have the Bluetooth working but in its current state it causes a long delay at shutdown and I can live without it, so I have insulated the USB pins on the PCIe card to stop it being detected at all.

Either this is a case where kernel support has been lost in an upgrade, or I have a hardware fault. I suspect the former.

Thanks again,  praseodym

---

