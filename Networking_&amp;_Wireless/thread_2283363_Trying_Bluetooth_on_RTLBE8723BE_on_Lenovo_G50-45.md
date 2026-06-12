---
title: "Trying Bluetooth on RTLBE8723BE on Lenovo G50-45"
date: 2015-06-21
forum: Networking &amp; Wireless
---

### Post by kagashe on 2015-06-21
I am trying for Bluetooth on my Laptop.

As per [this question on askubuntu]("http://askubuntu.com/questions/607339/rtl8723be-bluetooth-does-not-work/639185#639185")  I installed rtl8723au_bt module but it did not work.

Meanwhile Pilot6 posted a new ppa today. I added the ppa and installed rtl8723au-bt-dkms linux-firmware.

The result is my Android Phone can see the Ubuntu Laptop in Bluetooth but fails to pair.

The scan on Ubuntu Laptop times out:
```
$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
```

Kamalakar

---

### Post by jeremy31 on 2015-06-21
post the results of ```
lsmod
```

---

### Post by Pilot6 on 2015-06-21
You can install driver from ppa

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8723au-bt-dkms linux-firmware
```

I did not notice you already installed it. Please give output of

lsusb

dmesg | grep -i bluetooth

---

### Post by kagashe on 2015-06-21
Thanks for quick response.

I had compiled rtl8723au_bt which was interfering. I entered the directory rtlwifi_new and uninstalled it:
```
sudo make uninstall
```

Then I reinstalled:
```
sudo apt-get install --reinstall rtl8723au-bt-dkms linux-firmware

```

It works now.

Kamalakar

---

### Post by kagashe on 2015-06-22
> **Pilot6 said:**
> You can install driver from ppa

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8723au-bt-dkms linux-firmware
```

I did not notice you already installed it. Please give output of

lsusb

dmesg | grep -i bluetoothSorry. I had marked the thread solved but there is a problem and I have made it unsolved. There is a conflict between rtlwifi_new and the driver in this ppa so I reinstalled rtlwifi_new but I lost wifi driver, although, Bluetooth worked. I have installed rtlwifi_new again.

```
$ lsusb
Bus 002 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 13d3:5727 IMC Networks 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ dmesg | grep -i bluetooth
[    2.576699] usb 2-1.3: Product: Bluetooth Radio 
[   20.747623] Bluetooth: Core ver 2.19
[   20.747727] Bluetooth: HCI device and connection manager initialized
[   20.747745] Bluetooth: HCI socket layer initialized
[   20.747751] Bluetooth: L2CAP socket layer initialized
[   20.747772] Bluetooth: SCO socket layer initialized
[   20.974096] rtk_btusb: Realtek Bluetooth USB driver ver 0.8
[   20.978200] Bluetooth: hci0: hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   30.566471] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.566481] Bluetooth: BNEP filters: protocol multicast
[   30.566501] Bluetooth: BNEP socket layer initialized
[   30.586375] Bluetooth: RFCOMM TTY layer initialized
[   30.586402] Bluetooth: RFCOMM socket layer initialized
[   30.586422] Bluetooth: RFCOMM ver 1.11
[   73.019108] Bluetooth: hci0 command 0x0c24 tx timeout
[   75.023324] Bluetooth: hci0 command 0x0c52 tx timeout
[  102.613483] Bluetooth: hci0 command 0x0401 tx timeout
[  161.338038] Bluetooth: hci0 command 0x0405 tx timeout
[  218.870443] Bluetooth: hci0 command 0x0408 tx timeout
[  234.899739] Bluetooth: hci0 command 0x0401 tx timeout
[  917.159574] Bluetooth: hci0: hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
```

After uninstalling rtlwifi_new the following line was different:
```
[   20.974096] rtk_btusb: Realtek Bluetooth USB driver ver 0.8

```
I think rtk_btusb is a problem which is coming from rtlwifi_new.

Kamalakar

---

### Post by kagashe on 2015-06-22
Tried following [this post]("http://ubuntuforums.org/showthread.php?t=2243978&page=4&p=13308029#post13308029"). Sometimes it works, sometimes it does not work.

Kamalakar

---

### Post by byhoratiss on 2015-07-17
I believe that I've the same problem as you @kagashe

---

### Post by kagashe on 2015-09-08
It is working on Linux Kernel 3.19 on Ubuntu 14.04.3

Kamalakar

---

