---
title: "USB WLAN TL-WN722N not working with Ubuntu xenial"
date: 2017-08-26
forum: Networking &amp; Wireless
---

### Post by zubrowa on 2017-08-26
Hi,

I am trying to install an USB WLAN TL-WN722N v1.10 dongle in my Ubuntu xanial system.

When plugged in, the device is recognized:

```

dmesg

[ 1925.342043] usb 1-5: new high-speed USB device number 7 using xhci_hcd
[ 1925.363464] usb 1-5: New USB device found, idVendor=0cf3, idProduct=9271
[ 1925.363491] usb 1-5: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[ 1925.363511] usb 1-5: Product: USB2.0 WLAN
[ 1925.363525] usb 1-5: Manufacturer: ATHEROS
[ 1925.363539] usb 1-5: SerialNumber: 12345
```

and
```

lsusb

Bus 001 Device 008: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
```

However, the device does not appear in the output of iwconfig.

My kernel is 
```

uname -a
Linux localhost 3.8.11 #1 SMP Thu Jul 27 00:04:59 PDT 2017 x86_64 x86_64 x86_64 GNU/Linux
```

I am running Ubuntu on my Acer chromebook inside Android OS, that's why I cannot upgrade the kernel to a recent version.

My impression is that the module ath9k_htc is not loaded by the kernel.

Do you have any ideas how I can fix the problem?

Thank you.

Chris

---

### Post by praseodym on 2017-08-27
Load it automatically during boot-up:
```

echo ath9k_htc | sudo tee -a /etc/modules
```

---

### Post by chili555 on 2017-08-27
Does the version of ath9k_htc in your kernel version cover the exact device?```
modinfo ath9k_htc | grep 9271
```If so, perhaps the firmware is missing; check:```
dmesg | grep ath
```

---

### Post by praseodym on 2017-08-28
Maybe the driver package is missing?!
```

dpkg -l linux-image-* | grep ii
```

---

### Post by jeremy31 on 2017-08-28
How is it possible that Xenial is using an EOL 3.8 kernel?

You may need to use backports if possible as the last update from over a year ago should work if they still support kernels that old

One thing might work
```
sudo modprobe ath9k_htc
```
```
sudo -i
```
```
echo '0cf3 9271' > /sys/bus/usb/drivers/ath9k_htc/new_id
```
```
exit
```

Are you using crouton?

---

### Post by QIII on 2017-08-28
Could you please post the results of

```
lsb_release -a 
```

---

### Post by zubrowa on 2017-09-02
> **praseodym said:**
> Load it automatically during boot-up:
```

echo ath9k_htc | sudo tee -a /etc/modules
```

I used your command and ath9_htc was added into /etc/modules. However, even if I restart the system the USB dongle is still not working.

---

### Post by zubrowa on 2017-09-02
> **chili555 said:**
> Does the version of ath9k_htc in your kernel version cover the exact device?```
modinfo ath9k_htc | grep 9271
```If so, perhaps the firmware is missing; check:```
dmesg | grep ath
```

I get 
```
sudo modinfo ath9k_htc | grep 9271
modinfo: ERROR: Module ath9k_htc not found.
```

and 

```

dmesg | grep ath

[    0.099933]  [<ffffffff8aa3327e>] warn_slowpath_fmt+0x65/0x90
[    0.790867] Unsafe core_pattern used with suid_dumpable=2. Pipe handler or fully qualified core dump path required.
[    1.300810] usbcore: registered new interface driver ath3k
[    7.519094] ath: phy0: ASPM enabled: 0x43
[    7.519107] ath: EEPROM regdomain: 0x6c
[    7.519109] ath: EEPROM indicates we should expect a direct regpair map
[    7.519113] ath: Country alpha2 being used: 00
[    7.519114] ath: Regpair used: 0x6c
[    7.523242] ieee80211 phy0: Selected rate control algorithm 'ath9k_btcoex_rate_cotnrol'

```

---

### Post by zubrowa on 2017-09-02
> **praseodym said:**
> Maybe the driver package is missing?!
```

dpkg -l linux-image-* | grep ii
```

```

sudo dpkg -l linux-image-* | grep ii
dpkg-query: no packages found matching linux-image-*

```

---

### Post by zubrowa on 2017-09-02
> **jeremy31 said:**
> How is it possible that Xenial is using an EOL 3.8 kernel?

You may need to use backports if possible as the last update from over a year ago should work if they still support kernels that old

One thing might work
```
sudo modprobe ath9k_htc
```
```
sudo -i
```
```
echo '0cf3 9271' > /sys/bus/usb/drivers/ath9k_htc/new_id
```
```
exit
```

Are you using crouton?

Yes I am using crouton.

I think there is a problem with the modules:
```

sudo modprobe ath9k_htc
modprobe: FATAL: Module ath9k_htc not found in directory /lib/modules/3.8.11

```

---

### Post by chili555 on 2017-09-02
> I think there is a problem with the modules:
Code:
sudo modprobe ath9k_htc
modprobe: FATAL: Module ath9k_htc not found in directory /lib/modules/3.8.11Correct. 

The driver ath9k_htc has been around for many kernel version before 3.8.

Where id you install kernel version 3.8.11? Was there an 'extras' package that you forgot to install?

---

### Post by praseodym on 2017-09-02
Kernel 3.8?!?!?! Edit: With Xenial?!?!!?eleven!

Please run via LAN connection:
```

sudo apt-get install linux-generic linux-image-generic linux-headers-generic build-essential dkms
```

---

### Post by zubrowa on 2017-09-02
> **chili555 said:**
> Correct. 

The driver ath9k_htc has been around for many kernel version before 3.8.

Where id you install kernel version 3.8.11? Was there an 'extras' package that you forgot to install?

I am runing crouton on my Acer Chromebook which is run inside Chrome OS. 

With crouton I have to use the same kernel as from Chrome OS which is 3.8.11 and cannot be upgraded.

Is it possible to load the module ath9k_htc at run time without modifying the kernel?

---

### Post by jeremy31 on 2017-09-04
The problem is that the Chrome OS uses a highly customized kernel similar to what they use in Android phones to make the size of the kernel and modules as small as possible.
Can you not use the wifi that is in the Chromebook to connect using Ubuntu?

---

