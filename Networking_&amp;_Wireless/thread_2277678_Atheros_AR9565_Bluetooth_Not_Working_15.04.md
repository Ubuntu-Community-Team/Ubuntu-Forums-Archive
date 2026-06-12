---
title: "Atheros AR9565 Bluetooth Not Working 15.04"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by Johnny_Panos on 2015-05-10
Hi, I just installed Ubuntu 15.04 x64 on my laptop, and when I tried to connect a bluetooth device to it, it says that no bluetooth adapters were found. But the wifi part of the card works fine and I'm using it to post this right now. I need the bluetooth to work because we are having a Mario Kart Wii tournament in my science class and the controllers use bluetooth to connect.

---

### Post by jeremy31 on 2015-05-10
if ```
sudo apt-get install linux-firmware
``` doesn't work after a reboot post ```
lsusb; lsmod | grep bluetooth; rfkill list all; dmesg | grep -i bluetooth; dmesg | grep firmware
```

---

### Post by Johnny_Panos on 2015-05-11
It said linux-firmware was already the newest version.

Here is the output of those commands:


```
Bus 003 Device 004: ID 04ca:7046 Lite-On Technology Corp. 
Bus 003 Device 003: ID 04f3:0360 Elan Microelectronics Corp. 
Bus 003 Device 005: ID 0930:0227 Toshiba Corp. 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bluetooth             491520  2 ath3k,btusb
toshiba_bluetooth      16384  0 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    6.961501] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[    6.961748] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[    8.172926] Bluetooth: Core ver 2.20
[    8.172951] Bluetooth: HCI device and connection manager initialized
[    8.172956] Bluetooth: HCI socket layer initialized
[    8.172961] Bluetooth: L2CAP socket layer initialized
[    8.172969] Bluetooth: SCO socket layer initialized
[    8.468521] Bluetooth: Patch file not found ar3k/AthrBT_0x31010100.dfu
[    8.468523] Bluetooth: Loading patch file failed
[    8.468516] usb 3-1.5: Direct firmware load for ar3k/AthrBT_0x31010100.dfu failed with error -2


```

---

### Post by jeremy31 on 2015-05-11
If you have a dual boot with windows with the Atheros bluetooth installed, you can find the AthrBT_0x31010100.dfu in Program Files/Common Files/QCA_Bluetooth.  Then you will need to copy it to /lib/firmware/ar3k/

And you will likely need the ramps file from the same windows directory

---

### Post by edoardo-putti on 2016-01-02
I fixed this looking at the[ wifi wiki]("https://wireless.wiki.kernel.org/en/users/drivers/ath9k/btcoex"), the issue is that the right driver is the ath9k because the wifi chip is both providing wireless and bluetooth witht tha cohexistence option turned on.

To enable the driver cohexistence you must:

1. create a conf file inside*[FONT=courier new] /etc/modprobe.d/[/FONT]* (mine is named ath9k_bluetooth_coexists.conf)
2. add the line [FONT=courier new]options *ath9k btcoex_enable=1* [FONT=arial]to the conf file[/FONT][FONT=arial]
3. run [FONT=courier new]*sudo depmod -a*[FONT=arial]
4. run *[FONT=courier new]sudo update-initramfs[FONT=arial][/FONT][/FONT]*[FONT=courier new][FONT=arial][/FONT][/FONT][/FONT][/FONT][/FONT][FONT=arial]
5. reboot[/FONT]
[/FONT]

---

