---
title: "firmware for Qualcomm Atheros 802.11ac"
date: 2017-12-15
forum: Networking &amp; Wireless
---

### Post by luca31 on 2017-12-15
Hi all, I'm new to the forum and I'm trying to figure out what firmware is loaded for my wireless card.
I see some warning and error during the loading of the module nonetheless all works like a charm.
Following some clue on my setup and some test I've done:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

$ uname -a 
Linux catorcio 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

$ lspci -vvvknn -s 02:00.0
02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Lite-On Communications Inc QCA6174 802.11ac Wireless Network Adapter [11ad:0807]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 333
    Region 0: Memory at 94200000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci

$ modinfo ath10k_pci
filename:       /lib/modules/4.10.0-42-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     55269025DC0881FB8B580CD
alias:          pci:v0000168Cd00000050sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000042sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000046sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000056sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000040sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000041sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

$ dmesg
...
[    4.097421] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
[    4.097428] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    4.097596] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.097597] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.098913] ath10k_pci 0000:02:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
[    4.098914] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.099274] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    4.163450] ath10k_pci 0000:02:00.0: board_file api 2 bmi_id N/A crc32 6fc88fe7
...

$ dpkg -l linux-firmware 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/  Name                                                           Version                             Architecture                         Description
+++-=============================================================-===================================-===================================-================================================================================================================================
ii   linux-firmware                                                 1.157.14                            all                                  Firmware for Linux kernel drivers

$ ls -l /lib/firmware/ath10k/
total 0
drwxr-xr-x 1 root root 10 ago  1 13:21 QCA4019
drwxr-xr-x 1 root root 20 ago  1 13:21 QCA6174
drwxr-xr-x 1 root root 10 ago  1 13:21 QCA9377
drwxr-xr-x 1 root root 10 ago  1 13:21 QCA9887
drwxr-xr-x 1 root root 10 ago  1 13:21 QCA9888
drwxr-xr-x 1 root root 10 ago  1 13:21 QCA988X
drwxr-xr-x 1 root root 10 ago  1 13:21 QCA9984
drwxr-xr-x 1 root root 10 ago  1 13:21 QCA99X0

$ ls -l /lib/firmware/ath10k/QCA6174/hw*
/lib/firmware/ath10k/QCA6174/hw2.1:
total 804
-rw-r--r-- 1 root root 263188 nov  9 20:36 board-2.bin
-rw-r--r-- 1 root root   8124 dic  1  2016 board.bin
-rw-r--r-- 1 root root 498172 nov  9 20:36 firmware-5.bin
-rw-r--r-- 1 root root  46087 dic  1  2016 notice_ath10k_firmware-5.txt

/lib/firmware/ath10k/QCA6174/hw3.0:
total 1920
-rw-r--r-- 1 root root 337204 nov 15 22:56 board-2.bin
-rw-r--r-- 1 root root   8124 dic  1  2016 board.bin
-rw-r--r-- 1 root root 733784 dic  1  2016 firmware-4.bin
-rw-r--r-- 1 root root 711408 nov 15 22:44 firmware-6.bin
-rw-r--r-- 1 root root  79689 dic  1  2016 notice_ath10k_firmware-4.txt
-rw-r--r-- 1 root root  82663 nov 15 22:44 notice_ath10k_firmware-6.txt

```

So it seems the module tries to load some missing file
ath10k/pre-cal-pci-0000:02:00.0.bin
ath10k/cal-pci-0000:02:00.0.bin 
ath10k/QCA6174/hw3.0/firmware-5.bin
and eventually it can load the firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 from somewhere. Is there a way to show what file is used?
Following the hints of the interesting article on the wiki about the [firmware ]("https://wiki.ubuntu.com/Kernel/Firmware")
I check the udev message during the loading of the module using the commands: 
```

sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci

```
but no firmware request from the kernel is reported, here's the events:

```

$ udevadm monitor --property
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[6686.718598] add      /module/cfg80211 (module)
ACTION=add
DEVPATH=/module/cfg80211
SEQNUM=3855
SUBSYSTEM=module

KERNEL[6686.718657] add      /class/ieee80211 (class)
ACTION=add
DEVPATH=/class/ieee80211
SEQNUM=3856
SUBSYSTEM=class

KERNEL[6686.718683] add      /devices/platform/regulatory.0 (platform)
ACTION=add
DEVPATH=/devices/platform/regulatory.0
MODALIAS=platform:regulatory
SEQNUM=3857
SUBSYSTEM=platform

KERNEL[6686.718705] change   /devices/platform/regulatory.0 (platform)
ACTION=change
COUNTRY=00
DEVPATH=/devices/platform/regulatory.0
MODALIAS=platform:regulatory
SEQNUM=3858
SUBSYSTEM=platform

UDEV  [6686.719140] add      /module/cfg80211 (module)
ACTION=add
DEVPATH=/module/cfg80211
SEQNUM=3855
SUBSYSTEM=module
USEC_INITIALIZED=6686719108

UDEV  [6686.719288] add      /class/ieee80211 (class)
ACTION=add
DEVPATH=/class/ieee80211
SEQNUM=3856
SUBSYSTEM=class
USEC_INITIALIZED=6686719264

UDEV  [6686.719581] add      /devices/platform/regulatory.0 (platform)
ACTION=add
DEVPATH=/devices/platform/regulatory.0
MODALIAS=platform:regulatory
SEQNUM=3857
SUBSYSTEM=platform
USEC_INITIALIZED=6686719513

UDEV  [6686.721471] change   /devices/platform/regulatory.0 (platform)
ACTION=change
COUNTRY=00
DEVPATH=/devices/platform/regulatory.0
MODALIAS=platform:regulatory
SEQNUM=3858
SUBSYSTEM=platform
USEC_INITIALIZED=6686719739

KERNEL[6686.727620] add      /module/mac80211 (module)
ACTION=add
DEVPATH=/module/mac80211
SEQNUM=3859
SUBSYSTEM=module

UDEV  [6686.728116] add      /module/mac80211 (module)
ACTION=add
DEVPATH=/module/mac80211
SEQNUM=3859
SUBSYSTEM=module
USEC_INITIALIZED=6686728092

KERNEL[6686.728823] add      /module/ath (module)
ACTION=add
DEVPATH=/module/ath
SEQNUM=3860
SUBSYSTEM=module

UDEV  [6686.729209] add      /module/ath (module)
ACTION=add
DEVPATH=/module/ath
SEQNUM=3860
SUBSYSTEM=module
USEC_INITIALIZED=6686729180

KERNEL[6686.732426] add      /module/ath10k_core (module)
ACTION=add
DEVPATH=/module/ath10k_core
SEQNUM=3861
SUBSYSTEM=module

UDEV  [6686.733002] add      /module/ath10k_core (module)
ACTION=add
DEVPATH=/module/ath10k_core
SEQNUM=3861
SUBSYSTEM=module
USEC_INITIALIZED=6686732962

KERNEL[6686.733704] add      /module/ath10k_pci (module)
ACTION=add
DEVPATH=/module/ath10k_pci
SEQNUM=3862
SUBSYSTEM=module

UDEV  [6686.734194] add      /module/ath10k_pci (module)
ACTION=add
DEVPATH=/module/ath10k_pci
SEQNUM=3862
SUBSYSTEM=module
USEC_INITIALIZED=6686734155

KERNEL[6686.867210] add      /bus/pci/drivers/ath10k_pci (drivers)
ACTION=add
DEVPATH=/bus/pci/drivers/ath10k_pci
SEQNUM=3863
SUBSYSTEM=drivers

UDEV  [6686.868686] add      /bus/pci/drivers/ath10k_pci (drivers)
ACTION=add
DEVPATH=/bus/pci/drivers/ath10k_pci
SEQNUM=3863
SUBSYSTEM=drivers
USEC_INITIALIZED=6686868591

KERNEL[6689.312421] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0
(ieee80211)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0
SEQNUM=3864
SUBSYSTEM=ieee80211

KERNEL[6689.312454] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
(rfkill)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
RFKILL_NAME=phy0
RFKILL_STATE=1
RFKILL_TYPE=wlan
SEQNUM=3865
SUBSYSTEM=rfkill

KERNEL[6689.313258] change
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
(rfkill)
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
RFKILL_NAME=phy0
RFKILL_STATE=0
RFKILL_TYPE=wlan
SEQNUM=3866
SUBSYSTEM=rfkill

KERNEL[6689.313424] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0 (net)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0
DEVTYPE=wlan
IFINDEX=4
INTERFACE=wlan0
SEQNUM=3867
SUBSYSTEM=net

KERNEL[6689.313451] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/rx-0
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/rx-0
SEQNUM=3868
SUBSYSTEM=queues

KERNEL[6689.313467] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-0
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-0
SEQNUM=3869
SUBSYSTEM=queues

KERNEL[6689.313480] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-1
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-1
SEQNUM=3870
SUBSYSTEM=queues

KERNEL[6689.313491] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-2
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-2
SEQNUM=3871
SUBSYSTEM=queues

KERNEL[6689.313502] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-3
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-3
SEQNUM=3872
SUBSYSTEM=queues

KERNEL[6689.314245] add      /devices/virtual/thermal/cooling_device9 (thermal)
ACTION=add
DEVPATH=/devices/virtual/thermal/cooling_device9
SEQNUM=3873
SUBSYSTEM=thermal

UDEV  [6689.314277] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0
(ieee80211)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0
SEQNUM=3864
SUBSYSTEM=ieee80211
USEC_INITIALIZED=6689313064

UDEV  [6689.314587] add      /devices/virtual/thermal/cooling_device9 (thermal)
ACTION=add
DEVPATH=/devices/virtual/thermal/cooling_device9
SEQNUM=3873
SUBSYSTEM=thermal
USEC_INITIALIZED=6689314511

UDEV  [6689.314625] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
(rfkill)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
ID_PATH=pci-0000:02:00.0
ID_PATH_TAG=pci-0000_02_00_0
RFKILL_NAME=phy0
RFKILL_STATE=1
RFKILL_TYPE=wlan
SEQNUM=3865
SUBSYSTEM=rfkill
USEC_INITIALIZED=6689314560

UDEV  [6689.314932] change
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
(rfkill)
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
ID_PATH=pci-0000:02:00.0
ID_PATH_TAG=pci-0000_02_00_0
RFKILL_NAME=phy0
RFKILL_STATE=0
RFKILL_TYPE=wlan
SEQNUM=3866
SUBSYSTEM=rfkill
USEC_INITIALIZED=6689314560

KERNEL[6689.315463] move
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0 (net)
ACTION=move
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
DEVPATH_OLD=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0
DEVTYPE=wlan
IFINDEX=4
INTERFACE=wlp2s0
SEQNUM=3874
SUBSYSTEM=net

UDEV  [6689.344085] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0 (net)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
DEVTYPE=wlan
ID_BUS=pci
ID_MM_CANDIDATE=1
ID_MODEL_FROM_DATABASE=QCA6174 802.11ac Wireless Network Adapter
ID_MODEL_ID=0x003e
ID_NET_DRIVER=ath10k_pci
ID_NET_LINK_FILE=/lib/systemd/network/99-default.link
ID_NET_NAME=wlp2s0
ID_NET_NAME_MAC=wlx3ca06798bcc5
ID_NET_NAME_PATH=wlp2s0
ID_PATH=pci-0000:02:00.0
ID_PATH_TAG=pci-0000_02_00_0
ID_PCI_CLASS_FROM_DATABASE=Network controller
ID_PCI_SUBCLASS_FROM_DATABASE=Network controller
ID_VENDOR_FROM_DATABASE=Qualcomm Atheros
ID_VENDOR_ID=0x168c
IFINDEX=4
INTERFACE=wlp2s0
INTERFACE_OLD=
SEQNUM=3867
SUBSYSTEM=net
SYSTEMD_ALIAS=/sys/subsystem/net/devices/wlp2s0
TAGS=:systemd:
USEC_INITIALIZED=6689340337

UDEV  [6689.345331] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/rx-0
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/rx-0
SEQNUM=3868
SUBSYSTEM=queues
USEC_INITIALIZED=6689345284

UDEV  [6689.345365] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-1
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-1
SEQNUM=3870
SUBSYSTEM=queues
USEC_INITIALIZED=6689345287

UDEV  [6689.345555] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-2
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-2
SEQNUM=3871
SUBSYSTEM=queues
USEC_INITIALIZED=6689345524

UDEV  [6689.345680] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-0
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-0
SEQNUM=3869
SUBSYSTEM=queues
USEC_INITIALIZED=6689345605

UDEV  [6689.345802] add
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-3
(queues)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/queues/tx-3
SEQNUM=3872
SUBSYSTEM=queues
USEC_INITIALIZED=6689345724

UDEV  [6689.346920] move
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0 (net)
ACTION=move
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
DEVPATH_OLD=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0
DEVTYPE=wlan
ID_BUS=pci
ID_MM_CANDIDATE=1
ID_MODEL_FROM_DATABASE=QCA6174 802.11ac Wireless Network Adapter
ID_MODEL_ID=0x003e
ID_NET_DRIVER=ath10k_pci
ID_NET_LINK_FILE=/lib/systemd/network/99-default.link
ID_NET_NAME=wlp2s0
ID_NET_NAME_MAC=wlx3ca06798bcc5
ID_NET_NAME_PATH=wlp2s0
ID_PATH=pci-0000:02:00.0
ID_PATH_TAG=pci-0000_02_00_0
ID_PCI_CLASS_FROM_DATABASE=Network controller
ID_PCI_SUBCLASS_FROM_DATABASE=Network controller
ID_VENDOR_FROM_DATABASE=Qualcomm Atheros
ID_VENDOR_ID=0x168c
IFINDEX=4
INTERFACE=wlp2s0
SEQNUM=3874
SUBSYSTEM=net
SYSTEMD_ALIAS=/sys/subsystem/net/devices/wlp2s0
/sys/subsystem/net/devices/wlp2s0
TAGS=:systemd:
USEC_INITIALIZED=6689340337

KERNEL[7921.382397] change   /devices/platform/acer-wmi/rfkill/rfkill1 (rfkill)
ACTION=change
DEVPATH=/devices/platform/acer-wmi/rfkill/rfkill1
RFKILL_NAME=acer-wireless
RFKILL_STATE=1
RFKILL_TYPE=wlan
SEQNUM=3875
SUBSYSTEM=rfkill

KERNEL[7921.382532] change
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
(rfkill)
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
RFKILL_NAME=phy0
RFKILL_STATE=1
RFKILL_TYPE=wlan
SEQNUM=3876
SUBSYSTEM=rfkill

UDEV  [7921.383821] change   /devices/platform/acer-wmi/rfkill/rfkill1 (rfkill)
ACTION=change
DEVPATH=/devices/platform/acer-wmi/rfkill/rfkill1
ID_PATH=platform-acer-wmi
ID_PATH_TAG=platform-acer-wmi
RFKILL_NAME=acer-wireless
RFKILL_STATE=1
RFKILL_TYPE=wlan
SEQNUM=3875
SUBSYSTEM=rfkill
USEC_INITIALIZED=3384955

UDEV  [7921.383919] change
/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
(rfkill)
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill3
ID_PATH=pci-0000:02:00.0
ID_PATH_TAG=pci-0000_02_00_0
RFKILL_NAME=phy0
RFKILL_STATE=1
RFKILL_TYPE=wlan
SEQNUM=3876
SUBSYSTEM=rfkill
USEC_INITIALIZED=6689314560

```

Shoud I open a bug on linux-firmware package to highlight the non problem? 
Is the module code to select what file is loaded as the firmware? 
If so a specific version of the module is bound to specific firmware paths, right?
Is there a place in /sys/bus/pci/devices to see what firmware is used?
I'm wondering if I shoud create a link /lib/firmware/ath10k/QCA6174/hw3.0/firmware-5.bin to the existent /lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin to see what happens 
Anyway my wireless card works without problems or worse I haven't realized possible issues, anyway I'd like to look a little more under the hood. 

Regards

Luca

---

### Post by praseodym on 2017-12-15
Try

```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```

Reboot

---

### Post by luca31 on 2017-12-15
Cool, I pulled the new firmware for atheros from the git repo with the following commands:

```

$ git init linux-firmware
Initialized empty Git repository in /mnt/fogna/linux-firmware/.git/
$ cd linux-firmware/
$ git remote add origin git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
$ git remote -v
origin    git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git (fetch)
origin    git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git (push)
$ git config core.sparsecheckout true
$ echo "ath10k/*" >> .git/info/sparse-checkout
$ git remote show origin
* remote origin
  Fetch URL: git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
  Push  URL: git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
  HEAD branch: master
  Remote branch:
    master new (next fetch will store in remotes/origin)
$ git pull --depth=1 origin master
remote: Counting objects: 1692, done.
remote: Compressing objects: 100% (1142/1142), done.
remote: Total 1692 (delta 533), reused 1509 (delta 456)
Receiving objects: 100% (1692/1692), 105.14 MiB | 806.00 KiB/s, done.
Resolving deltas: 100% (533/533), done.
From git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master

```

But it seems the only changed file for atheros chipset QCA6174 are hw3.0/{ath10k_firmware-6.bin,board-2.bin,notice_ath10k_firmware-6.txt}. 

```

$ git branch
* master
$ cd ath10k/
$ ls
QCA4019  QCA6174  QCA9377  QCA9887  QCA9888  QCA988X  QCA9984  QCA99X0
$ diff <(cd /lib/firmware && find ./ath10k/QCA6174/* -type f |  sort |xargs md5sum) <(cd ../linux-firmware && find  ./ath10k/QCA6174/* -type f | sort | xargs md5sum)
5c5
< 4807903c956dbd8b87f5d83c559c2211  ./ath10k/QCA6174/hw3.0/board-2.bin
---
> 59ba4641c5e2d1bc1227b02eff15cd4c  ./ath10k/QCA6174/hw3.0/board-2.bin
8c8
< 48605abe5f687f66131a2a39fc531965  ./ath10k/QCA6174/hw3.0/firmware-6.bin
---
> fcdc7ffe6226f0c94268933ff1d7a4bb  ./ath10k/QCA6174/hw3.0/firmware-6.bin
10c10
< dd40c15ea4a9096e4977dd6ac2e22163  ./ath10k/QCA6174/hw3.0/notice_ath10k_firmware-6.txt
---
> 1996ef26689766a457043339661141c2  ./ath10k/QCA6174/hw3.0/notice_ath10k_firmware-6.txt

```

Anyway I decided to give it a go and backuped the /lib/firmware/ath10k just in case something goes wrong

```

$ sudo cp -ax --reflink=always /mnt/zero/@/lib/firmware/ath10k /mnt/zero/snapshots/firmware
$ cd /mnt/fogna/linux-firmware/ath10k/QCA6174/hw3.0/
$ sudo cp -a board-2.bin firmware-6.bin notice_ath10k_firmware-6.txt /lib/firmware/ath10k/QCA6174/hw3.0/

```

Then I reloaded the ath10k_pci driver with modprobe:

```

$ modprobe -r ath10k_pci
$ modprobe ath10k_pci

```

here's the same error msg from syslog snippet

```

$ cat /var/syslog
Dec 16 03:17:48 catorcio kernel: [14188.388163] ath10k_pci 0000:02:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
Dec 16 03:17:48 catorcio kernel: [14188.662678] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662691] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662702] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662704] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
Dec 16 03:17:48 catorcio kernel: [14188.663053] ath10k_pci 0000:02:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
Dec 16 03:17:48 catorcio kernel: [14188.663056] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
Dec 16 03:17:48 catorcio kernel: [14188.664251] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
Dec 16 03:17:48 catorcio kernel: [14188.727570] ath10k_pci 0000:02:00.0: board_file api 2 bmi_id N/A crc32 0e26ef70
Dec 16 03:17:50 catorcio kernel: [14190.882601] ath10k_pci 0000:02:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1

```

I think the driver is asking for a wrong path, but I don't know if the firmware path is hardlinked in the driver code. 
Tomorrow I'll search for the module sources and surely I'll have hard times to figure out it because I'm unfortunately not a super skilled kernel developer :(
Anyway I've got some fun with git 
thanks fot the tip 

good night 

Luca

---

### Post by praseodym on 2017-12-16
```
Dec 16 03:17:48 catorcio kernel: [14188.662678] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662691] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662702] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662704] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
```
These files sghould be there. Maybe creating these paths, if not there?!

---

### Post by luca31 on 2017-12-16
Yes they should, but they aren't included in the release 1.157.14 of the linux-firmware package, nor on the [git repository]("git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git") that you kindly adviced.
Nevertheless the card works properly. The module loads another firmware: 
<CODE>
[    4.133353] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
</CODE>
but I don't know how, it may fallback on another firmware file or maybe on the built-in firmware.
I'd like to figure out what file is loaded and how for the sake of awareness. 
And if I should open a bug to highlight the missing firmware files.

Cheers

Luca

---

### Post by jeremy31 on 2017-12-16
I think some of the firmware files only exist for the Atheros wifi cards used in routers, the cal-pci, pre-cal-pci but the driver searches for them anyhow.  Intel linux wifi drivers do something similar as they search for the highest firmware version supported by the kernel, if that one isn't found, it searches the next oldest firmware and continues until it finds firmware or reaches the minimum firmware version supported by the kernel
```
 ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
```
That line shows that firmware-4.bin is loaded(api 4) and it is version WLAN.RM.2.0-00180-QCARMSWPZ-1
If it works, I would not make changes

---

### Post by chili555 on 2017-12-16
> **jeremy31 said:**
> I think some of the firmware files only exist for the Atheros wifi cards used in routers, the cal-pci, pre-cal-pci but the driver searches for them anyhow.  Intel linux wifi drivers do something similar as they search for the highest firmware version supported by the kernel, if that one isn't found, it searches the next oldest firmware and continues until it finds firmware or reaches the minimum firmware version supported by the kernel
```
 ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
```
That line shows that firmware-4.bin is loaded(api 4) and it is version WLAN.RM.2.0-00180-QCARMSWPZ-1
If it works, I would not make changesExactly! I agree completely. Please resist the temptation to tweak it until it breaks. The dmesg you see here is entirely normal and expected:```
Dec 16 03:17:48 catorcio kernel: [14188.662678] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662691] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662702] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
Dec 16 03:17:48 catorcio kernel: [14188.662704] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
Dec 16 03:17:48 catorcio kernel: [14188.663053] ath10k_pci 0000:02:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
Dec 16 03:17:48 catorcio kernel: [14188.663056] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
Dec 16 03:17:48 catorcio kernel: [14188.664251] ath10k_pci 0000:02:00.0: [COLOR="#FF0000"]firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5[/COLOR]
Dec 16 03:17:48 catorcio kernel: [14188.727570] ath10k_pci 0000:02:00.0: board_file api 2 bmi_id N/A crc32 0e26ef70
Dec 16 03:17:50 catorcio kernel: [14190.882601] ath10k_pci 0000:02:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
```

We hate the kind of questions that start out with an explanation that the wireless worked fine, then s/he downloaded a bunch of drivers and firmware and next added a few driver parameters and then some grub parameters and now the wireless doesn't work be cause the whole entire computer won't even boot! And, by the way, could one of the wireless gurus please duct tape and superglue the thing back together.

---

### Post by luca31 on 2017-12-16
You're right the file loaded is the firmware-4.bin
I dumped few bytes  of the binary in order to match the version shown by dmesg, is there a  more straight way to get that version number?

```

$ hexdump -C /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin -n100
00000000  51 43 41 2d 41 54 48 31  30 4b 00 77 00 00 00 00  |QCA-ATH10K.w....|
00000010  1d 00 00 00 57 4c 41 4e  2e 52 4d 2e 32 2e 30 2d  |....WLAN.RM.2.0-|
00000020  30 30 31 38 30 2d 51 43  41 52 4d 53 57 50 5a 2d  |00180-QCARMSWPZ-|
00000030  31 77 77 77 01 00 00 00  04 00 00 00 6a 42 c5 55  |1www........jB.U|

```

Playing with drivers and firmwares are interesting enough to risk a  temporary system failure, after all you can always count on some  friendly guru on the forum ^__^

---

### Post by jeremy31 on 2017-12-16
You might be able to see the version number in the results for ```
lshw -c net
```
If you mess the firmware up you might have to delete the contents of /lib/firmware/ath10k/QCA6174/hw3.0/ before doing a ```
sudo apt-get install --reinstall linux-firmware
```

---

### Post by chili555 on 2017-12-16
> Playing with drivers and firmwares are interesting enough to risk a temporary system failure, after all you can always count on some friendly guru on the forum ^__^I'm digging out my personal protective equipment now. The smoke is not too bad but the sparks *really* bother me.

[IMG]https://www.homehardware.ca/products/300/54251951.jpg[/IMG]

---

### Post by luca31 on 2017-12-16
Eventually I glanced the module code from the kernel source fetched using apt-get source linux-image-extra-4.10.0-42-generic
The following function in linux-hwe-4.10.0/drivers/net/wireless/ath/ath10k/core.c should implement the logic of fallback for the firmware binary  

```

static int ath10k_core_fetch_firmware_files(struct ath10k *ar)
{
        int ret;

        /* calibration file is optional, don't check for any errors */
        ath10k_fetch_cal_file(ar);

        ar->fw_api = 5;
        ath10k_dbg(ar, ATH10K_DBG_BOOT, "trying fw api %d\n", ar->fw_api);

        ret = ath10k_core_fetch_firmware_api_n(ar, ATH10K_FW_API5_FILE,
                                               &ar->normal_mode_fw.fw_file);
        if (ret == 0)
                goto success;

        ar->fw_api = 4;
        ath10k_dbg(ar, ATH10K_DBG_BOOT, "trying fw api %d\n", ar->fw_api);

        ret = ath10k_core_fetch_firmware_api_n(ar, ATH10K_FW_API4_FILE,
                                               &ar->normal_mode_fw.fw_file);
        if (ret == 0)
                goto success;

        ar->fw_api = 3;
        ath10k_dbg(ar, ATH10K_DBG_BOOT, "trying fw api %d\n", ar->fw_api);

        ret = ath10k_core_fetch_firmware_api_n(ar, ATH10K_FW_API3_FILE,
                                               &ar->normal_mode_fw.fw_file);
        if (ret == 0)
                goto success;

        ar->fw_api = 2;
        ath10k_dbg(ar, ATH10K_DBG_BOOT, "trying fw api %d\n", ar->fw_api);

        ret = ath10k_core_fetch_firmware_api_n(ar, ATH10K_FW_API2_FILE,
                                               &ar->normal_mode_fw.fw_file);
        if (ret)
                return ret;

success:
        ath10k_dbg(ar, ATH10K_DBG_BOOT, "using fw api %d\n", ar->fw_api);

        return 0;
}

```

I'd confirm also that the binaries path are hardlinked in other headers/files of the modules  

```

ls *c *h ath10k/* | xargs grep -n ATH10K_FW_API[45]_FILE 
ath10k/core.c:1385:    ret = ath10k_core_fetch_firmware_api_n(ar, ATH10K_FW_API5_FILE,
ath10k/core.c:1393:    ret = ath10k_core_fetch_firmware_api_n(ar, ATH10K_FW_API4_FILE,
ath10k/hw.h:135:#define ATH10K_FW_API4_FILE        "firmware-4.bin"
ath10k/hw.h:138:#define ATH10K_FW_API5_FILE        "firmware-5.bin"
ath10k/pci.c:3400:MODULE_FIRMWARE(QCA988X_HW_2_0_FW_DIR "/" ATH10K_FW_API4_FILE);
ath10k/pci.c:3401:MODULE_FIRMWARE(QCA988X_HW_2_0_FW_DIR "/" ATH10K_FW_API5_FILE);
ath10k/pci.c:3406:MODULE_FIRMWARE(QCA9887_HW_1_0_FW_DIR "/" ATH10K_FW_API5_FILE);
ath10k/pci.c:3411:MODULE_FIRMWARE(QCA6174_HW_2_1_FW_DIR "/" ATH10K_FW_API4_FILE);
ath10k/pci.c:3412:MODULE_FIRMWARE(QCA6174_HW_2_1_FW_DIR "/" ATH10K_FW_API5_FILE);
ath10k/pci.c:3417:MODULE_FIRMWARE(QCA6174_HW_3_0_FW_DIR "/" ATH10K_FW_API4_FILE);
ath10k/pci.c:3418:MODULE_FIRMWARE(QCA6174_HW_3_0_FW_DIR "/" ATH10K_FW_API5_FILE);
ath10k/pci.c:3423:MODULE_FIRMWARE(QCA9377_HW_1_0_FW_DIR "/" ATH10K_FW_API5_FILE);

```

Anyway keep the equipments in handy, just in case of future fault, I mean fire.. 

[IMG]http://pop-verse.com/wp-content/uploads/2017/08/it-crowd-moss-fire-768x432.jpg[/IMG]

 thanks a lot for the support

---

