---
title: "BCM4352 Bluetooth hcitool scan does not find any device"
date: 2015-08-15
forum: Networking &amp; Wireless
---

### Post by x-mair-x on 2015-08-15
Hello Community my Blue-tooth is not working !

Rx and Tx bytes are counted but hcitool scan cant find any available device.
Wlan is working on the combo chip-set and the Blue-tooth icon is in the task-bar
I think wlan and blue-tooth use the same antenna because they use both 2.4GHz
No Blue-tooth errors in dmesg

Thanks in advance for any help !




> 

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

 uname -a
Linux myServer 3.13.0-58-generic #97-Ubuntu SMP Wed Jul 8 02:56:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03
  hciconfig --all
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 54:27:1E:FC:9A:1F  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:2870 acl:0 sco:0 events:304 errors:0
    TX bytes:4322 acl:0 sco:0 commands:253 errors:0
    Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'myServer-0'
    Class: 0x700100
    Service Classes: Object Transfer, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 4.0 (0x6)  Revision: 0x1000
    LMP Version: 4.0 (0x6)  Subversion: 0x220e
    Manufacturer: Broadcom Corporation (15)

hcitool scan
Scanning ...



---

### Post by jeremy31 on 2015-08-15
The results from ```
lsusb; dmesg | egrep -i 'blue|firm'
``` Will be helpful

---

### Post by x-mair-x on 2015-08-15
> **jeremy31 said:**
> The results from ```
lsusb; dmesg | egrep -i 'blue|firm'
``` Will be helpful

```
lsusb; dmesg | egrep -i 'blue|firm'
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 15c2:0036 SoundGraph Inc. LC16M VFD Display/IR Receiver
Bus 003 Device 003: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 054c:031e Sony Corp. PRS-300/PRS-505 eBook reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.360123] Bluetooth: Core ver 2.17
[    2.360251] Bluetooth: HCI device and connection manager initialized
[    2.360257] Bluetooth: HCI socket layer initialized
[    2.360258] Bluetooth: L2CAP socket layer initialized
[    2.360268] Bluetooth: SCO socket layer initialized
[    2.554766] Bluetooth: RFCOMM TTY layer initialized
[    2.554773] Bluetooth: RFCOMM socket layer initialized
[    2.554776] Bluetooth: RFCOMM ver 1.11
[    2.554885] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.554886] Bluetooth: BNEP filters: protocol multicast
[    2.554891] Bluetooth: BNEP socket layer initialized



```

---

### Post by jeremy31 on 2015-08-15
Support for that device is still broken in the 3.13 kernels, so an update should fix
```
[COLOR=#333333][FONT=Ubuntu Beta]sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-core-lts-utopic xserver-xorg-lts-utopic xserver-xorg-video-all-lts-utopic xserver-xorg-input-all-lts-utopic libwayland-egl1-mesa-lts-utopic
```
```
wget [/FONT][/COLOR]https://www.dropbox.com/s/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd
```

[COLOR=#333333][FONT=Ubuntu Beta]Reboot and run ```
dmesg | egrep -i 'firm|blue'
``` and post [/FONT][/COLOR]

---

### Post by x-mair-x on 2015-08-15
where is path to put the fw-0b05-17cf.hcd firmware file for the new kernel?

maybe default LTS distro kernel will switch from 3.13.0.58 .to 3.16.0.45.36 sooner or later and the the new firmware files are supporting the pci fake usb bluetooth by kernel module

I am a little bit scared because the wlan chipset has a pci connection and i do not know how they make a usb device out of this ? 

I think in 3.16.0.45.36 there is an update in the drivers folder for the wlan pci device that will support the usb id for the bluetooth ..my be thats the trick!

Do they stay for ever in the Ubuntu LTS on one kernel version (**major.minor**.bugfix.security) because
[https://www.kernel.org/category/releases.html](https://www.kernel.org/category/releases.html) => 3.14 is or better 3.18 
3.13 is not a LTS version by kernel.org
and on [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
i could not find any plans
ok..I have to study :-) [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

this my kernel today

```

 dpkg -l | grep linux
ii  bluez-tools                                           0.1.38+git662e-3                                    amd64        Set of tools to manage Bluetooth devices for linux
ii  libselinux1:amd64                                     2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                                        1.0.1-1                                             amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                  1.0.1-1                                             amd64        Video4linux frame format conversion library
ii  linux-firmware                                        1.127.15                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.58.65                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.58.65                                        amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.58.65                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-61.100                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  pptp-linux                                            1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                            2.20.1-5.1ubuntu20.6                                amd64        Miscellaneous system utilities

```

---

### Post by jeremy31 on 2015-08-15
I need to know the exact filename from the results of ```
dmesg | egrep -i 'blue|firm'
``` when booted into the new kernel, chances are it will need to be /lib/firmware/brcm/BCM20702A1-0b05-17cf.hcd

---

### Post by x-mair-x on 2015-08-15
ok.. thanks in advance for your help jeremy31,
but I edit my post before what is your suggestion as expert with the linux LTS distribution version ?
I am on [COLOR=#000000][I]14.04.3 LTS ..see my updated links above
so the new kernel has the *.hcd compiled in the drivers for wlan as call ?
normaly this is a *.bin !
I do not want to make rocket science with my stable ubuntu :-)
looks like brcm is the synonym for broadcom ..I designed in some chip-set in 2004/5 for with this company :-) 
[/I][/COLOR]```

/lib/firmware/brcm$ ls -al
total 7712
drwxr-xr-x  2 root root   4096 Aug 12 18:49 .
drwxr-xr-x 65 root root  20480 Aug 12 18:49 ..
-rw-r--r--  1 root root 269595 Nov 24  2014 bcm4329-fullmac-4.bin
-rw-r--r--  1 root root  96224 Dez  1  2014 bcm43xx-0.fw
-rw-r--r--  1 root root    180 Dez  1  2014 bcm43xx_hdr-0.fw
-rw-r--r--  1 root root 397312 Dez  1  2014 brcmfmac43143.bin
-rwxr-xr-x  1 root root 385067 Jul 31 15:06 brcmfmac43143-sdio.bin
-rw-r--r--  1 root root 348160 Nov 24  2014 brcmfmac43236b.bin
-rw-r--r--  1 root root 455745 Dez  1  2014 brcmfmac43241b0-sdio.bin
-rw-r--r--  1 root root 403855 Dez  1  2014 brcmfmac43241b4-sdio.bin
-rw-r--r--  1 root root 479232 Jul 31 15:06 brcmfmac43242a.bin
-rw-r--r--  1 root root 253748 Dez  1  2014 brcmfmac4329-sdio.bin
-rw-r--r--  1 root root 222126 Dez  1  2014 brcmfmac4330-sdio.bin
-rw-r--r--  1 root root 451566 Dez  1  2014 brcmfmac4334-sdio.bin
-rw-r--r--  1 root root 569291 Dez  1  2014 brcmfmac4335-sdio.bin
-rw-r--r--  1 root root 219557 Dez  1  2014 brcmfmac43362-sdio.bin
-rw-r--r--  1 root root 493599 Jul 31 15:06 brcmfmac4339-sdio.bin
-rw-r--r--  1 root root 507752 Jul 30 22:13 brcmfmac4354-sdio.bin
-rw-r--r--  1 root root 557056 Jul 31 15:06 brcmfmac43569.bin
-rw-r--r--  1 root root 550333 Jul 31 15:06 brcmfmac43570-pcie.bin

```

---

### Post by jeremy31 on 2015-08-15
Some of the Broadcom bluetooth devices need firmware that is only available from Windows driver packages and if you still aren't on a 3.16 kernel then try ```
[COLOR=#333333][FONT=Ubuntu Beta]sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid
``` and after a reboot post the result of ```
uname -a; dmesg | egrep -i 'blue|firm"
```[/FONT][/COLOR]

---

### Post by x-mair-x on 2015-08-15
For 14.04 its [COLOR=#333333][FONT=monospace]linux-generic-lts-vivid and not [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]linux-generic-lts-utopic am I right ?
[/FONT][/COLOR]https://wiki.ubuntu.com/Kernel/LTSEnablementStack

---

### Post by x-mair-x on 2015-08-15
uname -a
Linux myServer 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

ls -al
total 7748
drwxr-xr-x  2 root root   4096 Aug 16 02:21 .
drwxr-xr-x 66 root root  20480 Aug 16 02:13 ..
-rw-r--r--  1 root root 269595 Nov 24  2014 bcm4329-fullmac-4.bin
-rw-r--r--  1 root root  96224 Dez  1  2014 bcm43xx-0.fw
-rw-r--r--  1 root root    180 Dez  1  2014 bcm43xx_hdr-0.fw
-rw-r--r--  1 root root 397312 Dez  1  2014 brcmfmac43143.bin
-rwxr-xr-x  1 root root 385067 Jul 31 15:06 brcmfmac43143-sdio.bin
-rw-r--r--  1 root root 348160 Nov 24  2014 brcmfmac43236b.bin
-rw-r--r--  1 root root 455745 Dez  1  2014 brcmfmac43241b0-sdio.bin
-rw-r--r--  1 root root 403855 Dez  1  2014 brcmfmac43241b4-sdio.bin
-rw-r--r--  1 root root 479232 Jul 31 15:06 brcmfmac43242a.bin
-rw-r--r--  1 root root 253748 Dez  1  2014 brcmfmac4329-sdio.bin
-rw-r--r--  1 root root 222126 Dez  1  2014 brcmfmac4330-sdio.bin
-rw-r--r--  1 root root 451566 Dez  1  2014 brcmfmac4334-sdio.bin
-rw-r--r--  1 root root 569291 Dez  1  2014 brcmfmac4335-sdio.bin
-rw-r--r--  1 root root 219557 Dez  1  2014 brcmfmac43362-sdio.bin
-rw-r--r--  1 root root 493599 Jul 31 15:06 brcmfmac4339-sdio.bin
-rw-r--r--  1 root root 507752 Jul 30 22:13 brcmfmac4354-sdio.bin
-rw-r--r--  1 root root 557056 Jul 31 15:06 brcmfmac43569.bin
-rw-r--r--  1 root root 550333 Jul 31 15:06 brcmfmac43570-pcie.bin
-rw-r--r--  1 root root 588940 Jul 31 15:06 brcmfmac43602-pcie.ap.bin
-rw-r--r--  1 root root 590544 Jul 31 15:06 brcmfmac43602-pcie.bin
-rw-r-----  1 root root  35127 Aug 16 02:21 fw-0b05-17cf.hcd

dmesg | egrep -i 'blue|firm'
[    1.982007] Bluetooth: Core ver 2.20
[    1.982026] Bluetooth: HCI device and connection manager initialized
[    1.982030] Bluetooth: HCI socket layer initialized
[    1.982032] Bluetooth: L2CAP socket layer initialized
[    1.982038] Bluetooth: SCO socket layer initialized
[    1.986401] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    1.986403] Bluetooth: BNEP filters: protocol multicast
[    1.986406] Bluetooth: BNEP socket layer initialized
[    1.989003] Bluetooth: RFCOMM TTY layer initialized
[    1.989009] Bluetooth: RFCOMM socket layer initialized
[    1.989014] Bluetooth: RFCOMM ver 1.11
[    2.415408] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0b05-17cf.hcd failed with error -2
[    2.415411] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0b05-17cf.hcd not found



looks like a rename case !

---

### Post by x-mair-x on 2015-08-15
sudo mv fw-0b05-17cf.hcd BCM20702A0-0b05-17cf.hcd

 hcitool scan
Scanning ...
	D0:66:7B:37:7E:55	DTVBluetooth

you are the linux guru :-) thank you
but the right LTS kernel is also important !!! 

ok this scan was not my xbmc needed headset (only the BT id of the neighborhood)   
but now it will work with out a problem i am sure :-)

---

### Post by x-mair-x on 2015-08-15
how to get this to solved !

---

