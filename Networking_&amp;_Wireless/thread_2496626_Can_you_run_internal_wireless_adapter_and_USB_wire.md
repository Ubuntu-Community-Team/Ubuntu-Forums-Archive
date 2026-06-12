---
title: "Can you run internal wireless adapter and USB wireless at the same time?"
date: 2024-04-05
forum: Networking &amp; Wireless
---

### Post by vw16v on 2024-04-05
Hello, I recently bought a Cudy WU650 USB wireless adapter. I plan on trying to install the Linux drivers from the manufactures website here:

[https://www.cudy.com/wu650_software_download](https://www.cudy.com/wu650_software_download)

My main question / concern is if this will cause any conflict with my currently internal wireless adapter on my laptop that is working good.

Here's my current wifi info.
```
sudo lshw -class network-network                 
       description: Wireless interface
       product: Wi-Fi 6 AX201
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 20

```

Also, Per the link above I'm assuming I should probably just run this to attempt the install?
```
sudo ./install-driver.sh
```
Or do I need to run the MakeFile first? 
Here's a list of all the files
/Downloads/WU650_Linux_Driver$ ls
8821cu.conf   core       docs             halmac.mk          Kconfig   os_dep     remove-driver.sh   save-log.sh
ARM64_RPI.sh  debian     edit-options.sh  include            LICENSE   platform   rtl8821c.mk        supported-device-IDs
ARM_RPI.sh    dkms.conf  hal              install-driver.sh  Makefile  README.md  rtw88_8821cu.conf

I don't think I'll need to run > sudo Makefile 
Is that correct?

I'm just slightly confused because it also list this information the README.md.
I"m not sure if I should just run this apt install below or actually try to install the drivers via the .sh file mentioned above? I'm assuming it's the same thing and might be better to install online with the command below for the latest drivers?
I appreciate any information or experience running internal Wifi on laptop in conjunction with a USB Wifi adapter! I want to tread careful and hope for the best. 

### Installation Steps
- Option for Debian, Kali, and Raspberry Pi Desktop (x86)

```
sudo apt install -y linux-headers-$(uname -r) build-essential bc dkms git libelf-dev

---

### Post by vw16v on 2024-04-08
Nevermind, I got this figured out. You can run two wireless adapters at once. You can also disable them individually to test the speeds of internal vs USB wifi.

---

