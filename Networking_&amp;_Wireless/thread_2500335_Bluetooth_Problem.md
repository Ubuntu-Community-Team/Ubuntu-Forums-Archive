---
title: "Bluetooth Problem"
date: 2024-08-30
forum: Networking &amp; Wireless
---

### Post by hu016865 on 2024-08-30
I have a problem with my laptop bluetooth.
Bluetooth did not work after installing Ubuntu 24.04, which was activated with the following command
> cd /lib/firmware/brcm
sudo wget [https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd](https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd)

After restarting, Bluetooth is activated, but when I connect to my amplifier with Bluetooth and play a song, the sound keeps disconnecting and reconnecting, and the music does not play stably.
If this problem does not exist in Windows.
My laptop model is Sony Vaio 1521BYGB.

> reza@reza-SVF1521BYGB:/lib/firmware/brcm$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller (rev 0c)



> reza@reza-SVF1521BYGB:/lib/firmware/brcm$ sudo dmesg | grep -i bluetooth
[sudo] password for reza: 
[   25.398686] Bluetooth: Core ver 2.22
[   25.398736] NET: Registered PF_BLUETOOTH protocol family
[   25.398741] Bluetooth: HCI device and connection manager initialized
[   25.398749] Bluetooth: HCI socket layer initialized
[   25.398754] Bluetooth: L2CAP socket layer initialized
[   25.398763] Bluetooth: SCO socket layer initialized
[   25.906485] Bluetooth: hci0: BCM: chip id 70
[   25.907497] Bluetooth: hci0: BCM: features 0x06
[   25.923630] Bluetooth: hci0: reza-SVF1521BYGB
[   25.923655] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[   26.602294] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[   27.305544] Bluetooth: hci0: BCM: features 0x06
[   27.321588] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[   27.321631] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[   38.309506] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.309523] Bluetooth: BNEP filters: protocol multicast
[   38.309536] Bluetooth: BNEP socket layer initialized
[   38.316678] Bluetooth: MGMT ver 1.22
[   59.076824] Bluetooth: RFCOMM TTY layer initialized
[   59.076857] Bluetooth: RFCOMM socket layer initialized
[   59.076882] Bluetooth: RFCOMM ver 1.11
[ 2301.809476] Bluetooth: hci0: BCM: chip id 70
[ 2301.810471] Bluetooth: hci0: BCM: features 0x06
[ 2301.826478] Bluetooth: hci0: reza-SVF1521BYGB
[ 2301.826488] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 2301.827741] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[ 2302.522693] Bluetooth: hci0: BCM: features 0x06
[ 2302.539693] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[ 2302.539719] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 2302.619455] Bluetooth: MGMT ver 1.22
[ 2305.265511] Bluetooth: hci0: BCM: chip id 70
[ 2305.266505] Bluetooth: hci0: BCM: features 0x06
[ 2305.282511] Bluetooth: hci0: reza-SVF1521BYGB
[ 2305.282522] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 2305.283766] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[ 2305.978691] Bluetooth: hci0: BCM: features 0x06
[ 2305.995679] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[ 2305.995710] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 2306.075692] Bluetooth: MGMT ver 1.22
[ 2531.019874] Bluetooth: hci0: BCM: chip id 70
[ 2531.020871] Bluetooth: hci0: BCM: features 0x06
[ 2531.036890] Bluetooth: hci0: reza-SVF1521BYGB
[ 2531.036900] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 2531.038140] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[ 2531.739949] Bluetooth: hci0: BCM: features 0x06
[ 2531.756135] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[ 2531.756174] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 2531.812678] Bluetooth: MGMT ver 1.22
[ 2550.851737] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 2550.851801] Bluetooth: HIDP socket layer initialized
[ 2554.625615] input: Fosi Audio as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/bluetooth/hci0/hci0:12/0005:000A:FFFF.0002/input/input18
[ 2554.628920] hid-generic 0005:000A:FFFF.0002: input,hidraw1: BLUETOOTH HID vff.ff Device [Fosi Audio] on 0c:84:dc:f1:ee:12


---

### Post by currentshaft on 2024-08-30
Are you also connected over 2.4 Ghz wifi at the same time by chance?

---

