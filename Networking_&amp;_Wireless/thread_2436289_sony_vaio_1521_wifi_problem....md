---
title: "sony vaio 1521 wifi problem..."
date: 2020-02-03
forum: Networking &amp; Wireless
---

### Post by hu016865 on 2020-02-03
i have a sony vaio 1521 with ubuntu 19.10 "uefi" everythings are ok . but wifi dont work.
i update ubuntu and in additinal update for wifi was an update.i installed it but wifi dont work yet.
i tried to : sudo apt install bcmwl-kernel-sourcebut dont work.
> $ lspci -nn -d 14e4:
07:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)

> $ rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no




> ~$  lspci00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
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



now how can i fix it ?

---

### Post by chili555 on 2020-02-03
Please run this terminal command and reply with the result:```
sudo modprobe wl && dmesg | grep wl
```Thanks.

---

### Post by CelticWarrior on 2020-02-03
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Follow the instructions above (and disable Secure Boot).

---

### Post by hu016865 on 2020-02-03
tried :

> # sudo modprobe wl && dmesg | grep wlmodprobe: ERROR: could not insert 'wl': Operation not permitted




---

### Post by hu016865 on 2020-02-03
how can i disable secure boot ?
in bios i dont see and secure boot option ...

---

### Post by CelticWarrior on 2020-02-03
It must be there.

Security menu.

Unless you installed in Legacy mode in which case it's not applicable but then the drivers would load...

---

### Post by hu016865 on 2020-02-13
[FONT=arial]in bios i have no option " secure boot"
with this command : [COLOR=#000000]sudo mokutil --disable-validation
i disable secure boot and wifi work ok now.[/COLOR][/FONT]

---

### Post by him610 on 2020-02-13
> in bios i dont see and secure boot option ...
Sometimes you have to explore every path in your BIOS/UEFI to discover where the option is to disable secure boot.
> The BIOS setup utility is accessed using a key combination before the computer starts the operating system.

Restart the computer.
At the initial SONY screen press the F2 key to enter the BIOS setup utility.
In the BIOS setup utility window, press the ARROW keys to navigate through the menus.
Press the PLUS (+) or MINUS (-) keys to modify the BIOS setup values.
Press the F10 key to exit the BIOS setup utility.
In the Setup Confirmation dialog box, press the ENTER key to save the changes and exit.

---

