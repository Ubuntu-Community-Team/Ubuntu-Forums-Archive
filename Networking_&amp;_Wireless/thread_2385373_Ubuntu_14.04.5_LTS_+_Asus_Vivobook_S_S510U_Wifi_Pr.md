---
title: "Ubuntu 14.04.5 LTS + Asus Vivobook S S510U Wifi Problems"
date: 2018-02-19
forum: Networking &amp; Wireless
---

### Post by arthurcanal on 2018-02-19
I have started a new project for a company and to have all the supported libraries for development I need to be running Ubuntu 14.04.5 LTS.

Everything is working perfectly except for my Wifi.  I can plug in a USB wifi card and it works fine but it does not seem to pick up my internal one.

I am guessing that the Ubuntu 14.04.5 LTS does not come with the correct wifi drivers out of the box.  I have tried a few things online but with no success.

Here is some output from a few commands that might be useful.

[B]lspci

[/B]```
00:00.0 Host bridge: Intel Corporation Device 5914 (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Device 5917 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Device 1903 (rev 08)
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
00:15.0 Signal processing controller: Intel Corporation Device 9d60 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Device 9d61 (rev 21)
00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
00:17.0 SATA controller: Intel Corporation Device 9d03 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Device 9d15 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Device 9d27 (rev 21)
00:1e.2 Signal processing controller: Intel Corporation Device 9d29 (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
02:00.0 Network controller: Intel Corporation Device 24fd (rev 78)

```

[B]lshw -C network

[/B]```
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ef000000-ef001fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 50:46:5d:4c:5a:e6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-112-generic firmware=0.29 ip=192.168.0.110 link=yes multicast=yes wireless=IEEE 802.11abgn

```

You can see above that the system is aware of the card but not sure which drivers are correct.

I have also tried installing broadcom drivers to see if that would help

```

sudo apt install bcmwl-kernel-source
sudo modprobe wl

```

 I can keep using the USB wifi card but it would be nice to get the Intel integrated chip working.  Any help would be appreciated!  Let me know if more info would help or if there is another thread that has solved the same issue.

Thanks

---

### Post by jeremy31 on 2018-02-19
Try this in terminal with the USB connected
```
sudo apt-get install build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.14-rc2/backports-4.14-rc2-1.tar.gz
tar -zxvf backports-4.14-rc2-1.tar.gz
cd backports-4.14-rc2-1
make defconfig-wifi
make
sudo make install
```

Reboot and post results for ```
dmesg | grep iwl
```

---

### Post by arthurcanal on 2018-02-19
Thanks for your help here!


```

[    1.905755] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    1.909851] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-34.ucode failed with error -2
[    1.909863] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-33.ucode failed with error -2
[    1.910140] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-32.ucode failed with error -2
[    1.910385] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-31.ucode failed with error -2
[    1.910408] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-30.ucode failed with error -2
[    1.910427] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-29.ucode failed with error -2
[    1.910435] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-28.ucode failed with error -2
[    1.910458] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-27.ucode failed with error -2
[    1.910465] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[    1.910473] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[    1.910480] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    1.910488] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    1.910495] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-22.ucode failed with error -2
[    1.910496] iwlwifi 0000:02:00.0: no suitable firmware found!
[    1.910498] iwlwifi 0000:02:00.0: minimum version required: iwlwifi-8265-22
[    1.910499] iwlwifi 0000:02:00.0: maximum version supported: iwlwifi-8265-34
[    1.910500] iwlwifi 0000:02:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git

```

---

### Post by jeremy31 on 2018-02-19
Ok, now do
```
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-22.ucode
```
Reboot without the USB wifi and see if it works

If it does work, you will have to run some commands after a kernel update, when wifi quits working, do
```
cd backports-4.14-rc2-1
make clean
make defconfig-wifi
make
sudo make install
```
Reboot

---

### Post by arthurcanal on 2018-02-19
That worked perfectly!  Thanks so much!  Life saver.

---

