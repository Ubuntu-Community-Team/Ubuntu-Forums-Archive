---
title: "No wifi adapter found, suggested fixes no help"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by MibunoOokami on 2018-09-04
Hi everyone, I bought a new Lenovo Ideacentre all-in-one AIO 520-24AST and for some reason the wifi adapter is not being detected by Ubuntu. It does work in Window$. I:ve read that this is a common issue with Lenovo computers, but seems like it should be fixable.
 
 
 I followed the work around in [this]("https://www.unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/") website and below is the output from Terminal which indicates there is an error during the process, I’ve marked that in red.
 
 
 ```
mno@mno:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
 [sudo] password for mno:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 build-essential is already the newest version (12.4ubuntu1).
 build-essential set to manually installed.
 linux-headers-4.15.0-33-generic is already the newest version (4.15.0-33.36).
 linux-headers-4.15.0-33-generic set to manually installed.
 The following packages were automatically installed and are no longer required:
   libatkmm-1.6-1v5 libcairomm-1.0-1v5 libgtkmm-3.0-1v5 libpangomm-1.4-1v5
   qml-module-qtgraphicaleffects qml-module-qtquick-dialogs
   qml-module-qtquick-privatewidgets qml-module-qtwebkit
 Use 'sudo apt autoremove' to remove them.
 0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
 mno@mno:~$ sudo sh -c 'echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf'
 mno@mno:~$ cd Downloads/
 mno@mno:~/Downloads$ ls
 0012-r8168-8.046.00.tar.bz2  ubuntu-18.04.1-desktop-amd64.iso
 mno@mno:~/Downloads$ tar xfvj 0012-r8168-8.046.00.tar.bz2  
 r8168-8.046.00/
 r8168-8.046.00/autorun.sh
 r8168-8.046.00/Makefile
 r8168-8.046.00/README
 r8168-8.046.00/src/
 r8168-8.046.00/src/Makefile
 r8168-8.046.00/src/Makefile_linux24x
 r8168-8.046.00/src/r8168.h
 r8168-8.046.00/src/r8168_asf.c
 r8168-8.046.00/src/r8168_asf.h
 r8168-8.046.00/src/r8168_dash.h
 r8168-8.046.00/src/r8168_fiber.h
 r8168-8.046.00/src/r8168_n.c
 r8168-8.046.00/src/r8168_realwow.h
 r8168-8.046.00/src/rtltool.c
 r8168-8.046.00/src/rtltool.h
 r8168-8.046.00/src/rtl_eeprom.c
 r8168-8.046.00/src/rtl_eeprom.h
 mno@mno:~/Downloads$ cd r8168-8.046.00/
 mno@mno:~/Downloads/r8168-8.046.00$ sudo ./autorun.sh
 
 
 Check old driver and unload it.
 rmmod r8169
 Build the module and install
 [COLOR=#ed1c24]Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"[/COLOR]
 [COLOR=#ed1c24]Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"[/COLOR]
 At main.c:160:
 - SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
 - SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
 sign-file: certs/signing_key.pem: No such file or directory
 Backup r8169.ko
 rename r8169.ko to r8169.bak
 DEPMOD 4.15.0-33-generic
 load module r8168
 Updating initramfs. Please wait.
 update-initramfs: Generating /boot/initrd.img-4.15.0-33-generic
 Completed.
 mno@mno:~/Downloads/r8168-8.046.00$ lsmod | grep r8168
 r8168                 528384  0
```
 
 
 Further, I tried the troubleshooting tips [here]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html"), and wireless is indicated, however, I can’t get it to be identified by the system. I’ve installed the restricted extras under Synaptic.
 
 
 It may be worth noting, that under network devices in BIOS, there is a PXE IPV4 Network Stack and a  PXE IPV6 Network Stack listed, both of which are disabled. I haven:t tried experimenting with them as I:m cautious about what I do in BIOS, additionally, since they were already set like that and wifi works in Window$, I’m not sure it’s relevant.
 
 
 I appreciate any help you can offer, to help me get my system to recognise I do have a wifi adapter.

---

### Post by chili555 on 2018-09-04
r8168 is an ethernet driver, not wireless.

Let's first identify the wireless device. Please run and post:```
lspci -nnk | grep 0280 -A3
```

---

### Post by MibunoOokami on 2018-09-04
The output

```
lspci -nnk | grep 0280 -A3
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    Subsystem: Lenovo RTL8821CE 802.11ac PCIe Wireless Network Adapter [17aa:c024]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:36da]

```

> **chili555 said:**
> r8168 is an ethernet driver, not wireless.

Let's first identify the wireless device. Please run and post:```
lspci -nnk | grep 0280 -A3
```

---

### Post by chili555 on 2018-09-04
> Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]There you go! 

And please check here: [https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336)

This must be rtl8821ce night!

---

### Post by MibunoOokami on 2018-09-05
> **chili555 said:**
> There you go! 

And please check here: [https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce/1071336#1071336)

This must be rtl8821ce night!

Hmm, so how'd I go wrong with the troubleshooting tips? Anyway, that post you linked worked. Thanks heaps.

---

