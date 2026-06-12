---
title: "wifi adapter"
date: 2019-10-27
forum: Networking &amp; Wireless
---

### Post by cryxus on 2019-10-27
I have ubuntu 18.04  and my pc is connected to internet through a Mercusys MW300UM wifi adapter. How can I install it on ubuntu?

---

### Post by jeremy31 on 2019-10-27
Post results from terminal for ```
lsusb
``` 
With the device plugged in

---

### Post by cryxus on 2019-10-27
> **jeremy31 said:**
> Post results from terminal for ```
lsusb
``` 
With the device plugged in
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 2c4e:0100  
Bus 003 Device 003: ID 1a2c:4059 China Resource Semico Co., Ltd 
Bus 003 Device 002: ID 04d9:a0d6 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2019-10-27
```
sudo apt install git build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
```

Check results for ```
mokutil --sb-state
```
As Secure Boot(if it is a UEFI install) needs to be disabled in BIOS/UEFI settings for this driver to load
Reboot

---

### Post by cryxus on 2019-10-27
> **jeremy31 said:**
> ```
sudo apt install git build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
```

Check results for ```
mokutil --sb-state
```
As Secure Boot(if it is a UEFI install) needs to be disabled in BIOS/UEFI settings for this driver to load
Reboot

after I enter the code in terminal, it output : E: Unsupported file ./rtl8192eu-linux-driver given on commandline .
I checked and Secure Boot is disabled.

---

### Post by jeremy31 on 2019-10-27
There are 4 commands to run, one line at a time, don't copy and paste all 4 lines at once

---

### Post by cryxus on 2019-10-27
> **jeremy31 said:**
> There are 4 commands to run, one line at a time, don't copy and paste all 4 lines at once

this time the first 4 command lines worked, but when I enter the fifth(mokutil --sb-state) it display : EFI variables are not supported on this system.

---

### Post by jeremy31 on 2019-10-27
Ok, then reboot as your install is a legacy BIOS install, so there is no Secure Boot setting

---

### Post by cryxus on 2019-10-27
> **jeremy31 said:**
> Ok, then reboot as your install is a legacy BIOS install, so there is no Secure Boot setting

Thank you, it worked.

---

