---
title: "Bluetooth not working Ubuntu 14.04"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by rob167 on 2016-04-07
So I'm new to using ubuntu daily. I'm loving Ubuntu vs. any version of windows I have used. Only thing is I cant seem to get my bluetooth to work. Any help would be appreciated. Thanks in advance!
Laptop:
Dell Inspiron 1545

---

### Post by Bucky Ball on 2016-04-08
Welcome. What have you tried to get it to work and how is it not working? Please give as much info as you can about the issue when posting and that will help us help you. 

Do you have Bluez installed? What software are you using to try and connect?

---

### Post by rob167 on 2016-04-08
I have all bluetooth apps installed. When I click on bluetooth from settings, it pops up and says "no bluetooth adapters found" and i am unable to enable(turn on) bluetooth. 
Same with bluetooth manager. it wont let me search. All the options are whited out.

I have all bluetooth software installed(to my knowledge anyways) which includes the following.
Bluetooth support
Bluetooth transfer
Bluetooth device setup
Bluetooth Manager
Bluetooth
Bluewho
Bluez

Thanks again for any help! much appreciated.

---

### Post by Bucky Ball on 2016-04-08
And your bluetooth receiver/transmitter is internal or an external USB dongle?

Perhaps give us the output of this:

> sudo service bluetooth status

Please use code tags for the output (see the green link in my signature at the bottom of this post).

---

### Post by rob167 on 2016-04-08
Its internal.
```

bluetooth start/running, process 565

```

---

### Post by jeremy31 on 2016-04-08
Rob

Post the result of ```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'; uname -a
```

---

### Post by rob167 on 2016-04-08
```

yourlocalconsciousfella@yourlocalconsciousfella-Inspiron-1545:~$ lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'; uname -a
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.124110] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.232186] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.755944] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   31.400945] Bluetooth: Core ver 2.20
[   31.400999] Bluetooth: HCI device and connection manager initialized
[   31.401005] Bluetooth: HCI socket layer initialized
[   31.401009] Bluetooth: L2CAP socket layer initialized
[   31.401018] Bluetooth: SCO socket layer initialized
[   31.735389] Bluetooth: RFCOMM TTY layer initialized
[   31.735402] Bluetooth: RFCOMM socket layer initialized
[   31.735413] Bluetooth: RFCOMM ver 1.11
[   32.270927] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.270932] Bluetooth: BNEP filters: protocol multicast
[   32.270939] Bluetooth: BNEP socket layer initialized
[ 8176.231371] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[29522.505877] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[32429.942983] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Linux yourlocalconsciousfella-Inspiron-1545 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:39:00 UTC 2016 i686 i686 i686 GNU/Linux
yourlocalconsciousfella@yourlocalconsciousfella-Inspiron-1545:~$

```

---

### Post by jeremy31 on 2016-04-08
Did bluetooth work in windows?  Nothing is detected by the kernel in Ubuntu

---

### Post by Bucky Ball on 2016-04-09
> **jeremy31 said:**
> Did bluetooth work in windows?  Nothing is detected by the kernel in Ubuntu

Exactly what I was thinking. I'm wondering if the computer has bluetooth as I see [nothing in the specs]("http://www.cnet.com/products/dell-inspiron-1545-15-6-p-t4200-vista-home-premium-3-gb-ram-250-gb-hdd-series/specs/") about it.

---

### Post by kagashe on 2016-04-09
This Laptop has problems with Bluetooth even on Windows as per discussion Dell Support.
[Dell Inspiron 1545 laptop does it have bluetooth]("http://en.community.dell.com/support-forums/laptop/f/3518/t/19468332")

Dell has also sold this Laptop with Ubuntu pre-installed, therefore, he may not  have Windows.

Kamalakar

---

