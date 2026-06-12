---
title: "mediatek wifi doesn't load on ubuntu server for rpi after upgrade"
date: 2022-01-02
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2022-01-02
I setup ubuntu-server 20.04-lts on a raspberry pi4.
Then I upgraded to ubuntu-server 21.10 and my wifi is broken.

USB doesn't seem to be loading the wifi driver anymore.
This all dmesg says:
```
[ 1857.974972] usb 2-4: new SuperSpeed USB device number 5 using xhci_hcd
[ 1857.999529] usb 2-4: New USB device found, idVendor=0e8d, idProduct=7612, bcdDevice= 1.00
[ 1857.999536] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1857.999539] usb 2-4: Product: Wireless 
[ 1857.999542] usb 2-4: Manufacturer: MediaTek Inc.
[ 1857.999544] usb 2-4: SerialNumber: 000000000
```

This a working system:
```
[ 1857.974972] usb 2-4: new SuperSpeed USB device number 5 using xhci_hcd
[ 1857.999529] usb 2-4: New USB device found, idVendor=0e8d, idProduct=7612, bcdDevice= 1.00
[ 1857.999536] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1857.999539] usb 2-4: Product: Wireless 
[ 1857.999542] usb 2-4: Manufacturer: MediaTek Inc.
[ 1857.999544] usb 2-4: SerialNumber: 000000000
[ 1858.189120] usb 2-4: reset SuperSpeed USB device number 5 using xhci_hcd
[ 1858.214059] mt76x2u 2-4:1.0: ASIC revision: 76120044
[ 1858.320504] mt76x2u 2-4:1.0: ROM patch build: 20141115060606a
[ 1858.512593] mt76x2u 2-4:1.0: Firmware Version: 0.0.00
[ 1858.512597] mt76x2u 2-4:1.0: Build: 1
[ 1858.512598] mt76x2u 2-4:1.0: Build Time: 201507311614____
[ 1859.794770] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[ 1859.795637] usbcore: registered new interface driver mt76x2u
[ 1859.809763] mt76x2u 2-4:1.0 wlx00c0caaa9c2b: renamed from wlan0
```

Maybe the easiest thing is to start over unless it is an easy fix.

---

### Post by bjlockie on 2022-01-02
Tried a reinstall and it has the same error -(

---

### Post by chili555 on 2022-01-02
Please run and post:

```
modinfo mt76x2u | grep 7612
sudo dmesg | grep mt76
cat /etc/netplan/*.yaml
```

---

### Post by bjlockie on 2022-01-04
Grrr,

> lsmod | grep mt
Nothing. :-(

Next question is ho do I get the drivers?
I installed:
[https://cdimage.ubuntu.com/releases/21.10/release/ubuntu-21.10-preinstalled-server-arm64+raspi.img.xz?_ga=2.70338256.170504886.1641333062-1774966744.1639856566](https://cdimage.ubuntu.com/releases/21.10/release/ubuntu-21.10-preinstalled-server-arm64+raspi.img.xz?_ga=2.70338256.170504886.1641333062-1774966744.1639856566)

---

### Post by chili555 on 2022-01-04
The other items I requested likely offer some clues. Please run and post them.

---

### Post by jeremy31 on 2022-01-04
I would like to see results for ```
modprobe -c | grep 7612; dpkg -l | grep linux-modules-extra-$(uname -r)
```

---

### Post by chili555 on 2022-01-04
> linux-modules-extraBingo.

---

### Post by bjlockie on 2022-01-05
> **chili555 said:**
> 
```
modinfo mt76x2u | grep 7612

```

modinfo: ERROR: Module mt76x2u not found.

> **chili555 said:**
> 
```

sudo dmesg | grep mt76

```
Nothing

> **chili555 said:**
> 
```

cat /etc/netplan/*.yaml
```

01-netcfg.yaml
01-network-manager-all.yaml

```
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
  version: 2
  renderer: networkd
  ethernets:
     eth0:
        dhcp4: true
        optional: true
  wifis:
     wlan1:
        dhcp4: true
        access-points:
          "xxx":
             password: "xxx"

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

I tried deleting the 2nd file and it won't boot.
I'll try deleting the 1st file.

---

### Post by chili555 on 2022-01-06
> # Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManagerNetwork Manager on a server? Let's check: ```
sudo service NetworkManager status
```

Is linux-modules-extra installed as Jeremy suspects isn't?```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status

```
> I tried deleting the 2nd file and it won't boot.I suspect that it *will *boot but will take a few minutes as the system tries to initiate a connection to the non-existent eth0 and wlan1. Please do not amend or delete anything else until we diagnose and fix a few things here. It's difficult to hit an ever moving target.

---

### Post by bjlockie on 2022-01-06
> **chili555 said:**
> Network Manager on a server? Let's check: ```
sudo service NetworkManager status
```

Is linux-modules-extra installed as Jeremy suspects isn't?```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status

```


I had to take a picture this time:

---

### Post by chili555 on 2022-01-06
Ahhh! My favorite kind of problem; the more data points we collect, the more confusing and less helpful it is.

Let's dig deeper. If you have any connectivity; i.e. ethernet, then do:

```
sudo apt update
sudo apt install linux-modules-extra-$(uname -r) linux-generic wpasupplicant net-tools
sudo dmesg | grep wlan
```If some of the packages are already installed, that's fine; skip them and continue.

---

### Post by bjlockie on 2022-01-07
I wanted to do it by wireless only but I did plug in an ethernet cable.
I have a suspicion that this wasn't the SD card with the vanilla install of ubuntu-server.

I thought after that I could have used the command tee to capture the output instead of taking pictures.
I apologize for the second picture being blurry.

[ATTACH=CONFIG]289758[/ATTACH][ATTACH=CONFIG]289757[/ATTACH]

I have wireless now. :-)

---

### Post by chili555 on 2022-01-07
> I have wireless nowAwesome! Please use thread tools at the top to mark Solved.

---

