---
title: "My Ubuntu 16.04 doesn't connect to wifi"
date: 2017-08-29
forum: Networking &amp; Wireless
---

### Post by ra.abbasi on 2017-08-29
Hi guys,
 I'm very new in Ubuntu and have worked on Windows so far. I installed an Ubuntu 16.04 x64 OS on my HP laptop and now reading the book "Getting Started with Ubuntu 16.04" to be familiar with the OS. I even don't know what a command is or how to issue it!

Anyway, my issue for now is the wifi. While Ubuntu shows the wifi connections when I choose my own one and type the password to connect, whatever I try again, it doesn't connect. I have chosen the option "show characters" to be sure about right  typing. 
I also tested the wifi password on my smartphone. It connected and works well.
Once again I returned to the Ubuntu and clicked on "Forgot network" and then re-chose my connection and typing the password, but the same result! :(
It's strange for me. I would think Linux OS is really excellent and practical.

If possible please help me solve the issue.

---

### Post by praseodym on 2017-08-29
Please open a terminal with CTRL+ALT+T and show the hardware specs by these 2 commands:
```

lspci -nnk
lsusb
```

---

### Post by ra.abbasi on 2017-08-29
I typed the first and hit enter. Then the same for the second. this is the output:

```
~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: Hewlett-Packard Company 3rd Gen Core processor DRAM Controller [103c:1854]
	Kernel driver in use: ivb_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0156] (rev 09)
	Subsystem: Hewlett-Packard Company 3rd Gen Core processor Graphics Controller [103c:1854]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family MEI Controller [103c:1854]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family USB Enhanced Host Controller [103c:1854]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family High Definition Audio Controller [103c:1854]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family USB Enhanced Host Controller [103c:1854]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 7 Series Chipset Family LPC Controller [8086:1e5e] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series Chipset Family LPC Controller [103c:1854]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [103c:1854]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family SMBus Controller [103c:1854]
	Kernel modules: i2c_i801
01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi Adapter
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci
01:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
	Subsystem: Hewlett-Packard Company RTS5229 PCI Express Card Reader [103c:1854]
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	DeviceName: Hanksville Gbe Lan Connection
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:1854]
	Kernel driver in use: r8169
	Kernel modules: r8169
abbasi@abbasi-HP:~$ lsusb
Bus 002 Device 003: ID 1bcf:2c1e Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abbasi@abbasi-HP:~$
```

---

### Post by ra.abbasi on 2017-08-29
But one hint here, the Os would connect the wifi well beforehand but I don't know what happened that it has this issue now! :(

---

### Post by praseodym on 2017-08-29
So, the driver rt2800pci is shown. Lets see the following:
```

cat /etc/resolv.conf
ifconfig -a
iwconfig
rfkill list
```

---

### Post by Autodave on 2017-08-29
You are likely to get way better help from praseodym than me, but let me give you what I have. I have a Dell laptop. And, it is one of many. But, it is the ONLY one with the same issue that you are having. It may take me 20 times entering the password before it accepts it. (I used this particular machine experimenting with a few things and would often either have to reinstall the OS or install a different Linux version.)

The very first time I used it, I believe it took me 4 or 5 tries to get it to recognize the password. After that, I had the problem every time I had a new OS on it. Why? Dunno. It just did.

---

### Post by wildmanne39 on 2017-08-29
Welcome to the forum!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Autodave on 2017-08-29
Another thing you may try that did work for me a lot of the time:

Make a LibreOffice file or something similar with just your password in it. Copy and paste the password into you wifi when trying to connect. IF it connects, great!  Remember then to delete that file.

---

### Post by ra.abbasi on 2017-08-31
> Make a LibreOffice file or something similar with just your password in it. Copy and paste the password into you wifi when trying to connect. IF it connects, great! 
Yes, it worked that way. Thank you very much.
Two points:
1- Isn't it a bug in Ubuntu? I think so.
2- How can I give reps to you in return for your help.

I also thank all of other nice guys for their help through their replies. :-)

---

### Post by wildmanne39 on 2017-08-31
Please use thread tools at the top of the page to mark the thread solved.

Thanks

---

### Post by Autodave on 2017-08-31
> **ra.abbasi said:**
> Yes, it worked that way. Thank you very much.
Two points:
1- Isn't it a bug in Ubuntu? I think so.
2- How can I give reps to you in return for your help.

I also thank all of other nice guys for their help through their replies. :-)


Is it a bug? Dunno. I have installed Ubuntu and Xubuntu on *many *machines. And of course, my own machine is the one that gave me the headaches over the wireless password. :-) I spent quite a bit of time entering that password the first time. After about 30 tries, I thought of the copy & paste idea and it worked. Why? Dunno. Sometimes you just are thankful for getting something to work finally: you lock it away in your mind and move on to the next thing.

---

