---
title: "Dell XPS 15 9550 I have wifi but no bluetooth"
date: 2019-07-11
forum: Networking &amp; Wireless
---

### Post by paulp0523 on 2019-07-11
I know the xps series doesn't play well with ubuntu by reading about a hundred tutorials on different way to fix the bluetoooth connectivity problem. For some reason Nothing has worked for me. I tried to add the hcd file to no avail. I tried just about everything and im stumped. This is a pretty serious issue because im on my 5th set of speakers, this laptop is notorious for blowing speakers, i was hoping to just connect bluetooth speakers to avoid this problem. If anyone can help be diagnose this issue i would be greatly appreciate it and Please dont delete this thread it hasn't been answered before. Nothing has worked on my device for some reason.

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:bluetoothd(8)

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1bcf:2b95 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Serial IO I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Serial IO I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 (rev 31)
00:17.0 SATA controller: Intel Corporation HM170/QM170 Chipset SATA Controller [AHCI Mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #1 (rev f1)
00:1c.1 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #2 (rev f1)
00:1d.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #9 (rev f1)
00:1d.4 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #13 (rev f1)
00:1d.6 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #15 (rev f1)
00:1f.0 ISA bridge: Intel Corporation HM170 Chipset LPC/eSPI Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller (rev 31)
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
02:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43602 802.11ac Wireless LAN SoC (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
04:00.0 Non-Volatile memory controller: Toshiba America Info Systems NVMe Controller (rev 01)

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

[http://paste.ubuntu.com/p/GrDnKqzdyB/](http://paste.ubuntu.com/p/GrDnKqzdyB/)

---

