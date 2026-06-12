---
title: "Linux Driver for the RealTek RTL8812BU and RTL8822BU Chipsets"
date: 2020-08-03
forum: Networking &amp; Wireless
---

### Post by morrownr on 2020-08-03
[https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)

Driver version 5.8.7.1, 2019-11-19, from Realtek. I have tested the driver on Ubuntu 20.10 (daily, 08-07-20, kernel 5.8), Ubuntu 20.04, Ubuntu 18.04, Linux Mint 20 and Linux Mint 19.3.

Update: DKMS support has been added and tested.

Update: Tested on system with Secure Mode on. DKMS automatically handled the key signing.

Update: Tested hardware:

EDUP WiFi Adapter 1300Mbps USB 3.0 High Gain Wireless Adapter:
 [https://www.amazon.com/gp/product/B07Q56K68T](https://www.amazon.com/gp/product/B07Q56K68T)

Note: The rtl8812bu chipset is used in a lot of usb wifi adapters. The chipset is not bad but there are a lot of poorly made devices using this chipset and other chipsets. The EDUP device listed above is not only economical but it runs cool and appears to be well made. It is best used with a desktop system. 

What is needed? Testing. If you have a device based on the rtl8812bu or rtl8822bu chipsets and have time to test, please do and let me know. I will monitor this thread and Github.

---

### Post by morrownr on 2020-09-09
If anyone has a rtl8812bu adapter that is good quality, economical and would work well with a laptop system, that you would recommend, please let me know. TIA

---

### Post by morrownr on 2020-09-13
[https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)

Linux Driver for the RealTek RTL8812BU and RTL8822BU Chipsets.
Driver Version: 5.8.7.2.36899.20200819

Update: Driver version updated to a very recent release.

Update: Monitor Mode tested.

Update: DKMS installation appears to be working well.

---

### Post by dshah on 2020-09-14
@morrownr do you think you could help in this or even if its related?
[https://ubuntuforums.org/showthread.php?t=2450473](https://ubuntuforums.org/showthread.php?t=2450473)

---

### Post by mikehallettuk on 2020-12-19
Thanks this all worked well on Ubuntu 20, an Odroid N2+, with a USB Wi-Fi Adapter CUDY WU1300.

---

### Post by morrownr on 2020-12-22
Glad it worked for you. 

If anyone else is searching in the future, my github site has drivers for all commonly used Realtek USB wifi adapters:

https//github.com/morrownr

rtl8812bu
rtl8822bu
rtl8812au
rtl8814au
rtl8821cu
rtl8811cu
rtl8831au
rtl8821au
rtl8811au

---

### Post by dougbennett on 2021-01-07
Good morning. My wifi adapter has caused [COLOR=#000000]Ubuntu 20.04.1 LTS to use rtl88122au. But it doesn't work to make the adapter function. I have the installation disc and did my best to follow instructions, but there is little that is still applicable. I am not good with installation problems or solving any problem with Ubuntu yet. I was an expert in DOS and windows, but this is a whole new world.  I'm going to your link now. [/COLOR]

---

### Post by morrownr on 2021-01-07
> **dougbennett said:**
> Good morning. My wifi adapter has caused [COLOR=#000000]Ubuntu 20.04.1 LTS to use rtl88122au. But it doesn't work to make the adapter function. I have the installation disc and did my best to follow instructions, but there is little that is still applicable. I am not good with installation problems or solving any problem with Ubuntu yet. I was an expert in DOS and windows, but this is a whole new world.  I'm going to your link now. [/COLOR]

Sir, it would probably have been better if you had opened a new thread. In fact, can I get you to do that after opening a terminal (Ctrl+Alt+t) and running the following command:

```
$ lsusb
```

Please post the results.

FYI: Welcome to Linux. The first thing that we have to know to help you is exactly which WiFi chipset is in your adapter.

---

### Post by Andrew F in Australia on 2021-05-19
Confiriming this worked on an rtl8812bu chip in a 1200AC wifi adapter on ubuntu 20.10 as a non-LTS release 19/5/2021.

Install instructions below

```
 horace@horace:~$ uname -a
Linux horace 5.8.0-53-generic #60-Ubuntu SMP Thu May 6 07:46:32 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

lsusb
Bus 001 Device 002: ID 0bda:b812 Realtek Semiconductor Corp. RTL88x2bu [AC1200 Techkey]

```
Install commands used for those that need them - basically, there's a self-installer in the repository:
```
sudo apt update
sudo install -y dkms git
sudo apt install -y dkms git
mkdir src
cd src
git clone https://github.com/morrownr/88x2bu.git
cd 88x2bu/
sudo ./install-driver.sh


```

This worked where a lot of other third party manufacturer drivers (including the one  that came with the WiFi adapter) did not.

I'd spent about 2 hours trying before I found this which linked your github:

[https://askubuntu.com/questions/1079377/how-do-i-install-drivers-for-realtek-rtl8812bu](https://askubuntu.com/questions/1079377/how-do-i-install-drivers-for-realtek-rtl8812bu)

Thanks again for your time and expertise putting it together.

---

### Post by Andrew F in Australia on 2021-05-20
Hi @morrownr,

Just letting you know I've had issues with both your 8814 driver and the aircrack 8814 driver on this machine.

They both recognised this as a wifi dongle, but only went to 2.4GHz and did not recognise local networks.

Please see below.

Is there something else you need for faultfinding?  The city's in COVID lockdown here so time is plentiful.

Regards,

A

iwconfig```
lo        no wireless extensions.

enp4s0    no wireless extensions.

wlp8s0    IEEE 802.11  ESSID:"not-you-5GHz"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: A0:63:91:47:91:C8   
          Bit Rate=195.1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:75   Missed beacon:0

wlx1cbfcef982ea  unassociated  Nickname:"WIFI@RTL8814AU"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

uname -a ```
Linux horace-desktop 5.8.0-59-generic #66~20.04.1-Ubuntu SMP Thu Jun 17 11:14:10 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

sudo lshw -C network```
[sudo] password for horace: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 06
       serial: f8:1a:67:00:66:f1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-59-generic duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:30 ioport:e000(size=256) memory:fc500000-fc500fff memory:ea100000-ea103fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:fc300000-fc30ffff memory:fc310000-fc313fff
  *-network
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlp8s0
       version: 78
       serial: e8:84:a5:f5:81:a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-59-generic firmware=36.77d01142.0 8265-36.ucode ip=192.168.2.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:55 memory:fc200000-fc201fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7.3
       logical name: wlx1cbfcef982ea
       serial: 1c:bf:ce:f9:82:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8814au driverversion=5.8.0-59-generic multicast=yes wireless=unassociated
```

lsusb```
lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 008: ID 0e8f:00a8 GreenAsia Inc. 
Bus 001 Device 007: ID 0bda:8813 Realtek Semiconductor Corp. RTL8814AU 802.11a/b/g/n/ac Wireless Adapter
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 004: ID 0483:5750 STMicroelectronics LED badge -- mini LED display -- 11x44
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 005: ID 26ce:01a2 ASRock LED Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

