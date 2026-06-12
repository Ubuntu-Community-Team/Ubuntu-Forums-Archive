---
title: "Wifi Adapter help"
date: 2018-05-12
forum: Networking &amp; Wireless
---

### Post by blakefreak2 on 2018-05-12
I bought a cheap USB wifi adapter off of ebay and can't seem to get the driver installed.  I have the driver downloaded.  It is RTL8811au but I don't know how to instal via terminal.  Any help would be greatly appreciated.

---

### Post by jeremy31 on 2018-05-12
Please post results from terminal for ```
lsusb; uname -a; cat /etc/lsb-release
```
Welcome to the forums

---

### Post by blakefreak2 on 2018-05-12
> **jeremy31 said:**
> Please post results from terminal for ```
lsusb; uname -a; cat /etc/lsb-release
```
Welcome to the forums

```
derf@derf-desktop:~$ lsusb; uname -a; cat /etc/lsb-release
Bus 003 Device 002: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 002: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 05dc:c75c Lexar Media, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux derf-desktop 4.13.0-41-generic #46~16.04.1-Ubuntu SMP Thu May 3 10:06:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"
```

---

### Post by jeremy31 on 2018-05-12
Try the following and reboot
```
sudo apt install git dkms
git clone https://github.com/gnab/rtl8812au.git
sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2
```

---

### Post by blakefreak2 on 2018-05-12
That worked.  Thank you very much!

---

### Post by blakefreak2 on 2018-05-12
> **jeremy31 said:**
> Please post results from terminal for ```
lsusb; uname -a; cat /etc/lsb-release
```
Welcome to the forums

derf@derf-desktop:~$ lsusb; uname -a; cat /etc/lsb-release
Bus 003 Device 002: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 002: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 05dc:c75c Lexar Media, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux derf-desktop 4.13.0-41-generic #46~16.04.1-Ubuntu SMP Thu May 3 10:06:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"

---

