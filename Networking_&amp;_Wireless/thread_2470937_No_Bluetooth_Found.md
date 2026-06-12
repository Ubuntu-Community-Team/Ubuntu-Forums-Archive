---
title: "No Bluetooth Found"
date: 2022-01-17
forum: Networking &amp; Wireless
---

### Post by paul_b4 on 2022-01-17
Hello,

I have a Mediatek Bluetooth adapter and am using Ubuntu 20.04.3, and Settings tells me "No Bluetooth Found."  Sadly I have not been able to find any solution for this in the forums.  Bluetooth is however working in my Windows OS, though it crashes with annoying frequency.  I also installed Bluetooth Manager, but to no avail.  It tells me, "Connection to BlueZ failed.  BlueZ daemon is not running, blueman-manager cannot continue.  This probably means that there were no bluetooth adapters detected or Bluetooth daemon was not started."  Could anyone help me with this?

Thank you,
Paul

---

### Post by jeremy31 on 2022-01-17
Post results from terminal for ```
lsusb; lspci -nnk | grep -iA3 net; hciconfig -a; dmesg | egrep -i 'blue|firm'
```

---

### Post by paul_b4 on 2022-01-18
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 0489:e080 Foxconn / Hon Hai BT
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e084]
    Kernel driver in use: mt76x0e
    Kernel modules: mt76x0e
[    0.090118] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    1.601461] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f00)
[   17.478031] mt76x0e 0000:03:00.0: Firmware Version: 1.0.07
[  203.760105] Bluetooth: Core ver 2.22
[  203.760144] Bluetooth: HCI device and connection manager initialized
[  203.760149] Bluetooth: HCI socket layer initialized
[  203.760151] Bluetooth: L2CAP socket layer initialized
[  203.760155] Bluetooth: SCO socket layer initialized

---

### Post by jeremy31 on 2022-01-19
Please post results for ```
sudo awk -vRS= '/Vendor=0489/{print $0,"\n"}' /sys/kernel/debug/usb/devices; sudo dmesg | egrep -iA5 0489
```

---

### Post by paul_b4 on 2022-01-20
T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  7 Spd=480  MxCh= 0
D:  Ver= 2.01 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e080 Rev= 1.00
S:  Manufacturer=MediaTek
S:  Product=BT
S:  SerialNumber=1.0
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=450mA
A:  FirstIf#= 0 IfCount= 2 Cls=ff(vend.) Sub=ff Prot=ff
I:* If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=125us
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms
I:  If#= 1 Alt= 6 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  64 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  64 Ivl=1ms 

[    4.304919] usb 1-6: New USB device found, idVendor=0489, idProduct=e080, bcdDevice= 1.00
[    4.304932] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.304938] usb 1-6: Product: BT
[    4.304943] usb 1-6: Manufacturer: MediaTek
[    4.304947] usb 1-6: SerialNumber: 1.0
[    4.433683] usb 1-8: new high-speed USB device number 8 using xhci_hcd

---

### Post by jeremy31 on 2022-01-20
I forgot about ```
uname -r
```

---

### Post by paul_b4 on 2022-01-21
5.13.0-27-generic

---

### Post by jeremy31 on 2022-01-21
Check ```
mokutil --sb-state
```
As Secure Boot needs to be disabled for the new module to load, if mokutil is not installed, you are using BIOS mode, then in terminal do
```
sudo apt install git dkms
git clone https://github.com/jeremyb31/bluetooth-5.13.git
cd bluetooth-5.13
make
sudo mv /lib/modules/5.13.0-27-generic/kernel/drivers/bluetooth/btusb.ko /lib/modules/5.13.0-27-generic/kernel/drivers/bluetooth/btusb.ko.bak
sudo cp btusb.ko /lib/modules/5.13.0-27-generic/kernel/drivers/bluetooth/
```

Reboot and test, if it works I can make it use dkms so it will auto update for kernel updates

---

### Post by paul_b4 on 2022-01-22
Sadly it didn't work...  By the way Secure Boot had already been  disabled and mokutil was already installed.  Below is what I got in the  terminal, if it is of any help:
```

paul@paul-X555LAB:~$ mokutil --sb-state EFI variables are not supported on this system
 paul@paul-X555LAB:~$ sudo apt install git dkms
 [sudo] password for paul:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 dkms is already the newest version (2.8.1-5ubuntu2).
 dkms set to manually installed.
 The following packages were automatically installed and are no longer required:
   chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi
   libgstreamer-plugins-bad1.0-0 libva-wayland2 linux-headers-5.11.0-43-generic
   linux-hwe-5.11-headers-5.11.0-43 linux-image-5.11.0-43-generic
   linux-modules-5.11.0-43-generic linux-modules-extra-5.11.0-43-generic
 Use 'sudo apt autoremove' to remove them.
 The following additional packages will be installed:
   git-man liberror-perl
 Suggested packages:
   git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk
   gitweb git-cvs git-mediawiki git-svn
 The following NEW packages will be installed:
   git git-man liberror-perl
 0 upgraded, 3 newly installed, 0 to remove and 10 not upgraded.
 Need to get 5.465 kB of archives.
 After this operation, 38,4 MB of additional disk space will be used.
 Do you want to continue? [Y/n] y
 Get:1 http://it.archive.ubuntu.com/ubuntu focal/main amd64 liberror-perl all 0.17029-1 [26,5 kB]
 Get:2 http://it.archive.ubuntu.com/ubuntu focal-updates/main amd64 git-man all 1:2.25.1-1ubuntu3.2 [884 kB]
 Get:3 http://it.archive.ubuntu.com/ubuntu focal-updates/main amd64 git amd64 1:2.25.1-1ubuntu3.2 [4.554 kB]
 Fetched 5.465 kB in 1s (5.502 kB/s)
 Selecting previously unselected package liberror-perl.
 (Reading database ... 226213 files and directories currently installed.)
 Preparing to unpack .../liberror-perl_0.17029-1_all.deb ...
 Unpacking liberror-perl (0.17029-1) ...
 Selecting previously unselected package git-man.
 Preparing to unpack .../git-man_1%3a2.25.1-1ubuntu3.2_all.deb ...
 Unpacking git-man (1:2.25.1-1ubuntu3.2) ...
 Selecting previously unselected package git.
 Preparing to unpack .../git_1%3a2.25.1-1ubuntu3.2_amd64.deb ...
 Unpacking git (1:2.25.1-1ubuntu3.2) ...
 Setting up liberror-perl (0.17029-1) ...
 Setting up git-man (1:2.25.1-1ubuntu3.2) ...
 Setting up git (1:2.25.1-1ubuntu3.2) ...
 Processing triggers for man-db (2.9.1-1) ...
 paul@paul-X555LAB:~$ git clone https://github.com/jeremyb31/bluetooth-5.13.git
 Cloning into 'bluetooth-5.13'...
 remote: Enumerating objects: 54, done.
 remote: Counting objects: 100% (54/54), done.
 remote: Compressing objects: 100% (50/50), done.
 remote: Total 54 (delta 6), reused 46 (delta 3), pack-reused 0
 Unpacking objects: 100% (54/54), 199.79 KiB | 878.00 KiB/s, done.
 paul@paul-X555LAB:~$ cd bluetooth-5.13
 paul@paul-X555LAB:~/bluetooth-5.13$ make
 make -C /lib/modules/5.13.0-27-generic/build M=/home/paul/bluetooth-5.13 modules
 make[1]: Entering directory '/usr/src/linux-headers-5.13.0-27-generic'
   CC [M]  /home/paul/bluetooth-5.13/btusb.o
 /home/paul/bluetooth-5.13/btusb.c: In function ‘btusb_setup_intel_new’:
 /home/paul/bluetooth-5.13/btusb.c:2959:9: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
  2959 |   match = usb_match_id(data->intf, msft_rej_table);
       |         ^
   CC [M]  /home/paul/bluetooth-5.13/ath3k.o
   MODPOST /home/paul/bluetooth-5.13/Module.symvers
   CC [M]  /home/paul/bluetooth-5.13/ath3k.mod.o
   LD [M]  /home/paul/bluetooth-5.13/ath3k.ko
   BTF [M] /home/paul/bluetooth-5.13/ath3k.ko
 Skipping BTF generation for /home/paul/bluetooth-5.13/ath3k.ko due to unavailability of vmlinux
   CC [M]  /home/paul/bluetooth-5.13/btusb.mod.o
   LD [M]  /home/paul/bluetooth-5.13/btusb.ko
   BTF [M] /home/paul/bluetooth-5.13/btusb.ko
 Skipping BTF generation for /home/paul/bluetooth-5.13/btusb.ko due to unavailability of vmlinux
 make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-27-generic'
 paul@paul-X555LAB:~/bluetooth-5.13$ sudo mv /lib/modules/5.13.0-27-generic/kernel/drivers/bluetooth/btusb.ko /lib/modules/5.13.0-27-generic/kernel/drivers/bluetooth/btusb.ko.bak
 paul@paul-X555LAB:~/bluetooth-5.13$ sudo cp btusb.ko /lib/modules/5.13.0-27-generic/kernel/drivers/bluetooth/
 paul@paul-X555LAB:~/bluetooth-5.13$ 
  
```

---

### Post by jeremy31 on 2022-01-22
Did you reboot after?  Post result for ```
modinfo btusb
```

---

### Post by paul_b4 on 2022-01-23
Yes I did reboot after.  Results of  modinfo btusb:

filename:       /lib/modules/5.13.0-27-generic/kernel/drivers/bluetooth/btusb.ko
license:        GPL
version:        0.9
description:    Generic Bluetooth USB driver ver 0.9
author:         Marcel Holtmann <marcel@holtmann.org>
firmware:       mediatek/mt7668pr2h.bin
firmware:       mediatek/mt7663pr2h.bin
srcversion:     A69BAF66E0ECCF39796CCD2
alias:          usb:v8087p0A5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v413Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v13D3p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v050Dp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0B05p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0A5Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v04CAp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0489p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0BB4p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v105Bp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v19FFp0239d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v413Cp8197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C10p0000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDBp1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BFp030Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp3800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8281d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5Cp21E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE080d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp763Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v*p*d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v*p*d*dcE0dsc01dp04ic*isc*ip*in*
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
alias:          of:N*T*Cusb4ca,301aC*
alias:          of:N*T*Cusb4ca,301a
alias:          of:N*T*Cusbcf3,e300C*
alias:          of:N*T*Cusbcf3,e300
alias:          of:N*T*Cusb1286,204eC*
alias:          of:N*T*Cusb1286,204e
depends:        btbcm,bluetooth,btrtl,btintel
retpoline:      Y
name:           btusb
vermagic:       5.13.0-27-generic SMP mod_unload modversions 
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           enable_autosuspend:Enable USB autosuspend by default (bool)
parm:           reset:Send HCI reset command on initialization (bool)

---

### Post by jeremy31 on 2022-01-23
Post results for ```
dmesg | egrep -i 'blue|firm|hci'; hciconfig -a; rfkill list; sudo awk -vRS= '/Vendor=0489/{print $0,"\n"}' /sys/kernel/debug/usb/devices
```

---

### Post by paul_b4 on 2022-01-24
[    0.090088] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.430782] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.430788] ehci-pci: EHCI PCI platform driver
[    0.430803] ehci-platform: EHCI generic platform driver
[    0.430813] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.430816] ohci-pci: OHCI PCI platform driver
[    0.430824] ohci-platform: OHCI generic platform driver
[    0.430831] uhci_hcd: USB Universal Host Controller Interface driver
[    0.812553] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.812568] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.813651] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x000000000004b810
[    0.813915] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.813922] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.813928] xhci_hcd 0000:00:14.0: Host supports USB 3.0 SuperSpeed
[    0.813994] usb usb1: Product: xHCI Host Controller
[    0.813997] usb usb1: Manufacturer: Linux 5.13.0-27-generic xhci-hcd
[    0.821900] ahci 0000:00:1f.2: version 3.0
[    0.841704] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.841715] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    0.848784] usb usb2: Product: xHCI Host Controller
[    0.848787] usb usb2: Manufacturer: Linux 5.13.0-27-generic xhci-hcd
[    0.862206] scsi host0: ahci
[    0.862639] scsi host1: ahci
[    1.181623] usb 1-3: new low-speed USB device number 2 using xhci_hcd
[    1.465657] usb 1-6: new high-speed USB device number 3 using xhci_hcd
[    1.487459] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f00)
[    1.757711] usb 1-8: new high-speed USB device number 4 using xhci_hcd
[   18.448306] mt76x0e 0000:03:00.0: Firmware Version: 1.0.07
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[sudo] password for paul: 
T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=480  MxCh= 0
D:  Ver= 2.01 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e080 Rev= 1.00
S:  Manufacturer=MediaTek
S:  Product=BT
S:  SerialNumber=1.0
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=450mA
A:  FirstIf#= 0 IfCount= 2 Cls=ff(vend.) Sub=ff Prot=ff
I:* If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=125us
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms
I:  If#= 1 Alt= 6 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  64 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  64 Ivl=1ms

---

### Post by jeremy31 on 2022-01-24
I already made a change anticipating that result, so
```
cd bluetooth-5.13
make clean
git pull
make
sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak
sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```

Reboot and if that doesn't work, post new results for ```
dmesg | egrep -i 'blue|firm|hci'; hciconfig -a; rfkill list; sudo awk -vRS= '/Vendor=0489/{print $0,"\n"}' /sys/kernel/debug/usb/devices
```

---

### Post by paul_b4 on 2022-01-25
alas... it still doesn't work

[    0.090008] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.466628] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.466635] ehci-pci: EHCI PCI platform driver
[    0.466647] ehci-platform: EHCI generic platform driver
[    0.466656] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.466659] ohci-pci: OHCI PCI platform driver
[    0.466666] ohci-platform: OHCI generic platform driver
[    0.466675] uhci_hcd: USB Universal Host Controller Interface driver
[    0.874197] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.874209] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.875321] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x000000000004b810
[    0.875567] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.875577] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.875583] xhci_hcd 0000:00:14.0: Host supports USB 3.0 SuperSpeed
[    0.875654] usb usb1: Product: xHCI Host Controller
[    0.875657] usb usb1: Manufacturer: Linux 5.13.0-27-generic xhci-hcd
[    0.879645] ahci 0000:00:1f.2: version 3.0
[    0.891426] usb usb2: Product: xHCI Host Controller
[    0.891429] usb usb2: Manufacturer: Linux 5.13.0-27-generic xhci-hcd
[    0.893615] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.893626] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    0.895515] scsi host0: ahci
[    0.895664] scsi host1: ahci
[    1.225605] usb 1-3: new low-speed USB device number 2 using xhci_hcd
[    1.500135] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f00)
[    1.505615] usb 1-6: new high-speed USB device number 3 using xhci_hcd
[    1.797596] usb 1-8: new high-speed USB device number 4 using xhci_hcd
[   17.325851] mt76x0e 0000:03:00.0: Firmware Version: 1.0.07
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by jeremy31 on 2022-01-25
No results for ```
sudo awk -vRS= '/Vendor=0489/{print $0,"\n"}' /sys/kernel/debug/usb/devices
```
That might be a sign of other issues

---

### Post by paul_b4 on 2022-01-26
T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=480  MxCh= 0
D:  Ver= 2.01 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e080 Rev= 1.00
S:  Manufacturer=MediaTek
S:  Product=BT
S:  SerialNumber=1.0
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=450mA
A:  FirstIf#= 0 IfCount= 2 Cls=ff(vend.) Sub=ff Prot=ff
I:* If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=125us
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms
I:  If#= 1 Alt= 6 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  64 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  64 Ivl=1ms

---

### Post by jeremy31 on 2022-01-26
One last try with a change
```
cd bluetooth-5.13
make clean
git pull
make
sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak
sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```

---

### Post by paul_b4 on 2022-01-26
Alas, it still hasn't worked.   Is there no hope?

---

### Post by jeremy31 on 2022-01-26
Ok, I forgot one thing since the last time I did this
```
cd bluetooth-5.13
make clean
git pull
make
sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak
sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
sudo depmod -a
```

Reboot.  Since I added a new ID to the source code, the depmod command has to be run for the kernel to know about that change

---

### Post by paul_b4 on 2022-01-27
IMPROVEMENT!  After I rebooted, the little bluetooth icon immediately appeared in the taskbar, with a red x-out.  I was able to click the turn-on function, but that did not turn it on.  In Settings, I am able to toggle bluetooth switch on and off, but it still displays as "Bluetooth Turned Off" the whole time.  Bluetooth Manager doesn't give me the same error as before, but it appears to be loading but then doesn't actually load.  This is what I got in the terminal when I did your operations:

```
paul@paul-X555LAB:~$ cd bluetooth-5.13
paul@paul-X555LAB:~/bluetooth-5.13$ make clean
make -C /lib/modules/5.13.0-27-generic/build M=/home/paul/bluetooth-5.13 clean
make[1]: Entering directory '/usr/src/linux-headers-5.13.0-27-generic'
  CLEAN   /home/paul/bluetooth-5.13/Module.symvers
make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-27-generic'
paul@paul-X555LAB:~/bluetooth-5.13$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 703 bytes | 63.00 KiB/s, done.
From https://github.com/jeremyb31/bluetooth-5.13
   df3370a..ba71f37  main       -> origin/main
Updating df3370a..ba71f37
Fast-forward
 btusb.c | 7 ++++---
 1 file changed, 4 insertions(+), 3 deletions(-)
paul@paul-X555LAB:~/bluetooth-5.13$ make
make -C /lib/modules/5.13.0-27-generic/build M=/home/paul/bluetooth-5.13 modules
make[1]: Entering directory '/usr/src/linux-headers-5.13.0-27-generic'
  CC [M]  /home/paul/bluetooth-5.13/btusb.o
/home/paul/bluetooth-5.13/btusb.c: In function ‘btusb_setup_intel_new’:
/home/paul/bluetooth-5.13/btusb.c:2959:9: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
 2959 |   match = usb_match_id(data->intf, msft_rej_table);
      |         ^
  CC [M]  /home/paul/bluetooth-5.13/ath3k.o
  MODPOST /home/paul/bluetooth-5.13/Module.symvers
  CC [M]  /home/paul/bluetooth-5.13/ath3k.mod.o
  LD [M]  /home/paul/bluetooth-5.13/ath3k.ko
  BTF [M] /home/paul/bluetooth-5.13/ath3k.ko
Skipping BTF generation for /home/paul/bluetooth-5.13/ath3k.ko due to unavailability of vmlinux
  CC [M]  /home/paul/bluetooth-5.13/btusb.mod.o
  LD [M]  /home/paul/bluetooth-5.13/btusb.ko
  BTF [M] /home/paul/bluetooth-5.13/btusb.ko
Skipping BTF generation for /home/paul/bluetooth-5.13/btusb.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-27-generic'
paul@paul-X555LAB:~/bluetooth-5.13$ sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak
[sudo] password for paul: 
paul@paul-X555LAB:~/bluetooth-5.13$ sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
paul@paul-X555LAB:~/bluetooth-5.13$ sudo depmod -a
paul@paul-X555LAB:~/bluetooth-5.13$ 
```

Thanks

---

### Post by jeremy31 on 2022-01-27
In terminal try```
bluetoothctl
power on
scan on
```
See if it works or gives errors, use ctrl + d to exit Bluetooth control 
Also see if Bluetooth is blocked in```
rfkill list
```

---

### Post by paul_b4 on 2022-01-28
OK, this is what I get:

```
paul@paul-X555LAB:~$ bluetoothctl
Agent registered
[bluetooth]# power on
No default controller available
[bluetooth]# scan on
No default controller available
[bluetooth]# quit
paul@paul-X555LAB:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
paul@paul-X555LAB:~$ 



```

---

### Post by jeremy31 on 2022-01-28
should look at new results for ```
dmesg | egrep -i 'blue|firm|hci'; hciconfig -a
```

---

### Post by paul_b4 on 2022-01-28
Ok

```
paul@paul-X555LAB:~$ dmesg | egrep -i 'blue|firm|hci'; hciconfig -a
[    0.090279] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.450508] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.450515] ehci-pci: EHCI PCI platform driver
[    0.450527] ehci-platform: EHCI generic platform driver
[    0.450536] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.450538] ohci-pci: OHCI PCI platform driver
[    0.450546] ohci-platform: OHCI generic platform driver
[    0.450553] uhci_hcd: USB Universal Host Controller Interface driver
[    0.849922] ahci 0000:00:1f.2: version 3.0
[    0.851644] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.851657] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.852727] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x000000000004b810
[    0.853000] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.853008] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.853014] xhci_hcd 0000:00:14.0: Host supports USB 3.0 SuperSpeed
[    0.853085] usb usb1: Product: xHCI Host Controller
[    0.853089] usb usb1: Manufacturer: Linux 5.13.0-27-generic xhci-hcd
[    0.860325] usb usb2: Product: xHCI Host Controller
[    0.860327] usb usb2: Manufacturer: Linux 5.13.0-27-generic xhci-hcd
[    0.862215] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.862225] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    0.866174] scsi host0: ahci
[    0.878206] scsi host1: ahci
[    1.193854] usb 1-3: new low-speed USB device number 2 using xhci_hcd
[    1.473856] usb 1-6: new high-speed USB device number 3 using xhci_hcd
[    1.479149] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f00)
[    1.773896] usb 1-8: new high-speed USB device number 4 using xhci_hcd
[   17.874679] Bluetooth: Core ver 2.22
[   17.874745] Bluetooth: HCI device and connection manager initialized
[   17.874752] Bluetooth: HCI socket layer initialized
[   17.874757] Bluetooth: L2CAP socket layer initialized
[   17.874765] Bluetooth: SCO socket layer initialized
[   18.290830] mt76x0e 0000:03:00.0: Firmware Version: 1.0.07
[   37.233411] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.233415] Bluetooth: BNEP filters: protocol multicast
[   37.233420] Bluetooth: BNEP socket layer initialized
hci0:    Type: Primary  Bus: USB
    BD Address: 40:B8:9A:76:DC:B8  ACL MTU: 1021:4  SCO MTU: 128:2
    DOWN 
    RX bytes:587 acl:0 sco:0 events:32 errors:0
    TX bytes:374 acl:0 sco:0 commands:32 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0xdb 0xff 0x5b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 


```

---

### Post by jeremy31 on 2022-01-29
try ```
sudo hciconfig hci0 up
```
See if anything changes, the hciconfig -a result shows the device is down but did transmit and receive data

---

### Post by paul_b4 on 2022-01-30
hmm, i get this

```
paul@paul-X555LAB:~$ sudo hciconfig hci0 up
[sudo] password for paul: 
Can't init device hci0: Input/output error (5)

```

---

### Post by jeremy31 on 2022-01-30
I don't know what is causing the issue as there were no clues in dmesg.  I would recommend getting an IOGear GBU521 USB dongle.  Mine has worked reliably since I started using Ubuntu

---

### Post by paul_b4 on 2022-02-04
Ok, thanks

---

