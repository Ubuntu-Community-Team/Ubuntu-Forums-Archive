---
title: "ASUS WL-167g support"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by jamey on 2006-07-19
I have just ordered this wirless USB adapter for my girlfriend's laptop. Her machine is relatively low-powered and has a Via C3 processor, 256 MB of RAM, a 30 GB hard disk and a CD/DVD combo drive.

I am planning on using the Ubuntu 6.06 LTS alternative CD (the Live installer fails to partition the disk) to install a fresh copy onto it. I will be using the WL-167g adapter with it; will I have any problems trying to get wireless networking using this adapter?

---

### Post by x64Jimbo on 2006-07-19
Quote from Ndiswrapper wiki article:
> [LIST=1]
[*]Card: Asus WL-167G, 54mbps[LIST]
[*]Chipset: Ralink RT2500 USB
[*]usbid: 0b05:1706
[*]Driver: Cdrom, WinXP driver. (rt2500.sys, original at [www.ralinktech.com]("http://www.ralinktech.com"))
[*]Other: Tested with Ndiswrapper 0.11, kernel 2.4.27, Knoppix. All thanks to ndiswrapper! B-) (RS) Works with vanilla 2.6.9 ONLY WITH EHCI DISABLED + ndiswrapper 0.11 and D-Link 1.00.00.0000 drivers found at [[[27]]("http://www.sarcazzo.com/cose/dwlg_122_rt2500_usbdrivers_ndis.tar.gz")] More info at [[[28]]("http://61.222.76.235/phpbb2/viewtopic.php?t=129")] Works OK with 2.6.10 and Ndiswrapper 1.0rc1Works OK with 2.6.11 and Ndiswrapper 1.1 (EHCI Disabled/Kenrel 4K Stack Disabled/May have to modify the rt2500usb.inf for proper#*usbid if No "hardware present" found after ndiswrapper -i)Works ok with 2.6.10, ndiswrapper 1.1 (EHCI loaded with modprobe ehci-hcd log2_irq_thresh=4 to avoid "usb 1-2: reset high speed USB device using ehci_hcd and address 2" Works fine with Ndiswrapper 0.11, kernel 2.4.27, WinXP driver(should comment out other manufactures in inf file; make sure /etc/ndiswrapper/rt2500usb has file named in correct usbid(0b05:1706))[/LIST] [/LIST]
The Ralink cards are also known to work with a special linux driver, which can be found here:
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

---

### Post by Stinger on 2006-07-19
> **jamey said:**
> I have just ordered this wirless USB adapter for my girlfriend's laptop. Her machine is relatively low-powered and has a Via C3 processor, 256 MB of RAM, a 30 GB hard disk and a CD/DVD combo drive.

I am planning on using the Ubuntu 6.06 LTS alternative CD (the Live installer fails to partition the disk) to install a fresh copy onto it. I will be using the WL-167g adapter with it; will I have any problems trying to get wireless networking using this adapter?

Sounds similar to my IBM Netvista 20GB harddisk , 256MB SD ram , 1GHz PIII.
The machine is using ( yes you guessed it ) an ASUS WL-167g just like yours.

I can tell you it works out of the box , no problems so far.:-D 
(And no need for ndiswrapper , it just plain works )

---

