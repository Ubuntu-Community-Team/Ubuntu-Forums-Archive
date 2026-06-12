---
title: "vaio svf1521 &amp; bluetooth problem"
date: 2023-07-29
forum: Networking &amp; Wireless
---

### Post by hu016865 on 2023-07-29
I installed kubuntu 23.04 in uefi mode and bluetooth was not activated.
 with the command

```
cd /lib/firmware/brcm
sudo wget [https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd](https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd)
```

The problem was solved and Bluetooth was activated, but the problem is  that sometimes it disconnects and reconnects for no reason when playing  music. Also, while playing music, 
if I install a program or open firefox or  file manager or do anything else, the music stops and starts and  sometimes it makes a lot of noise.

```
[FONT=monospace][COLOR=#54ff54]**reza@reza-Vaio**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lspci [/COLOR]
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
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
[/FONT]
```

```
[FONT=monospace][COLOR=#000000]root@reza-Vaio:/home/reza# dmesg | grep -i bluetooth[/COLOR]
[    8.743152] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: Core ver 2.22[/COLOR]
[    8.743209] NET: Registered PF_[COLOR=#ff5454]**BLUETOOTH**[/COLOR][COLOR=#000000] protocol family[/COLOR]
[    8.743213] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: HCI device and connection manager initialized[/COLOR]
[    8.743220] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: HCI socket layer initialized[/COLOR]
[    8.743225] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: L2CAP socket layer initialized[/COLOR]
[    8.743235] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: SCO socket layer initialized[/COLOR]
[    9.163930] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM: chip id 70[/COLOR]
[    9.164934] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM: features 0x06[/COLOR]
[    9.180956] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: reza-Vaio[/COLOR]
[    9.180966] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM43142A0 (001.001.011) build 0280[/COLOR]
[    9.185581] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch[/COLOR]
[    9.564969] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: BNEP (Ethernet Emulation) ver 1.3[/COLOR]
[    9.564977] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: BNEP filters: protocol multicast[/COLOR]
[    9.564985] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: BNEP socket layer initialized[/COLOR]
[    9.963936] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM: features 0x06[/COLOR]
[    9.979962] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: Broadcom [/COLOR][COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000] Device (43142)[/COLOR]
[    9.979972] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: hci0: BCM43142A0 (001.001.011) build 0280[/COLOR]
[   10.045709] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: MGMT ver 1.22[/COLOR]
[   13.426422] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: RFCOMM TTY layer initialized[/COLOR]
[   13.426441] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: RFCOMM socket layer initialized[/COLOR]
[   13.426453] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: RFCOMM ver 1.11[/COLOR]
[   24.391738] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: HIDP (Human Interface Emulation) ver 1.2[/COLOR]
[   24.391750] [COLOR=#ff5454]**Bluetooth**[/COLOR][COLOR=#000000]: HIDP socket layer initialized[/COLOR]
[   24.393095] input: Fosi Audio as /devices/pci0000:00/0000:00:1a.0/usb2/2-1/2-1.2/2-1.2:1.0/[COLOR=#ff5454]**bluetooth**[/COLOR][COLOR=#000000]/hci0/hci0:12/0005:000A:FFFF.0002/input/input18[/COLOR]
[   24.393278] hid-generic 0005:000A:FFFF.0002: input,hidraw1: [COLOR=#ff5454]**BLUETOOTH**[/COLOR][COLOR=#000000] HID vff.ff Device [Fosi Audio] on 0c:84:dc:f1:ee:12[/COLOR]
[/FONT]
```

---

### Post by hu016865 on 2023-08-01
i test it in kubuntu 23.04 - debian 12 - ubuntu 22.04 and in all had same problem

---

### Post by hu016865 on 2023-08-08
i installed Ubuntu 22.04 lts and now Bluetooth search but not found my devices.

---

