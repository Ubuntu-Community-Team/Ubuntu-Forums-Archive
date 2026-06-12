---
title: "Dell 5537 not showing wireless connections ubuntu 12.04 LTS"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by thenewone2 on 2014-07-08
tried :
```

sudo apt-get update 
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
sudo modprobe b43

```

its a dual boot with wireless working well in windows 

here is the output of the wireless script [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) :

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux happy-lappy 3.8.0-42-generic #63~precise1-Ubuntu SMP Fri Jul 4 21:16:26 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Device [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Device [8086:4462]
03:00.0 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI Device [1002:6660]

##### lsusb #####

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0781:5572 SanDisk Corp. 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0c45:64ad Microdia 

##### PCMCIA Card Info #####


##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #####


##### iw reg get #####


##### interfaces #####

auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####


##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC ADDRESS >

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####


##### iwlist channel #####


##### modinfo #####


##### modules #####


lp
rtc

##### blacklist #####
```



wireless not working sice installed :(

---

### Post by slooksterpsv on 2014-07-10
Looks like it may need to be compiled and installed that way:
[http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63)
Here's the link for intel source
[http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm)

You can try a few things first though such as:
sudo modprobe iwlwifi

You should also check that your BIOS is up to date and that you're not able to disable wireless in BIOS. You may need to edit grub and add one or both of these lines: 
acpi=off 
noapic

You'd add them to where it says quiet splash --

---

