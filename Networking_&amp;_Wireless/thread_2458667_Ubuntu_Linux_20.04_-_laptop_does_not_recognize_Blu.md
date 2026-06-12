---
title: "Ubuntu Linux 20.04 - laptop does not recognize Bluetooth devices; need help"
date: 2021-03-02
forum: Networking &amp; Wireless
---

### Post by la.khan on 2021-03-02
Hi all,

I have a Dell Inspiron 3543 laptop running Ubuntu Linux 20.04.2 LTS (64 bit). When I installed UL20.04 in May 2020, my laptop did not recognize any BT device and that never bothered me as I did not own a BT device.

A month back I got a BT speaker and it was a trivial task to pair my laptop with BT speaker. I don't recollect the steps I performed. I vaguely recollect using some sudo commands and/or install some BT driver(s) and my laptop recognized my BT speaker. A couple weeks ago, I bought a BT neckband (earphones + microphone). The earphones paired effortlessly with my laptop but I could never get the microphone to work with my laptop. However, the neckband (earphones + microphone) work flawlessly with my Android mobile.

To make the neckband microphone work with my laptop, I looked up Google and made changes to config files, changed settings, installed applications (Blueman, oFono, VLC), installed drivers etc. In short, I made changes to my laptop that I don't even understand. To no avail, as my neckband microphone did not work with my laptop. I was uncomfortable with changes I made so I decided to wipe my HDD clean and re-install my UL20.04 installation (I backed all the folders/files so that nothing important is lost).

It took me a couple of days to bring my entire system back to what it was. Now with my laptop OS, applications, folders/files restored, my laptop does not recognize any BT device. I know it was something simple & trivial but I can't recollect anymore the commands I ran a month back. I spent 2 days trying to figure out how to get my laptop recognize BT devices but couldn't succeed:cry: So, I need help in getting my laptop to recognize BT devices again. I wonder what is it I am missing. Any ideas?

My configuration is
Hardware: Dell Inspiron 3543 Intel(R) Core i5-5200U CPU @ 2.2 GHz x 4; 8GB RAM; 1 TB HDD
OS: Ubuntu Linux 20.04.2 LTS (64 bit); Gnome 3.36.8

If you need any more information, please let me know. Thanks for your assistance in this regard. 

Note: One key learning from this episode, for me, was to install timeshift application so that I can easily restore my OS to an earlier date. In 2-3 minutes, as opposed to 24+ hours:)

---

### Post by la.khan on 2021-03-02
Hi all,

Just to add more information to my BT problem. I ran the following commands.

```
$sudo cat /sys/kernel/debug/usb/devices | grep Vendor=0a5c -A8
P:  Vendor=0a5c ProdID=21d7 Rev= 1.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM43142A0
S:  SerialNumber=2C337AFC6E92
C:* #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

$rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
14: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

$lsusb; dmesg | egrep -i 'blue|firm'
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 004: ID 0c45:6a04 Microdia 
Bus 001 Device 007: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 001 Device 003: ID 0a05:7211 Unknown Manufacturer hub
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.110930] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.152870] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   16.947397] Bluetooth: Core ver 2.22
[   16.947425] Bluetooth: HCI device and connection manager initialized
[   16.947429] Bluetooth: HCI socket layer initialized
[   16.947432] Bluetooth: L2CAP socket layer initialized
[   16.947436] Bluetooth: SCO socket layer initialized
[   17.404485] Bluetooth: hci0: BCM: chip id 70
[   17.414860] Bluetooth: hci0: BCM: features 0x06
[   17.431514] Bluetooth: hci0: <***machine name***>
[   17.431517] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[   17.638726] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
[   17.638729] Bluetooth: hci0: BCM: 'brcm/BCM43142A0-0a5c-21d7.hcd'
[   17.638730] Bluetooth: hci0: BCM: 'brcm/BCM-0a5c-21d7.hcd'
[   19.674550] Bluetooth: hci0: command 0x1003 tx timeout
[   19.675500] Bluetooth: hci0: unexpected event for opcode 0x1003

```
Since my system is unable to find BCM43142A0-0a5c-21d7.hcd, I searched for the same on Google and I found [https://github.com/winterheart/broadcom-bt-firmware/tree/master/brcm](https://github.com/winterheart/broadcom-bt-firmware/tree/master/brcm)  and I found file BCM43142A0-0a5c-21d7.hcd. I downloaded it and copied  to /lib/firmware/brcm/. I ran these  sudo commands and restarted my machine.

```
sudo modprobe -r btusb
sudo modprobe btusb

```

Now when I run dmesg | egrep -i 'blue|firm', I see
```
[    0.111326] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.153238] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   17.236337] Bluetooth: Core ver 2.22
[   17.236360] Bluetooth: HCI device and connection manager initialized
[   17.236363] Bluetooth: HCI socket layer initialized
[   17.236365] Bluetooth: L2CAP socket layer initialized
[   17.236371] Bluetooth: SCO socket layer initialized
[   19.385432] Bluetooth: hci0: BCM: chip id 70
[   19.386425] Bluetooth: hci0: BCM: features 0x06
[   19.402423] Bluetooth: hci0: <***machine name***>
[   19.402425] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0341
[   20.364354] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0a5c-21d7.hcd' Patch
[   21.148462] Bluetooth: hci0: BCM43142A0 Generic USB Class 2 NonUHE @ 20 MHz
[   21.148465] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0341
[   34.222434] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.222436] Bluetooth: BNEP filters: protocol multicast
[   34.222441] Bluetooth: BNEP socket layer initialized
[   80.054475] Bluetooth: RFCOMM TTY layer initialized
[   80.054481] Bluetooth: RFCOMM socket layer initialized
[   80.054486] Bluetooth: RFCOMM ver 1.11

```

Finally, my machine could detect BT devices :grin::KS

---

### Post by zerubbabel on 2021-11-19
Are you saying that you got both the headphones and the mic to work?

---

