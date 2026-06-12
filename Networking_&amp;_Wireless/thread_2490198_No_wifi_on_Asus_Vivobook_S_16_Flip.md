---
title: "No wifi on Asus Vivobook S 16 Flip"
date: 2023-08-25
forum: Networking &amp; Wireless
---

### Post by Tikhon03 on 2023-08-25
I have a new Asus Vivobook S 16 Flip, with kubuntu installed. Here is the output of uname -r
```
[FONT=monospace]
5.15.0-79-generic
[/FONT]
```
Usually I have been lucky getting wifi to work on new laptops. Not this time.
```

[FONT=monospace][COLOR=#000000]lspci | grep Network [/COLOR]
02:00.0 [COLOR=#ff5454]**Network**[/COLOR][COLOR=#000000] controller: MEDIATEK Corp. Device 7902[/COLOR][/FONT]

```
A google search for "linux  MEDIATEK wifi 7902" leads to various forum discussions within the past few months, such as this one [https://www.reddit.com/r/linuxmint/comments/143khw4/mt7902_mediatek_wifi_driver/?rdt=41023](https://www.reddit.com/r/linuxmint/comments/143khw4/mt7902_mediatek_wifi_driver/?rdt=41023), all of which indicate that no driver is known. I then tried getting a usb wifi adapter. It also is not working. Here is the output of lsusb
```

[FONT=monospace][COLOR=#000000]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub [/COLOR]
Bus 003 Device 003: ID 3277:0022 Sonix Technology Co., Ltd. USB2.0 FHD UVC WebCam 
Bus 003 Device 006: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter 
Bus 003 Device 004: ID 0b05:1a62 ASUSTek Computer, Inc. 802.11ax WLAN Adapter 
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. Hub 
Bus 003 Device 005: ID 13d3:3579 IMC Networks Wireless_Device 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT]
```
And the output of dmesg | grep usb
```

[FONT=monospace][COLOR=#000000][    3.109595] [/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new interface driver [/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]fs [/COLOR]
[    3.109595] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new interface driver hub [/COLOR]
[    3.109595] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new device driver [/COLOR][COLOR=#ff5454]**usb**[/COLOR]
[    3.814423] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15 [/COLOR]
[    3.814428] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]1: New USB device strings: Mfr=3, Product=2, SerialNumber=1 [/COLOR]
[    3.814430] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]1: Product: xHCI Host Controller [/COLOR]
[    3.814432] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]1: Manufacturer: Linux 5.15.0-79-generic xhci-hcd [/COLOR]
[    3.814434] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]1: SerialNumber: 0000:00:0d.0 [/COLOR]
[    3.819862] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15 [/COLOR]
[    3.819867] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]2: New USB device strings: Mfr=3, Product=2, SerialNumber=1 [/COLOR]
[    3.819869] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]2: Product: xHCI Host Controller [/COLOR]
[    3.819872] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]2: Manufacturer: Linux 5.15.0-79-generic xhci-hcd [/COLOR]
[    3.819874] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]2: SerialNumber: 0000:00:0d.0 [/COLOR]
[    3.823472] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15 [/COLOR]
[    3.823476] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]3: New USB device strings: Mfr=3, Product=2, SerialNumber=1 [/COLOR]
[    3.823479] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]3: Product: xHCI Host Controller [/COLOR]
[    3.823481] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]3: Manufacturer: Linux 5.15.0-79-generic xhci-hcd [/COLOR]
[    3.823483] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]3: SerialNumber: 0000:00:14.0 [/COLOR]
[    3.833081] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15 [/COLOR]
[    3.833087] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]4: New USB device strings: Mfr=3, Product=2, SerialNumber=1 [/COLOR]
[    3.833090] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]4: Product: xHCI Host Controller [/COLOR]
[    3.833092] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]4: Manufacturer: Linux 5.15.0-79-generic xhci-hcd [/COLOR]
[    3.833094] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]4: SerialNumber: 0000:00:14.0 [/COLOR]
[    4.166610] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7: new high-speed USB device number 2 using xhci_hcd [/COLOR]
[    4.317732] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7: New USB device found, idVendor=05e3, idProduct=0610, bcdDevice=92.26 [/COLOR]
[    4.317751] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0 [/COLOR]
[    4.317756] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7: Product: USB2.0 Hub [/COLOR]
[    4.317760] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7: Manufacturer: GenesysLogic [/COLOR]
[    4.446674] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-8: new high-speed USB device number 3 using xhci_hcd [/COLOR]
[    4.605014] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-8: New USB device found, idVendor=3277, idProduct=0022, bcdDevice= 0.02 [/COLOR]
[    4.605026] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-8: New USB device strings: Mfr=2, Product=1, SerialNumber=0 [/COLOR]
[    4.605031] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-8: Product: USB2.0 FHD UVC WebCam [/COLOR]
[    4.605034] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-8: Manufacturer: Sonix Technology Co., Ltd. [/COLOR]
[    4.674602] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.3: new high-speed USB device number 4 using xhci_hcd [/COLOR]
[    4.779507] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.3: New USB device found, idVendor=0b05, idProduct=1a62, bcdDevice= 0.00 [/COLOR]
[    4.779519] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3 [/COLOR]
[    4.779525] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.3: Product: 802.11ax WLAN Adapter [/COLOR]
[    4.779529] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.3: Manufacturer: Realtek [/COLOR]
[    4.779531] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.3: SerialNumber: 00e04c000001 [/COLOR]
[    4.906599] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-10: new high-speed USB device number 5 using xhci_hcd [/COLOR]
[    5.056417] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-10: New USB device found, idVendor=13d3, idProduct=3579, bcdDevice= 1.00 [/COLOR]
[    5.056429] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-10: New USB device strings: Mfr=5, Product=6, SerialNumber=7 [/COLOR]
[    5.056434] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-10: Product: Wireless_Device [/COLOR]
[    5.056438] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-10: Manufacturer: MediaTek Inc. [/COLOR]
[    5.056441] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-10: SerialNumber: 000000000 [/COLOR]
[    5.134606] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.4: new high-speed USB device number 6 using xhci_hcd [/COLOR]
[    5.236123] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.4: New USB device found, idVendor=0bda, idProduct=8153, bcdDevice=30.00 [/COLOR]
[    5.236136] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.4: New USB device strings: Mfr=1, Product=2, SerialNumber=6 [/COLOR]
[    5.236141] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.4: Product: USB 10/100/1000 LAN [/COLOR]
[    5.236145] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.4: Manufacturer: Realtek [/COLOR]
[    5.236148] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.4: SerialNumber: 000001 [/COLOR]
[    5.249198] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new interface driver r8152 [/COLOR]
[    5.252674] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new interface driver cdc_ether [/COLOR]
[    5.253585] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new interface driver r8153_ecm [/COLOR]
[    5.330925] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-7.4: reset high-speed USB device number 6 using xhci_hcd [/COLOR]
[    7.452786] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new interface driver bt[/COLOR][COLOR=#ff5454]**usb**[/COLOR]
[    7.458774] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000] 3-8: Found UVC 1.00 device USB2.0 FHD UVC WebCam (3277:0022) [/COLOR]
[    7.469072] input: USB2.0 FHD UVC WebCam: USB2.0 F as /devices/pci0000:00/0000:00:14.0/[COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]3/3-8/3-8:1.0/input/input18 [/COLOR]
[    7.480480] [COLOR=#ff5454]**usb**[/COLOR][COLOR=#000000]core: registered new interface driver uvcvideo[/COLOR]
[/FONT]
```
A google search turned up this website: [https://superuser.com/questions/1685189/correct-driver-for-asus-usb-ax56-wifi-adapter](https://superuser.com/questions/1685189/correct-driver-for-asus-usb-ax56-wifi-adapter). One of the comments lead to this github repository:
[https://github.com/s-2/RTL8852AU_WiFi_linux_v1.15.0.1-0-g487ee886.20210714](https://github.com/s-2/RTL8852AU_WiFi_linux_v1.15.0.1-0-g487ee886.20210714), but make results in the following error:
```

[FONT=monospace][COLOR=#ff5454]**fatal error: **[/COLOR][COLOR=#000000]net/ipx.h: No such file or directory [/COLOR]
   20 |         #include [COLOR=#ff5454]**<net/ipx.h>**[/COLOR][/FONT]

```
A google search for that error leads to a github issue with a different Realtek driver, [https://github.com/aircrack-ng/rtl8188eus/issues/150](https://github.com/aircrack-ng/rtl8188eus/issues/150). I guess I could post an issue on the other driver, but I'm not even confident it is the one that I need. Further google searches also led to the repo [FONT=monospace][COLOR=#000000]ppa:kelebek333/kablosuz[/COLOR][/FONT], which I added with apt. At this point, I need to figure out if these is an uptodate driver for this Asus USB wifi adapter. If there is not, then I will need to return it. Does anyone recognize this device? Thank you.

---

### Post by chili555 on 2023-08-26
> [    5.134606] usb 3-7.4: new high-speed USB device number 6 using xhci_hcd 
[    5.236123] usb 3-7.4: New USB device found, idVendor=0bda, idProduct=8153, bcdDevice=30.00 
[    5.236136] usb 3-7.4: New USB device strings: Mfr=1, Product=2, SerialNumber=6 
[    5.236141] usb 3-7.4: Product: USB 10/100/1000 LAN 
[    5.236145] usb 3-7.4: Manufacturer: Realtek 
[    5.236148] usb 3-7.4: SerialNumber: 000001 
[    5.249198] usbcore: [COLOR="#FF0000"]registered new interface driver r8152 [/COLOR]
[    5.252674] usbcore: [COLOR="#FF0000"]registered new interface driver cdc_ether[/COLOR] 
[    5.253585] usbcore: [COLOR="#FF0000"]registered new interface driver r8153_ecm [/COLOR]
[    5.330925] usb 3-7.4: reset high-speed USB device number 6 using xhci_hcd You have no less than *four* wireless devices!! One of them actually has a driver, namely the 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter. In order to avoid conflicts, etc., I suggest that you unplug the others and let's concentrate on the above.

The comments about the built-in Mediatek are correct. We know of no way, currently, to get it working.

The driver mentioned above requires firmware. I suspect that's all you are missing. Please run:

```
sudo dmesg | grep r812
```

Let's see what is required but missing.

---

### Post by readableauthor on 2023-08-26
```

[FONT=monospace][COLOR=#ff5454]**fatal error: **[/COLOR][COLOR=#000000]net/ipx.h: No such file or directory [/COLOR]
   20 |         #include [COLOR=#ff5454]**<net/ipx.h>**[/COLOR][/FONT]

```
Can be fixed by this:

```

sudo apt install build-essential

```

---

### Post by Tikhon03 on 2023-08-26
So first, [COLOR=#000000]readableauthor, build-essential is already installed.

Chili555, I'm pretty sure that r1852 is for ethernet not wifi. I have a usb dongle plugged in with 3 usb ports and 1 ethernet port. It works, and it has to be plugged in for me to post anything by copy and paste. It does seem strange that several drivers are loaded. I may have to blacklist some of them, but I don't think they are all wifi. Now the command that you mentioned has no output. Did you mean sudo dmesg | grep r8152? Here is the output of that
[/COLOR]```
[FONT=monospace][COLOR=#000000]sudo dmesg | grep r8152[/COLOR]
[    7.754169] usbcore: registered new interface driver [COLOR=#FF5454]**r8152**[/COLOR]
[    7.966796] [COLOR=#FF5454]**r8152**[/COLOR][COLOR=#000000] 3-7.4:1.0: load rtl8153a-4 v2 02/07/20 successfully[/COLOR]
[    7.996226] [COLOR=#FF5454]**r8152**[/COLOR][COLOR=#000000] 3-7.4:1.0 eth0: v1.12.13[/COLOR]
[    8.004380] [COLOR=#FF5454]**r8152**[/COLOR][COLOR=#000000] 3-7.4:1.0 enx00e04d78ff2b: renamed from eth0[/COLOR]
[   99.795024] [COLOR=#FF5454]**r8152**[/COLOR][COLOR=#000000] 3-7.4:1.0 enx00e04d78ff2b: carrier on[/COLOR]
[/FONT]
```
[COLOR=#000000]And eth0 is usually ethernet. So, what next?[/COLOR]

---

### Post by chili555 on 2023-08-26
I made a mistake and I apologize for my mis-step. Your r8152 is, obviously, an ethernet device and it&#8217;s working just fine. I&#8217;ve cleaned my spectacles and switched my beverage to plain water. Let me try again.

Let&#8217;s do this: 0b05:1a62 ASUSTek Computer, Inc. 802.11ax WLAN Adapter

```
sudo apt update
sudo apt install &#8211;reinstall build-essential bc git dkms
git clone https://github.com/lwfinger/rtl8852au.git
cd rtl8852au
sudo dkms add .
sudo dkms build rtl8852au -v 1.15.0.1
sudo dkms install rtl8852au -v 1.15.0.1
sudo modprobe 8852au
```

You should be all set.

---

### Post by Tikhon03 on 2023-08-26
Hi Chili555! Thanks for posting again. No worries about the mistake. I tried your suggestion just now. It didn't work. It did compile cleanly without error, and the module is loaded:
```

[FONT=monospace][COLOR=#000000]lsmod | grep 8852au [/COLOR]
[COLOR=#ff5454]**8852au**[/COLOR][COLOR=#000000]              13606912  0 [/COLOR]
cfg80211              974848  1 [COLOR=#ff5454]**8852au**[/COLOR][/FONT]

```
But no wifi. I am not surprised because I tried something very similar before your last post. You see, the error that I was getting when compiling before was caused by a change as of kernel 5.15. I have 5.11 as a fallback, so I booted into it compiled loaded the module and it didn't work. My usb adapter is this one: [http://en.techinfodepot.shoutwiki.com/wiki/ASUS_USB-AX55_Nano](http://en.techinfodepot.shoutwiki.com/wiki/ASUS_USB-AX55_Nano). It looks like 8852au is only listed as a "probable" driver. It looks to me like it isn't. I also ran across this website which I wish I had found earlier: [https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md](https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md). Unless you have another suggestion, I think I will try to return this usb, and get one of the ones known to work.

---

### Post by chili555 on 2023-08-27
This is kind of unbelievable. The git page clearly says:

> This driver currently handles the following devices:

<snip>
ASUS USB-AX56 with USB ID 0b05:1a62

However, the relevent driver code says:

> usb_intf.c   Remove ASUS AX55 - it uses rtl8852bu   4 days ago

Indeed, your 0b05:1a62 device, although mentioned as included in the README, is not, as of four days ago, actually covered in the driver code.

Checking the code in his rtl8852bu repository, we clearly see in the driver code:

```
{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDOR_ID_ASUS, 0x[COLOR="#FF0000"]1a62[/COLOR], 0xff, 0xff, 0xff), .driver_info = RTL8852B},
```

So, let’s remove the incorrect driver and install the correct driver:

```
sudo dkms remove rtl8852au/1.15.0.1 –all
sudo depmod -a
git clone https://github.com/lwfinger/rtl8852bu.git
cd rtl8852bu
sudo dkms add .
sudo dkms build rtl8852bu -v 1.15.0.1
sudo dkms install rtl8852bu -v 1.15.0.1
sudo modprobe 8852bu

```
Is there any improvement?

---

### Post by Tikhon03 on 2023-08-27
Hi Chili555.  I can report partial success. I get the following error with sudo dkms add .
```

[FONT=monospace][COLOR=#000000]Error! Arguments <module> and <module-version> are not specified. [/COLOR]
Usage: add <module>/<module-version> or 
       add -m <module>/<module-version> or 
       add -m <module> -v <module-version>[/FONT]

```
However, I can get the module compiled and loaded by the following steps after cd rtl8852bu
```

make
sudo make install
modprobe 8852bu

```
The driver works! I have wifi now. But I don't have dkms support for some reason. At least I don't have to return the device.

---

### Post by chili555 on 2023-08-28
> But I don't have dkms support for some reason. At least I don't have to return the device.

I've raised an issue at the git repository: [https://github.com/lwfinger/rtl8852bu/issues/3](https://github.com/lwfinger/rtl8852bu/issues/3)

I hope it will be fixed soon and I'll advise.

---

### Post by chili555 on 2023-08-28
My issue got a reply from L. W. Finger:

> I do not support dkms. Those routines were added as a starting point. If you want to use them, you will need to debug them.

Therefore, I recommend that, when you get a kernel update from Update Manager, after the requested reboot, do:

```
cd rtl8852bu
make clean
make
sudo make install
sudo modprobe 8852bu
```

---

### Post by Tikhon03 on 2023-08-28
Thank you. That shouldn't be hard to do. You have have been a big help chili555.

---

### Post by chili555 on 2023-08-29
If you have any performance issues with th current driver, I suggest that you try this instead: [https://github.com/morrownr/rtl8852bu.git](https://github.com/morrownr/rtl8852bu.git)

Post back if you need a step-by-step.

---

### Post by Tikhon03 on 2023-08-29
I don't think I need step by step instructions. I will compare the drivers. I certainly don't have time to debug dkms right now, but may do that later.

---

