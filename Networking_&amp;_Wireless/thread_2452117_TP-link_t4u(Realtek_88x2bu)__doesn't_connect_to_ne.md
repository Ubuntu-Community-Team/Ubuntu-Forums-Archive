---
title: "TP-link t4u(Realtek 88x2bu)  doesn't connect to network after reboot"
date: 2020-10-17
forum: Networking &amp; Wireless
---

### Post by grisha2020 on 2020-10-17
Hello. I have ubuntu 20.04 and use wi-fi adapter TP-link t4u. I try to install 3 different drivers Realtek 88x2bu ([https://github.com/morrownr/88x2bu;](https://github.com/morrownr/88x2bu;) [https://github.com/RinCat/RTL88x2BU-Linux-Driver;](https://github.com/RinCat/RTL88x2BU-Linux-Driver;) [https://github.com/cilynx/rtl88x2bu](https://github.com/cilynx/rtl88x2bu)). But I have one and the same problem for all these drivers : after reboot of computer Ubuntu can not reconnecting to the network due to authentication error. I have to delete  the network settings (forget the network) and reconnect with reenter the  password. Does anyone know how to solve this problem?

---

### Post by wildmanne39 on 2020-10-17
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by CelticWarrior on 2020-10-17
Welcome.

There's a section here specifically for Networking & Wireless.
Furthermore there's a driver for that chipset already in the Ubuntu repositories:
```
[COLOR=#242729][FONT=Consolas]sudo apt install  rtl8812au-dkms[/FONT][/COLOR]
```

---

### Post by chili555 on 2020-10-17
> **CelticWarrior said:**
> Welcome.

There's a section here specifically for Networking & Wireless.
Furthermore there's a driver for that chipset already in the Ubuntu repositories:
```
[COLOR=#242729][FONT=Consolas]sudo apt install  rtl8812au-dkms[/FONT][/COLOR]
```I doubt that 88x2**bu** covers the same devices as rtl8812**au**. 

Let's get more details about the device and check with modinfo. Please run and post:
```

lsusb
```

---

### Post by grisha2020 on 2020-10-18
1) Yes. rtl8812au didn't work.
2) The details about the device with lsusb
> Bus 001 Device 002: ID 2357:0115 TP-Link 802.11ac NIC

---

### Post by chili555 on 2020-10-18
This is interesting!

```
chili@T440p:~$ modinfo rtl8812au | grep 0115
alias:          usb:v2357p0115d*dc*dsc*dp*ic*isc*ip*in*
chili@T440p:~$ modinfo 88x2bu | grep 0115
alias:          usb:v2357p0115d*dc*dsc*dp*icFFiscFFipFFin*

```In other words, the device in question is claimed by *both* drivers!

Which is loaded?

```
lsmod | grep -e 8812 -e 88x2
sudo dkms status
```I suspect that we'll need to blacklist one or the other.

---

### Post by morrownr on 2020-10-19
That is interesting. I checked the device ID and its shows Realtek 8812bu chipset. I wonder if that 8812au driver that the OP has installed has a bad ID included. It would be good for the OP to tell us where that 8812au driver came from and the solution might be as simple as uninstalling it.

---

### Post by grisha2020 on 2020-10-21
[COLOR=#242729][FONT=Consolas]I have tried rtl8812au but it didn't work with TP-link t4u. So this package is not install in my computer. [/FONT][/COLOR]

---

### Post by chili555 on 2020-10-21
> **grisha2020 said:**
> [COLOR=#242729][FONT=Consolas]I have tried rtl8812au but it didn't work with TP-link t4u. So this package is not install in my computer. [/FONT][/COLOR]What is loaded now?

```
lsusb

```

---

### Post by grisha2020 on 2020-11-10
```
lsmod | grep -e 8812 -e 88x2 

88x2bu               3055616  0
cfg80211              782336  1 88x2bu


```

```

sudo dkms status
rtl88x2bu, 5.8.7.4, 5.8.0-26-generic, x86_64: installed

```

```

lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bc2:ab26 Seagate RSS LLC Backup Plus Slim Portable Drive 1 TB
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0079:0011 DragonRise Inc. Gamepad
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 008: ID 0bc2:3300 Seagate RSS LLC Desktop         
Bus 001 Device 002: ID 2357:0115 TP-Link Archer T4U ver.3
Bus 001 Device 007: ID 0cf3:3002 Qualcomm Atheros Communications AR3011 Bluetooth
Bus 001 Device 006: ID 046d:0805 Logitech, Inc. Webcam C300
Bus 001 Device 005: ID 045e:0780 Microsoft Corp. Comfort Curve Keyboard 3000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub





```

---

### Post by SeijiSensei on 2020-11-10
I have an older T4U with the 8812AU chipset. Running the Driver Manager app in Settings compiled the correct driver from source and installed it. The whole process was handled automatically.

Linux isn't Windows. Downloading drivers is not the best choice of action. Let the Driver Manager do its job.  If it fails, then you can fall back on other methods.

---

### Post by morrownr on 2020-11-10
SeijiSensei, I am going to have to politely disagree with you regarding your above post. Downloading drivers is often the only course of action and, sometimes, even if there is a driver in the repositories, downloading a far better driver may be the best course of action.

Do a test for me: Go to: github.com/morrownr

Download the 8812au driver.

Do some tests, iperf3 perhaps, and record the results with the driver you let the Driver Manager install,

Now install the driver from my github site and do the same tests.

Post the results.

Regards.

---

### Post by SeijiSensei on 2020-11-11
My performance is fine with the Ubuntu-installed driver.  I have a 200 MBit connection to the Internet. If I use speedtest.net, I get about that speed on the laptop.  Ran a 100-person Zoom session from my laptop with this driver installed and had no issues.

We're mostly talking to relative newbies on this forum. For most people, using the built-in Driver Manager is the best choice.

If you think your driver should be bundled with Ubuntu, you'll probably need to convince the Debian administrators.

---

### Post by grisha2020 on 2020-11-11
I have only Nvidia Driver in my Driver Manager. TP link is missing

---

### Post by grisha2020 on 2020-11-29
It work with [https://github.com/EntropicEffect/rtl8822bu](https://github.com/EntropicEffect/rtl8822bu). Problem was solved

---

