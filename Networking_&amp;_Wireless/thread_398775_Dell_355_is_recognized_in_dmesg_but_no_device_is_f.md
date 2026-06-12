---
title: "Dell 355 is recognized in dmesg but no device is found - Feisty Dell XPS M1210"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by tavella on 2007-04-01
Hello,

I have a Dell XPS M1210 and Dell 355 bluetooth card installed. I have tried Kubuntu Feisty, Ubuntu Feisty, and Fedora Core 7 Beta 3 and I cannot get my Bluetooth working. 

dmesg:
[   31.092000] Bluetooth: HCI device and connection manager initialized
[   31.092000] Bluetooth: HCI socket layer initialized
[   31.120000] Bluetooth: L2CAP ver 2.8
[   31.120000] Bluetooth: L2CAP socket layer initialized
[   31.252000] Bluetooth: RFCOMM socket layer initialized
[   31.252000] Bluetooth: RFCOMM TTY layer initialized
[   31.252000] Bluetooth: RFCOMM ver 1.8

hcitool dev:
root@xpsm1210:~# hcitool dev
Devices:
root@xpsm1210:~# 

hciconfig hci0 reset:
root@xpsm1210:~# hciconfig hci0 reset
Can't get device info: No such device
root@xpsm1210:~# 

Any ideas on what might be wrong? There is no fn-F2 sequence on this laptop, only a switch on the side which is set to On since I do have wifi. I have the Intel 3945.

Thank you.

---

### Post by Jonecm on 2007-11-04
I have the exact same problem on my Dell vostro 1500 running gusty (7.10)
Any help would be greatly appreciated.

---

### Post by psygen on 2007-11-04
I also have this problem. My laptop is a Itautec (Fujitsu Siemens) Dual Core 1.66 with Intel Pro Wireless 3945 ABG.

I already installed the linux-restricted-modules. I also have disable the module ipw3945 and used the iwl3945. With these two can not work the wireless interface.

With the ndiswrapper and the driver provided with the Windows XP works, but the laptop freezes frequently.

I am using Gutsy 7.10 final and also tried to Gutsy 7.10 Alternate without success.

If someone knows something, will be of great help.

---

