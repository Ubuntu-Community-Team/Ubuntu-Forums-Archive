---
title: "[SOLVED] Almost have wireless, need a little more help"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by dougtron on 2007-10-08
Hello! So I'm fairly happy, I finally got ndiswrapper to install the drivers that I needed.

When I type ```
ndiswrapper -l
```

it says "------ driver installed"

So the next step in finishing this all so I get the 'wlan0' option, I am instructed to type ```
modprobe ndiswrapper
```

but when I enter this modprobe code (either sudo, su- or just regularly) it just goes to the next line..nothing happens.

so, when i type iwconfig "wlan0" is still not even listed, it just shows eth0, eth, and lo.
so then I try ```
iwconfig wlan0 up
``` it tells me that wlan0 doesn't exist.

What's going on!? Thanks, Doug.

EDIT:::
Just to add on, I've just learned that it should say both 'driver installed' and list the hardware. Mine is not listing the hardware so I'm assuming, although the driver is installed correctly, it doesn't know which device it is going to. If that makes any sense, how do I point the drivers to the internal wireless card?

---

### Post by Floppyjoe on 2007-10-08
Does it also say hardware present when you do the ndiswrapper -l command?

---

### Post by dougtron on 2007-10-08
Hah, yeah I forgot to mention that. Read my above EDIT:::

It isn't associating the drivers to the hardware. No hardware present.

---

### Post by Floppyjoe on 2007-10-08
What do you get from the :
```
lspci
```
command?

---

### Post by dougtron on 2007-10-08
I'm not running my Ubuntu right now, If I must I'll switch and show you the lspci (it's tricky with the no-wifi thing)....but hopefully this is enough:

both LSPCI and LSUSB show my device, so it's recognizing it, and it gives some sort of xxxx : xxxx number next to it. It's a USB Internal Wireless RTL8187B which I've found the correct drivers for.

---

### Post by Floppyjoe on 2007-10-08
> **dougtron said:**
> I'm not running my Ubuntu right now, If I must I'll switch and show you the lspci (it's tricky with the no-wifi thing)....but hopefully this is enough:

both LSPCI and LSUSB show my device, so it's recognizing it, and it gives some sort of xxxx : xxxx number next to it. It's a USB Internal Wireless RTL8187B which I've found the correct drivers for.
Only one of those commands will show you the internal wifi device. Most likely the lspci command. The lsusb is mainly for USB plugin dongles.

---

### Post by dougtron on 2007-10-08
Alright sorry.

LSPCI:
```
doug@doug-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

and LSUSB
```
doug@doug-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
doug@doug-laptop:~$ 

```

note*-- Microsoft USB Device is my wireless mouse, and from what I understand the Realtek is my wireless card.

Thanks a lot, let me know if you can figure something out.

---

### Post by Floppyjoe on 2007-10-08
> **dougtron said:**
> Alright sorry.

LSPCI:
```
doug@doug-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```
If you had an internal wifi card it would be listed in the above as a network controller. Ethernet controller is for wired internet.
> 
and LSUSB
```
doug@doug-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
doug@doug-laptop:~$ 

```
If you plug in your wifi card in one of your usb ports then it would be listed above. It would be an external wifi device.

---

### Post by dougtron on 2007-10-08
Ok so from what you're saying, Ubuntu isn't even regonizing the internal wireless at all. Where do I go from here?

---

### Post by Floppyjoe on 2007-10-08
> **dougtron said:**
> Ok so from what you're saying, Ubuntu isn't even regonizing the internal wireless at all. Where do I go from here?
I'm saying you do not have an internal wifi device in your computer.

---

### Post by dougtron on 2007-10-08
Gah! Sorry to be such a pain, but that doesn't make sense because when running Vista I'm getting wireless. Dual boot system, Ubuntu and Vista. Obviously want to be running Ubuntu and not Vista at all. But only Vista is recognizing the wireless device. This is quite the mess but I don't want to give up yet, hah! 

Thanks.

---

### Post by Floppyjoe on 2007-10-08
> **dougtron said:**
> Gah! Sorry to be such a pain, but that doesn't make sense because when running Vista I'm getting wireless. Dual boot system, Ubuntu and Vista. Obviously want to be running Ubuntu and not Vista at all. But only Vista is recognizing the wireless device. This is quite the mess but I don't want to give up yet, hah! 

Thanks.
Do you have a wireless dongle plugged into one of the USB ports?

---

### Post by dougtron on 2007-10-08
No.

---

### Post by Floppyjoe on 2007-10-08
Well I have not ever heard of something like that happening before like Ubuntu not at least recognizing that there is an internal wifi device of some kind. It's a first for me.

Is this a laptop you are using?

---

### Post by dougtron on 2007-10-08
Yep its the laptop I'm using to type this all to you. Only, on Vista. I'm really bad at wording this sort of stuff but like I said from what I understand I think my internal wifi is weird and is regonized as USB...which is stupid because it's internal. Oh well, we'll see if anyone else reads this who understands. Thanks for your help anyway, I wont give up, I like Ubuntu too much!

Doug.

---

### Post by Floppyjoe on 2007-10-08
> **dougtron said:**
> Yep its the laptop I'm using to type this all to you. Only, on Vista. I'm really bad at wording this sort of stuff but like I said from what I understand I think my internal wifi is weird and is regonized as USB...which is stupid because it's internal. Oh well, we'll see if anyone else reads this who understands. Thanks for your help anyway, I wont give up, I like Ubuntu too much!

Doug.
I yahood your USB device and found this Url:
[http://forums.gentoo.org/viewtopic-p-4329059.html](http://forums.gentoo.org/viewtopic-p-4329059.html)
It might provide some insight. It might have something to do with your version of ndiswrapper.

---

### Post by dwibby on 2007-10-09
I also have a laptop with a Realtek RTL8187B Internal Wireless device (no, I haven't got it set up yet, either). If I understand what I'm seeing correctly, the internal card is tied to the internal USB port, of all things. 

Dougtron, > 08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01) is your Ethernet port on the outside (perhaps the back?) of your computer. 

I took the easy way out and used ndisgtk to install the net8187b (Win98, Win2000, WinXP, and X64; VistaX86 and VistaX64 are incompatible) driver from Realtek, but it returns with "Hardware present: No".

Running ndiswrapper -l shows net8187b as installed. Modprobe runs without errors. But iwconfig wlan0 returns

```
wlan0    No such device
```

Also, the laptop's wireless switch is on, but the status light is off.

If anyone has any ideas, or suggestions, I'd appreciate it.



My LSUSB:

```
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```


LSUSB -vv

```
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8197
  bcdDevice            2.00
  iManufacturer           1 Manufacturer_Realtek
  iProduct                2
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           81
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Wireless Network Card
    bmAttributes         0x80
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           9
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0b  EP 11 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0c  EP 12 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1 
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by dougtron on 2007-10-10
bump. anyone have any luck with this tricky internal wireless card? i'm thinking about buying a cheapo external card one to pop in, maybe it will work.

---

### Post by kevdog on 2007-10-10
ndiswrapper with the win98 drivers is what you want.

---

### Post by secureboot on 2007-10-11
I've been unable to find drivers (Windoze, even) for the 8197 wireless chipset - it sounds like people have had good luck, and they must exist somewhere.

Does anyone have a direct link?  I've tried searching at ndiswrapper and realtek.com.tw, but didn't have any luck in either place.  It sounds like at least one person in this thread has been able to find a .inf...

---

### Post by kevdog on 2007-10-11
Look at my signature for the troubleshooting post.  At the bottom of this post Ive posted a link to realtek drivers -- they might be 8187 drivers -- Im not sure

---

### Post by dougtron on 2007-10-12
So I suppose after trying many different things my main question is, when ndiswrapper shows the drivers installed correctly but lists nothing about hardware, does that mean it was the wrong set of drivers or the drivers didn't activate the hardware?

I mean, lsusb shows the Realtek wireless card, so it knows it's there. But I can't make any drivers "attach" to it, so to speak.

---

### Post by kevdog on 2007-10-12
Im not sure if this is the case or not.  I would keep working through, insert the ndiswrapper kernel module into the kernel and see what happens.  Check dmesg after this and see if you get any error messages.

---

### Post by rickhall on 2007-10-15
I just bought a Toshiba Satellite notebook and it has a RealTek 8187b integrated USB wifi adapter too. I have been trying to get it to install under Fedora, without luck as well.

My situation is the same as what has been described here. Under lspci I can see the RealTek ethernet adapter and under lsusb I can see the RealTek wifi adapter, but I have been unable to get any connectivity at all.

I have tried building rtl-wifi from source forge, building the drivers from RealTek, using ndiswrapper with various windows drivers, building linux 2.6.23 (this successfully turned on the wifi adapter light, but still no connectivity), and I also installed Fedora 8 (which includes 2.6.23 and also gave me the wifi light, but no connectivity).

I won't claim that I did everything correctly, but I tried to follow all of the steps at the various web sites and I have had no luck.

Anyone make any progress on this yet? Thanks.

---

### Post by rickhall on 2007-10-15
I should clarify, I can get connectivity under the RealTek ethernet adapter, but I have had no signs of connectivity under the integrated RealTek USB wifi adapter, other than getting it light to turn on.

---

### Post by skanxalot on 2007-10-16
I have the USB r8187B, and after receiving the linux drivers from Realtek, I followed the instructions in the readme.txt file and it worked great.

---

### Post by mowgli81 on 2007-10-16
could you post the output of "dmesg" after you modprobe ndiswrapper

---

### Post by rickhall on 2007-10-16
I am going to try to install Ubuntu 7.10 on my machine tonight. I will post a follow up after that.

Were you able to download the driver from RealTek or did they have to mail it to you? Could you share the link or email the package to me?

Thanks.

---

### Post by xvalentinex on 2007-10-16
I am interested in the result of this as well.

lsusb gives:
Bus 003 Device 003: ID 0bda:8197 Realtek Semiconductor Corp.

Ubuntu Device Manager says it is:
RTL8187B_WLAN_Adapter

ndiswrapper is a no go with any OS version
the module rtl8187 does not recognize it

scanxalot: The 8187B drivers were removed from the site some time ago.  I have e-mailed them asking about it.  This was just before posting this (no response yet).
[https://sourceforge.net/forum/forum.php?thread_id=1844833&forum_id=652149](https://sourceforge.net/forum/forum.php?thread_id=1844833&forum_id=652149)

RickHall:  Hate to break it to ya, I'm running 7.10 with the same result.   Realtek is good about getting Linux drivers out.  Probably just a waiting game.

If they send me the drivers I'll post them.  The replier to the link above said he would also send them.  I'll email him as well.s

Doing a  `echo -n "0x0bda 0x8197" > /sys/bus/usb/drivers/rtl8187/new_id` actually created the wlan0 device, but no scan results.

---

### Post by rickhall on 2007-10-16
Ok, I think I know what is going on, but I am still stuck.

I grabbed the driver from the RealTek web site for RTL8187B for WinXP, etc., but apparently this isn't the correct driver. If I do lsusb I see:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

But when I ndiswrapper -i on the driver I downloaded, I don't get conf files for this device, in /etc/ndiswrapper/net8187b I get:

0BDA:8187.F.conf  0BDA:8189.F.conf  net8187b.inf  rtl8187b.sys

Thus, when I modprobe ndiswrapper, it doesn't work because it doesn't detect the device. However, if I grab the driver off of my Vista partition and install it into ndiswrapper I get the following in /etc/ndiswrapper/net8187b:

0BDA:8197.F.conf  net8187b.inf  rtl8187b.sys

So, now ndiswrapper -l actually reports the device as present, it never has before. Unfortunately, if I do a modprobe ndiswrapper I get a bunch of unknown symbols (like the web page says I will) since ndiswrapper doesn't support Vista drivers yet.

So, in short, I need to find the WinXP drivers that will work with this device. Any advice?

---

### Post by rickhall on 2007-10-16
xvalentinex, definitely if you find them let me know. It looks like I am close if I can just get the drivers. If I don't hear from you, I guess I will mail the person at RealTek mentioned in the thread that you referenced. Thanks.

---

### Post by xvalentinex on 2007-10-16
You can get the drivers for all Win OS's [here](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

However, I tried Win98 and WinXP, and it did not work.  Perhaps you will have better luck.

Realtek has responded with the firmware.  It is attached to this post.
The PC I am trying this on is a coworkers so I don't have access to it now, however tomorrow I am going to try these steps.

These steps are adapted from the [rtl-wifi project](http://rtl-wifi.sourceforge.net/wiki/Installing#Debian.2FUbuntu).  I have not put these to the test yet, but this is the process I was going to take.  Note that Gutsy integrates rtl-wifi, and so the " Removing mainline ieee80211 Stack" should be unnecessary.  One may have to complete this process for Feisty.

**WARNING:  To repeat, this is what I plan to do.  I advise waiting until tomorrow and see if it works.  I will update this post if it does.**

**Installation in Gutsy**

**Preparing the System**
Open a terminal and install this:
```
sudo apt-get install build-essential subversion module-assistant
```
If you are root do not write "sudo".
And to finish run:
```
sudo module-assistant prepare
```
If you are root do not write "sudo".

**Getting package**
Download attached Source to a directory.
cd to directory and type
```
tar xzvf rtl8187B_linux_24\[1\].6.1024.0822.2007.tar.gz
cd rtl8187B_linux_24.6.1024.0822.2007/
```

**Making Module**
```
./makedrv
```

**Testing Module**
```
./wlan0up
sudo iwlist wlan0 scan
```

**If working install Module**
```

sudo cp /usr/lib/`uname -r`/kernel/drivers/net/wireless/rtl8187.ko ~/rtl8187.ko.old
sudo cp r8187/r8187.ko /usr/lib/`uname -r`/kernel/drivers/net/wireless/rtl8187.ko
sudo depmod -a
sudo rmmod r8187
sudo modprobe rtl8187
```

---

### Post by Speedoo on 2007-10-17
That's funny, here's my lspci, and I'm sending this through my wireless connection.
I looked in on this thread because I'm experiencing frequent disconnects and would like to make my wireless more stable.

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by xvalentinex on 2007-10-17
Hey Speedoo,

I realize your post is innocent enough, but in no way that I can see, is it pertaining to getting the RTL8187B Wireless adapter working.

If you're having intermittent wireless issues please start a new thread, or continue on a thread more suited for your problem.

If an `lsusb` reveals that you are indeed using a realtek wireless, welcome aboard.

> **Speedoo said:**
> That's funny, here's my lspci, and I'm sending this through my wireless connection.
I looked in on this thread because I'm experiencing frequent disconnects and would like to make my wireless more stable.

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
....

---

### Post by rickhall on 2007-10-17
Great, I will be waiting to hear about your progress. Thanks.

---

### Post by Speedoo on 2007-10-17
Sorry, I was trying to respond to the post stating that if the card doesn't appear in lspci, there's no card installed.  Under lsusb, I do indeed have a Realtek 8187 installed.  Not sure how my post ended up out of sequence, but if someone has a fix for my wireless dropping out for no apparent reason, I'd love to give it a try.
I should reiterate that my wireless DOES work, it's just not very stable.  Also, I recently replaced my old Netgear 802.11b router with a D-Link DIR-615 802.11n (draft) model to try to solve a wireless dropout problem on a different computer.  I'm not at all sure my problem is related to Ubuntu; could be the new router.
Sorry for butting in, and thanks for your understanding.

---

### Post by dougtron on 2007-10-17
xvalentine, i'm curious to see if this works for you. I also emailed RealTek and they sent me the drivers as well. I'll try to install them later this evening and see if it works, it looks promising. I'll keep an eye out for an update from you and see if you've done it before me.

---

### Post by xvalentinex on 2007-10-17
Unfortunately it did not work.  Our device is not recognized.  I emailed realtek about this, but they're going into the "give him the run around" mode.

> Dear Sir,
Could you check if your RTL8187B hardware IDs are "VID: 0BDA, PID: 8189" first?
Realtek official Linux driver only can support our own hardware IDs "VID: 0BDA, PID: 8189".
If yours are not, please contact with your card maker to get Linux driver. Thanks!
 
Best regards,
Jason

    ----- Original Message -----
    From:
    To: Realtek - Jason Chang
    Sent: Thursday, October 18, 2007 1:34 AM
    Subject: Re: RTL8187B Linux Drivers

    Hello Jason,

    Thanks for the prompt response.

    I followed the Readme.txt.  The driver compiled fine and inserted.

    However my wireless device was not recognized.  Here is some output.
    Any help would be greatly appreciated.

    Thank you,

    lsusb:
    Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.

    dmesg after insmod:
    [ 1015.704000] Linux kernel driver for RTL8187/RTL8187B based WLAN cards
    [ 1015.704000] Copyright (c) 2004-2005, Andrea Merello
    [ 1015.704000] rtl8187: Initializing module
    [ 1015.704000] rtl8187: Wireless extensions version 22
    [ 1015.704000] rtl8187: Initializing proc filesystem
    [ 1015.704000] usbcore: registered new interface driver rtl8187

    dmesg after `echo -n "0x0bda 0x8197" > /sys/bus/usb/drivers/rtl8187/new_id`
    [ 1596.116000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
    [ 1596.392000] rtl8187: Card MAC address is 00:16:44:12:81:6a
    [ 1596.744000] rtl8187: WW:Unknown RF module 6
    [ 1596.744000] rtl8187: WW:Exiting...
    [ 1596.744000] rtl8187: Initialization failed
    [ 1596.744000] rtl8187: wlan driver load failed
    [ 1596.744000] 

---

### Post by dougtron on 2007-10-17
Great. I'll play around with this...let me know if you figure anything out or if they contact you with any relevant information.

---

### Post by rickhall on 2007-10-17
Yeah, I had tried it too and didn't have any luck either.

I think it is pretty clear in your email that your have device 0bda:8197 (like me), so I am not sure why he is asking about 0bda:8189.

I thought the first part was the vendor ID, so I would have assumed that RealTek made the card, but he implies that someone else made it. Hmm. Not sure where this leaves us. :-(

---

### Post by rickhall on 2007-10-17
This is related:

[http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/)

He has patched the driver. He says it works for him. I did a quick pass on 7.10, but it still didn't work for me. I am wondering if I should try a clean install of 7.10 or under a different distro.

---

### Post by rickhall on 2007-10-17
I take it back. I am not sure if it was the above patched driver, but I am now seeing wireless networks under my Network Manager task tray icon!

I will try to connect and be right back! :-)

---

### Post by rickhall on 2007-10-18
Ok, I responding via my wireless connection! :-D

However, I notice some odd behavior that I don't know how to explain. 1) The detected networks have no signal strength displayed and 2) the signal for my home wifi is really really low, even though I am sitting right next to the router. On my Sony under Fedora I neither of these issues are true.

See the attached screenshot to see what I am talking about.

---

### Post by jbaerbock on 2007-10-18
Hmm never heard of that problem either. You must have a very special wireless. Btw reason your wireless works perfect with Vista is most likely because manufacturer had drivers for it and preconfigured it for you. Ubuntu on the other hand is being run with no manufacturer preconfiguration and therefore takes more of your time to get it up and going. Same would be the case with a fresh Vista install in most cases.

I was going to suggest typing sudo ndiswrapper -l to see what it says. If it gives an alternate driver in parenthesis after your installed one you would have to blacklist that driver. That is what I had to do since ndiswrapper does not blacklist whatever driver ubuntu thinks is right.

---

### Post by dougtron on 2007-10-18
I'm going to have to try this guys patched driver...sounds promising.

---

### Post by dougtron on 2007-10-18
YES YES YES!! This guys patched drivers do indeed work! The RTL8187B driver issue is solved! (for now)...

Thanks everyone!

-Doug

---

### Post by dougtron on 2007-10-18
I'm going to mark this thread as solved. If anyone in the future has problems with the RTL8187B internal wireless card, use the set of patched drivers at this website:

[http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/)

Thanks again, Doug.

---

### Post by kevdog on 2007-10-18
Can you make a summary of this thread -- the problem and the workaround -- very useful information here.  Just to make it a bit more cohesive.  Im kind of getting lost in the details.

---

### Post by xcuervo on 2007-10-18
Hello,

I've made the patched drivers available at [http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/"), so you can get at them without wading through my blog.

I've also patched them so you can specifically override the detected card; see the README at the URL above.

Hope this helps. :-)

---

### Post by kevdog on 2007-10-18
Good job on the compilation - but when would I need to recommend this patch to someone?? Give me some background on it so I can start recommending and linking to your page.

---

### Post by xcuervo on 2007-10-19
> **kevdog said:**
> Good job on the compilation - but when would I need to recommend this patch to someone?? Give me some background on it so I can start recommending and linking to your page.

The patch is required for USB devid 0bda:8197, the Realtek RTL8187B USB adapter, which is the onboard wireless (for some strange reason) for the Toshiba Satellite A215-S7407 (see [http://www.datanorth.net/~cuervo/laptop/]("http://www.datanorth.net/~cuervo/laptop/")). It may also work for others that report "Unknown RF module" with the module parameters "force_card=0x8189" or "force_card=0x8187". USB devid 0bda:8197 (the onboard USB wireless card in my aforementioned laptop) is hardcoded, since it was the card present in my laptop, and that was all I initially cared about; it writes "WW: Going dooh. >%^||" to klog/syslog when detected, then falls through a case statement to be handled the same as USB devid 0bda:8189 ("Going dooh" being a good sign).

Also, I replied to the gentleman from @realtek.com.tw who sent me the drivers in the first place with a description of the patch I applied to get the drivers working on my make and model of laptop. While I didn't receive a reply, I'm cautiously optimistic that he forwarded it to the relevant parties, and that future versions of the official driver won't require my patch(es).

---

### Post by xvalentinex on 2007-10-20
Great work Cuervo!

I spent last friday swapping the mini pci-express wireless card for an Intel one in my coworkers laptop.

Toshiba in all it's glory failed to recognize the new card.  Nothing like cutting corners to support one card, throwing standards out the window.  No wonder it's recognized as a usb device. :mad:

Anyways, /rant.  Thanks for the patched driver, I'm excited to get his laptop working, and he's excited to run Linux (first timer).

---

### Post by xcuervo on 2007-10-20
Happy to contribute, glad I could be useful. :-)

By the way, the box the patched rtl8187b driver is hosted on is going to be moving relatively soon, according to my buddy who's hosting it. Same URL, it might just be unavailable for a day or two while he gets situated.

If you're unable to get to [http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/") (and, please, only if! the following is my home box on DSL), I'm putting it up at [http://zerokarma.homeunix.org/rtl8187b/]("http://zerokarma.homeunix.org/rtl8187b/")

Happy hacking!

---

### Post by statik11 on 2007-10-22
good job on the patch cuervo but I am not able to get it to  work. Keeps saying unknown symbol in module the whole way down the list after I do a ./wlan0up, Maybe you could help since  I am very new at linux. 

Thank you

---

### Post by bns on 2007-11-01
Worked for me.  Thanks boss.  

You rock.  :guitar:

:)

---

### Post by statik11 on 2007-11-05
Well the patched driver didnt work and only one person tried to help but couldnt. I just rewrote the windows98 drivers and got it workin perfectly with ndiswrapper. If you cant get it to work with the patch then let me know and I'll email my driver to ya. Unless Im the only person in the world who couldnt get to work.

---

### Post by Buster95 on 2007-11-08
> **statik11 said:**
> Well the patched driver didnt work and only one person tried to help but couldnt. I just rewrote the windows98 drivers and got it workin perfectly with ndiswrapper. If you cant get it to work with the patch then let me know and I'll email my driver to ya. Unless Im the only person in the world who couldnt get to work.

Hello statik,
The patched driver didn't work for me. Nor did ndiswrapper and the w98 driver.
Any help would be appreciated.
Cheers

---

### Post by secureboot on 2007-11-20
Patched driver worked for me.

Is this likely to remain necessary, or will this make it into the mainline kernel soon?

---

### Post by chezbo425 on 2007-11-20
Fantastic work, it worked for me as well :D It'd be nice if something like this got comitted to the distros.

---

### Post by burnttoast11 on 2007-11-20
Ok, so I am having the same problem as everyone here and have been trying to fix it for quite a while now.  This thread looks promising, but it is very long and I need some clarification.  So, here are my questions.  (I just did a fresh install of gutsy)

1. How should I get ndiswrapper?  Should I download it through the package managers, or should I compile it myself?

2. When typing "lsusb" I get this:
Bus 006 Device 001: ID 0bda:8189 Realtek Semiconductor Corp.
So does this mean that I do NOT need the patched drivers since my cards ID is 8189?
So should I install the drivers that were emailed to xvalentinex and follow his directions? (See post #32)

3. Will I have to change my /etc/network/interfaces?

Thanks

---

### Post by burnttoast11 on 2007-11-20
Well, got ndiswrapper from synaptic and tried following xvalentinex's instructions, but I have a problem when I try making the module
```
./makedrv
```
I get the following:
```
peder@peder-laptop:~/wifi/rtl8187B_linux_24.6.1024.0822.2007$ ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.22-14-generic/build M=/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.o
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_scan_wq&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:433: warning: initialization from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:432: warning: unused variable &#8216;dwork&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_probe_resp&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:710: warning: ISO C90 forbids mixed declarations and code
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_retry_wq&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2253: warning: initialization from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2252: warning: unused variable &#8216;dwork&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2475: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2476: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2477: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2478: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2479: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:2480: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_rx_frame_softmac&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:1666: warning: &#8216;chlen&#8217; may be used uninitialized in this function
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_aes_encrypt&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c:87: warning: passing argument 1 of &#8216;crypto_cipher_encrypt_one&#8217; from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_init&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c:109: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c:125: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_deinit&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c:141: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_set_key&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp.c:423: warning: passing argument 1 of &#8216;crypto_cipher_setkey&#8217; from incompatible pointer type
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211-rtl.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211-rtl.ko
  CC      /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.22-14-generic/build M=/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.o
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_rx_urbsubmit&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:928: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_rx_manage_urbsubmit&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:948: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_rtx_disable&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:1249: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2214: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2221: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_initendpoints&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2271: warning: ISO C90 forbids mixed declarations and code
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2275: warning: ISO C90 forbids mixed declarations and code
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2304: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2250: warning: unused variable &#8216;i&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_deleteendpoints&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2322: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: At top level:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2429: warning: &#8216;struct struct_work&#8217; declared inside parameter list
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2429: warning: its scope is only this definition or declaration, which is probably not what you want
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_wmm_param_update&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2431: warning: initialization from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2433: warning: initialization from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_init&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2648: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:2696: warning: assignment from incompatible pointer type
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_adapter_start&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:3036: warning: unused variable &#8216;bInvalidWirelessMode&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:3035: warning: unused variable &#8216;SupportedWirelessMode&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:3034: warning: unused variable &#8216;InitWirelessMode&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:3033: warning: unused variable &#8216;ieee&#8217;
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_irq_rx_tasklet&#8217;:
/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187_core.c:3751: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8180_93cx6.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8180_wx.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8180_rtl8225.o
  CC [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8180_rtl8225z2.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_wx_get_freq" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko] undefined!
  CC      /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.mod.o
  LD [M]  /home/peder/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
peder@peder-laptop:~/wifi/rtl8187B_linux_24.6.1024.0822.2007$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8187.ko': -1 Operation not permitted
wlan0: ERROR while getting interface flags: No such device

```
I downloaded the build-essential subversion module-assistant.  Is there something else my system needs to make this work or are all of these warnings "ok"?


Thanks

---

### Post by skanxalot on 2007-11-21
This patch works great! Is there any way to avoid having to run ./wlan0up manually on every boot?

---

### Post by Roasted on 2007-11-22
I did everything the tutorial said, step by step. Somehow, I am not yet able to use my laptop wirelessly. After running the setup, the wireless option became available in my network settings. At this point I have wireless, wired, and modem or some garbage. I've done everything I could think of offhand. I removed all of the security restrictions from my LAN to make less hurdles to jump over. 

In short, how do I get the damn thing to work? I've gotten no errors up to this point. It's just once I unplug the wired ethernet cord, I just drop connection. Wireless doesn't take over. No idea what to do...

---

### Post by burnttoast11 on 2007-11-22
Shanxalot,
I'm not sure if this will work, but it is worth a shot:
Go to System->Preferances->Sessions and click add.  For "command," browse to the script that you want to load at startup.
Hope it works.

---

### Post by Roasted on 2007-11-23
I know I'm not the best with compiling and whatnot. Whenever I attempt it, something goes wrong.

Anyway, I tried to follow the solved option here as I read on page 5. However, I had no idea what to do with the newfound fixed patch which was downloaded as a tarball.

So I tried this after googling how to work with tarballs.


jason@jason:~$ tar xvzf rtl8187b-modified
tar: rtl8187b-modified: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jason@jason:~$ 



Of course, an error. 

In short - What do I do to get this thing working? Detailed steps would be fantastic.

---

### Post by kevdog on 2007-11-23
use tab to complete your entry

Its going to be something like this:

tar xvzf rtl8187b-modified.tar.gz

---

### Post by Roasted on 2007-11-23
jason@jason:~$ tar xvzf rtl8187b-modified-dist(2).tar.gz
bash: syntax error near unexpected token `('
jason@jason:~$

---

### Post by kevdog on 2007-11-23
rename the file to something without parentheses.

---

### Post by hoagies on 2007-12-09
Hi:

Please look at the Linux Mint Forum, under 'wireless':

[http://www.linuxmint.com/forum/viewtopic.php?f=53&t=7485](http://www.linuxmint.com/forum/viewtopic.php?f=53&t=7485)

Go to the very last post, from 'hansie'.....:  The driver itself can be 'directly' downloaded, (and installed),  from Realtek

---

### Post by statik11 on 2007-12-10
My Driver works perfectly with 8197 and automatically connects without having to do a /wlan0 up or adding anything to the session. But it has to be the 8197 for 8189 and others you need not ask for my help, because I dont know.

---

### Post by yolabingo on 2007-12-22
I just bought a Satellite A215-S7422 and installed Ubuntu 7.10, and am having trouble with the wireless adapter.  I have read MANY posts here and elsewhere but can only get so far.  I had no luck using ndiswan/ndiswrapper with the current Realtek WinXP/ME driver.  I have been attempting to use the modified Linux driver (module?) from [http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/)

I compiled it and can scan for networks, but am not able to connect to my Linksys wireless router.  I'm relatively comfortable using Linux, but have no idea how to troubleshoot from here.  It is possible I'm not configuring it corerectly.  The built-in tools in System->Network are also not able to get me connected.  Thanks much in advance for any assistance you can provide.  

Here's the steps I take after a reboot:

```
#lsusb
# Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.

```

```
#./wlan0up
```

```

#dmesg 
[44587.000000] Linux kernel driver for RTL8187/RTL8187B based WLAN cards
[44587.000000] Copyright (c) 2004-2005, Andrea Merello
[44587.000000] rtl8187: Initializing module
[44587.000000] rtl8187: Wireless extensions version 22
[44587.000000] rtl8187: Initializing proc filesystem
[44587.004000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[44587.272000] rtl8187: Card MAC address is 00:16:44:75:bc:47
[44587.612000] rtl8187: WW:Going dooh. >%^||
[44587.612000] rtl8187: PAPE from CONFIG2: 0
[44587.616000] rtl8187: Driver probe completed  

```

```

# iwlist wlan0 scan
wlan0     Failed to read scan data : Operation not permitted
```

I think this is because the interface is not up? Then I do:
```

# iwconfig wlan0 ap any
#ifconfig wlan0 up

```
I have tried using dhclient, the included ./wlan0dhcp binary, and assigning a static IP address to wlan0, all to no avail, using just the essid or MAC address with iwconfig, and followed the steps described in the Readme.txt file included with this driver.  At this point, here's where I'm at

```

# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:16:44:75:BC:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:8988 (8.7 KB)
```

```
# iwconfig wlan0
wlan0     802.11b/g  Mode:Managed  Channel=12  
          Access Point: Invalid   Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

However, I can see my network when I scan now, which gives me hope:

```
# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:CE:4A:6E
                    ESSID:"mojo"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:39  Signal level:0  Noise level:46
                    Extra: Last beacon: 1461ms ago
```

However, all attempts to connect to the router fail.  For instance:

```
# iwconfig wlan0 ap 00:14:BF:CE:4A:6E essid "mojo"
# iwconfig wlan0
wlan0     802.11b/g link..  ESSID:"mojo"  
          Mode:Managed  Channel=7  Access Point: 00:14:BF:CE:4A:6E   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

If I try
```
#dhclient wlan0
Listening on LPF/wlan0/00:16:44:75:bc:47
Sending on   LPF/wlan0/00:16:44:75:bc:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
```

And this creates wlan0:ava with a useless IP address (router assigns 192.168.1.x addresses)
```
#  ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:16:44:75:BC:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:7 overruns:0 frame:0
          TX packets:577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:23406 (22.8 KB)

wlan0:ava Link encap:Ethernet  HWaddr 00:16:44:75:BC:47  
          inet addr:169.254.6.81  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```

Please spare me the humiliation of having to go out and buy a stupid Prism pcmcia card.  I had hoped those days were behind me.

Thanks

---

### Post by iQuizzle on 2007-12-24
im having the same problems. i have a gateway mt3422 with realtek 8185 wireless card. wlan0 came up using the windows xp drivers, but i can't get it to work with my router. it doesn't seem to keep the essid when i try to set it.


iwlist shows this, so i know that it's finding the router.

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:14:01:9C:87
                    ESSID:"miller-keep-out"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

so i try to set the essid using: sudo iwconfig wlan0 essid miller-keep-out
```
$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


??

---

### Post by kevdog on 2007-12-24
What driver are you using??

lshw -C network

What type of encryption are you using? WEP or WPA

---

### Post by iQuizzle on 2007-12-24
here's lshw -C network:

```
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@06:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:f4:a7:58
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Realtek,02/01/2007,5.1097.0201. latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11b
       resources: ioport:6000-60ff iomemory:b3400000-b34001ff irq:11

```

i'm using a WEP router and the realtek windows xp driver that matches my card along with ndiswrapper.

---

### Post by kevdog on 2007-12-24
Can you post 

ndiswrapper -l

And have you seen this thread:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by iQuizzle on 2007-12-24
the driver is loaded properly (i think). here's the result of ndiswrapper -l

```
$ ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)

```

also, i followed your guide, but still nothing:

```
$ sudo ifconfig wlan0 up
$ sudo iwconfig wlan0 essid "miller-keep-out"
$ sudo iwconfig wlan0 key s:xxxxx
$ sudo iwconfig wlan0 mode Managed
$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:c0:a8:f4:a7:58
Sending on   LPF/wlan0/00:c0:a8:f4:a7:58
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

after doing all that i checked iwconfig and have the same result:

```
$ sudo iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Encryption key:6174-7472-74   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


again with the essid not getting set :/ is it possible that the driver is not getting loaded? i noticed that your driver says ndiswrapper+<driver name>, but mine doesn't. i just assumed that it worked because i don't have a wlan0 until i modprobe ndiswrapper.

---

### Post by iQuizzle on 2007-12-24
boo-yeah. got it working. for the realtek 8185 card in my gateway mt3422 and ubuntu 7.04 kernel 2.6.20, it works to compile the drivers from source off of the realtek website. i just gave up on the ndiswrapper method after trying for a few days to get it to work.

---

### Post by kevdog on 2007-12-24
Can you post a brief explanation on how you did this??  I like this solution, I may reference it at the bottom of my command line thread!

---

### Post by Cabldevil on 2007-12-26
I just got a gateway laptop with the 8187B realtek.   I have compiled the modified linux driver and I can get the adapter up and see my network but cannot connect.  

Wireless does not use any wep or wpa  just MAC filtering.  I have it running fine under Vista.  I am close but when I manually setup or use network manager in 7.10 using the modified realtek driver it refuses to connect to my router. 

I am at work now but would post any information that can help me.  

Should I ditch the Modified driver and go with ndswrapper?

Thank You

---

### Post by kevdog on 2007-12-26
PM iQuizzle -- Im interested in his solution and Im sure it will work for you.  What is the link for downloading the realtek driver source?

---

### Post by Cabldevil on 2007-12-26
Here is the link for the modified driver.

[http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/")

---

### Post by kevdog on 2007-12-26
Seems pretty to use --  what is the problem you are having. If you compile the driver you can verify it will work by bringing the driver up and then connecting from the command line.  Do you need some help?

---

### Post by Cabldevil on 2007-12-26
It refuses to connect to the router.  All I need to do is iwconfig ESSID and then bring up DHCP  but it never gets a IP addy.

Again no wep or wpa2  just mac filtering  and ssid is not broadcast.

Thank you

---

### Post by kevdog on 2007-12-26
First lets do a little troubleshooting.

Broadcast the ESSID right now.

Load the driver (kernel module) with the 
./wlan0up 
statement.

Then do a 
iwlist scan

Is your access point seen?

Then try connecting manually from the command line.  Instructions are in a thread I wrote referenced in my signature.

Again the statment 
./wlan0down 
will unload the kernel module.

I believe these two statements are equivalent to modprobe and modprobe -r

I read about possible having to force the ID of your card.  Do you know the ID of your card.

---

### Post by kevdog on 2007-12-26
Just real quick -- you are using a USB wireless device or dongle?

---

### Post by Cabldevil on 2007-12-26
No Dongle  it is internal usb  (part of the laptop).
I have the hardware address and device ID at home I will check and post when I get back home (should have took the laptop to work with me hehe)

I will follow your directions and post the reply tonight. Thank you for your reply!

---

### Post by kevdog on 2007-12-26
Great -- internal USB devices -- kind of forgot about those, sorry.

---

### Post by Cabldevil on 2007-12-26
Oh BTW I am running64 bit not 32.  Not sure if that will matter but I think its a 32 bit driver.

---

### Post by t5noel on 2007-12-26
If you look back at the lsusb list you'll find the realtek device listed. It is the wireless device. Now getting it to work has been a challenge for me as well. Good Luck.

---

### Post by Cabldevil on 2007-12-26
ok just got in =)

sudo ./wlan0up
all good

sudo iwconfig wlan0 essid "my_id"

All good  ( i did turn broadcast essid on)

sudo dhclient wlan0

finally got no dhcpoffer received

just wont connect with the modified driver. Maybe ill try the native driver?  or go 32bit 7.10? 

thanks

---

### Post by kevdog on 2007-12-26
with the driver up can you post

iwlist scan
lshw -C network

---

### Post by Cabldevil on 2007-12-27
```
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:77:e6:ab
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.152 multicast=yes wireless=802.11b/g linked

```

I took the laptop to work upwent the driver  then i did a scan and boom it showed up in network manager like it did at home. But when I clicked on the network it got an ip and connected to the AP!!!

So something fishy about my mac filter at my house.  But with my laptop 2 feet from the AP I only show 30% in network manager and this in iwconfig

> wlan0     802.11b/g linked  ESSID:"router2"  
          Mode:Managed  Channel=11  Access Point: 00:13:10:B6:B0:45   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



THink I should use the black list driver kevdog?

---

### Post by kevdog on 2007-12-27
Try a bunch of different driver -- the blacklisted driver, ndiswrapper, and the patched driver.  See which one works for you.  Remember with the blacklisted driver you are going to have to add the extra character at the end of the essid statement.

---

### Post by Cabldevil on 2007-12-27
tried black listed drivers  I dont think they are even in the latest x64 kernel


```
cabldevil@cabldevil-laptop:~/rtl8187b-modified$ sudo modprobe r818x
FATAL: Module r818x not found.
cabldevil@cabldevil-laptop:~/rtl8187b-modified$ sudo modprobe r8187
FATAL: Module r8187 not found.

```

I will try Ndiswrapper next with a 64 bit xp driver

I will also check realtek website for 64 bit version of the linux driver

---

### Post by MASTIFFKING on 2007-12-27
ALright! Sorry to come into the conversaion so late in the game. I have been searching and searching for the answers I found in this Thread. I have read all of the post prior to this one and I am still stuck.
I installed the modified driver and it worked. Only problem is now I can't connect using WPA. Any suggestions. Not quite sure how to setup wpa
Thanks,

---

### Post by kevdog on 2007-12-28
setting up wpa is another topic.  You need to install the wpa supplicant package.  Not sure what GUI (or if any) you are using to make the connection for you.  I think in the README.txt file contained in the modified driver download there was a hint on how to setup the wpa_supplicant.conf file to use with WPA.  I would definitely go back and reread the documentation.  Another source similar to what is contained in the documentation is contained in my tutorial under connecting from the command line.  This should allow you to set up the wpa_supplicant.conf file and then reference this file from the command line to complete the wireless initialization.  
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

There is also Wieman's guide which tries to automate the process:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

If network manager is not working for you, you could try WICD. imdano - the creator of WICD -- seems to have disappeared from the forum's later, so I dont know how development of the WICD tool is coming along.  Its currently functional, however I know he was going to add new features.  Not sure if he is still doing so.

---

### Post by iQuizzle on 2007-12-28
sorry, for the late response, but here's what i did. (for reference, i have a gateway mt3422 laptop with a realtek 8185 wireless card running on ubuntu 7.04 feisty).

**problem:** when i first installed ubuntu, no wlan0 device came up, so i went to the realtek site and downloaded the windows xp driver. then i installed ndiswrapper and ndiswrapper -i'ed the driver. after modprobing ndiswrapper, wlan0 came up in ifconfig so i thought the windows xp driver was working. wlan0 was able to find available wireless networks, but when i attempted to set the esside or key, it wouldn't get set in iwconfig. i blacklisted all the drivers that i thought might interfere with ndiswrapper, but to no avail. i even tried using ndiswrapper with drivers from different windows versions (98,me,xp 64) but nothing changed.

**solution:** realtek lists a native linux driver on their website for the realtek 8185L card. i rmmoded the ndiswrapper driver that i had previously used and did the following:

1. downloaded and unpacked the driver found here: [realtek 8185 drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")
you should check out the readme file included with the drivers
2. ran the **sudo ./makedrv** file included
3. did **sudo ./wlan0up** also in that folder
4. checked to see if i had wlan0 running: ifconfig
5. looked to make sure i had available networks: iwlist wlan0 scanning
6. set the essid of the network that i wanted to use: sudo iwconfig wlan0 essid "xxxxxx"
7. set the key of the network that i wanted to use: sudo iwconfig wlan0 key "xxxxxxx"
or for an ascii key: sudo iwconfig wlan0 key "s:xxxxxx"
8. checked that the information had now been set on the device: "iwconfig wlan0"
9. acquired an ip from the router: "sudo dhclient wlan0"

at this point i just checked ifconfig to make sure i had a local ip (192.168.0.xxx) on my wireless card and when i saw that i did, i was on my way. i hope this works for other people as well. the driver says kernel version 2.6.22 on the site, but i think as long as you have a 2.6 kernel that is less that revision 22 it'll work for you...for reference i did this on 2.6.20

---

### Post by Cabldevil on 2007-12-28
Just an update for the 8187b:

No driver is working under ndiswrapper.  The Modified and the original linux driver from realtek does work but only connects with very low signal even next to the router.  If I move over a room it drops (maybe a tweek you know of kevdog to fix that).

Hate to go back to vista on my new xmass laptop but I may have to - know sound no webcam  making it tuff with 7.10.  I know that usually the case with new laptops I might just wait for the next release.

BTW i have a Gateway T1616

---

### Post by statik11 on 2008-01-12
If you are having problems with cuervo's driver or the linux drivers. I have the fix for you. Its only for rtl8187b with number ending in 8197 mostly found in Toshibas. Ive used it now for a couple of months or so and it works flawlessly it connects to routers and networks with encryption. Just drop me a line and I would be happy to send it to you. Dont know if it is compatible with 64 bit but I could sure make one and have you test it. 

StatiK

---

### Post by mac8706 on 2008-01-24
I have a toshiba laptop and i have tried cuervo's driver for mt rtl8187b on the 8197 and it doesn't work, tried ndiswrapper and doesn't work, tried unmodified driver and doesn't work, i think that this laptop is jsut screwed all to hell and i am thinking about selling it and getting some of my money back

---

### Post by kevdog on 2008-01-24
> Its only for rtl8187b with number ending in 8197 mostly found in Toshibas

Where do you find if your card version ends in 8197?  Could you provide a command with the output that would show this?

---

### Post by Macrophage6 on 2008-01-25
I have a Toshiba Satellite A205-S5804 laptop. Device Manager in Vista shows my internal wireless adapter as 'Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter' and lsusb Kubuntu 7.10 shows it as ‘0bda:8197 Realtek Semiconductor Corp.'

I tried to use the blacklisted drivers suggested in [kevdog's guide]("http://ubuntuforums.org/showthread.php?t=571188"), but didn't get anywhere since 7.10 doesn't seem to have these drivers. I tried using the drivers for 98 and XP that I got from the bottom of [Realtek's driver page]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") with ndiswrapper, but, although the driver seemed to install successfully, my adapter wasn't recognized. I tried [cuervo's modified driver]("http://www.datanorth.net/~cuervo/rtl8187b/"), and that let me connect (reliably by using the commands in kevdog's guide) to an unencrypted signal--though the signal showed as only 30% about two rooms from the router when Vista shows it as closer to 90%. (I'm not so sure that that was the real signal strength though, since my connection seemed stable.) Unfortunately, I cannot connect with WPA encryption. (I briefly tried WEP, which also didn't work (but I didn't entirely know what I was doing)--but WEP is nearly useless now anyway, isn't it?)

From what I can tell, statik11's rewritten driver seems like a good match for me, but after sending a private message to statik11 about a week ago requesting it I still haven't received a reply. If anyone has statik11's driver, or has an idea of how I can get WPA working with cuervo's driver, I'd really appreciate the help.


Thanks,
Macrophage6

---

### Post by kevdog on 2008-01-25
i dont know if that driver does wpa.  you should be able to get WEP working from the command line however -- Im fairly certain about that.

---

### Post by runt on 2008-02-06
i have gotten my 8187b working using cuervo's driver, but only with WEP and not WPA.  i don't want to have to switch back to WEP if i can help it, but i don't want to go back to vista neutered edition (i mean home basic) no matter what.  i will install xp before i go back to that mess.......

---

### Post by ReyJames on 2008-03-14
I wanted to thank everyone that has posted to this thread.
I just installed Ubuntu 7.10 and was having the exact problem that many of you have had.

Thanks to the very detailed trail of trails and errors that has helped me to get my WiFi up and running.

Thanks again!

---

### Post by pabloezekiel on 2008-03-21
hello everyone I'm a newbie and I got cuervo's patch to work does anybody know how to make the network manager show the wireless networks in the area?

---

### Post by lacie on 2008-03-27
Hello everyone, i tried to apply the patch, but i get the Error Messages:
```
lacie@lacie-laptop:~/Desktop/rtl8187b-modified$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

```

But the files are there.. anyone had this problem?
 I tried with /without sudo, i tried the 
#  rtl8187b-modified-dist.tar.gz
# rtl8187b-modified-jadams-2-1-2008.tar.gz
but with both i get the same error..

---

### Post by lacie on 2008-03-27
I tryed now several drivers with ndiswrapper.. none worked..
and this patch doesnt seem to work for me.. can anyone help?
I still get the same error message as above.

---

### Post by post_erasmus on 2008-04-01
lacie,
the following dirver got me, a linux/ubuntu newbie most of the way there.  I'm having some minor WEP issues, but I don't think that's the driver's fault.

Go to [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B") and download the windows driver near the bottom of the page.  

When you extract it, open up the Win98 subdirectory, open up the .inf file,  and go to the section that says IDs for 98Se/ME/2K/XP. These two lines should be there

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB/VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200

Add the line

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

after them. Load it with ndiswrapper and you ought to have a wlan0 at your disposal.  

This ONLY worked for me when starting out with the 98 driver, so make sure you don't edit one of the other myriad .inf files in the zip from realtek.  Let me know if it works.

---

### Post by acirilo on 2008-04-05
> **post_erasmus said:**
> lacie,

This ONLY worked for me when starting out with the 98 driver, so make sure you don't edit one of the other myriad .inf files in the zip from realtek.  Let me know if it works.

ok... i've done this.. but it still isn't shown in my ifconfig... ? where am i going wrong

ive restarted networking

on a toshiba a205-s5809

---

### Post by ercork on 2008-04-06
Thanks post_erasmus - your solution about adding the extra line to the Win98 inf file worked perfectly for me. I now have wireless working on my satellite a205-S5804 with all the extra bits too - signal strength monitor, WEP, WPA, etc.

acirilo - be sure after you install the amended driver in ndiswrapper to do all the extra bits and pieces mentioned in an earlier post, i.e., 

sudo depmod -a



sudo modprobe ndiswrapper



sudo ndiswrapper -m
"module configuration already contains alias directive"



While the "sudo ndiswrapper -m" supposedly sets up the module for loading, it seems sometimes that is not the case. To be safe, we also need to add ndiswrapper to the kernel modules list to be loaded at boot:



cd /etc



sudo gedit modules



add the following line to the end of that file:



ndiswrapper



save the file, exit, and then REBOOT.



When the boot comes back up, check you networking icon to see if the wireless networks are listed.

---

### Post by statik11 on 2008-04-06
Hello fellow Ubuntu users, Im sorry I have not been able to respond to most users for the fact that Yahoo will not allow me to foward mail to Gmail users which is the majority of you guys. Also I have been very busy with work which I no longer have, haha. If you would still like my drivers I made a webpage about 4 minutes ago to further assist you. 
[www.geocities.com/dvs_statik](www.geocities.com/dvs_statik)  Please follow the instructions on the site. If you still have any questions please email me, and I will try to respond in a timely fashion. 

StatiK

---

### Post by acirilo on 2008-04-06
> **ercork said:**
> Thanks post_erasmus - your solution about adding the extra line to the Win98 inf file worked perfectly for me. I now have wireless working on my satellite a205-S5804 with all the extra bits too - signal strength monitor, WEP, WPA, etc.

acirilo - be sure after you install the amended driver in ndiswrapper to do all the extra bits and pieces mentioned in an earlier post, i.e., 

sudo depmod -a



sudo modprobe ndiswrapper



sudo ndiswrapper -m
"module configuration already contains alias directive"



While the "sudo ndiswrapper -m" supposedly sets up the module for loading, it seems sometimes that is not the case. To be safe, we also need to add ndiswrapper to the kernel modules list to be loaded at boot:



cd /etc



sudo gedit modules



add the following line to the end of that file:



ndiswrapper



save the file, exit, and then REBOOT.



When the boot comes back up, check you networking icon to see if the wireless networks are listed.
 
yes thanks.. i posted the solution with the edited driver on my blog
[http://mycirilo.com/?p=24](http://mycirilo.com/?p=24)
much thanks.

---

### Post by heavenslade23 on 2008-04-16
I also have an A205-S5804 that ALMOST has wireless.  :)

I'm fairly certain everything is set up mostly correct...I used ndiswrapper with the Win98 driver.  I can see all the wireless networks within range, I just can't connect.  If I use manual connect mode I can't connect to any webservers.  If I use roaming mode I can see all the nearby networks with signal strength, I just can't connect.  I've typed in many of the commands listed in this thread and all of them have returned the correct result.

One of two things happens when I try to connect in roaming mode...either the network icon turns into totally grey signal strength bars, or I'm prompted for a password and it turns into the two swirly dots connecting icon and neither of them ever turn green and it just goes on forever.

---

### Post by acirilo on 2008-04-16
> **heavenslade23 said:**
> I also have an A205-S5804 that ALMOST has wireless.  :)

I'm fairly certain everything is set up mostly correct...I used ndiswrapper with the Win98 driver.  I can see all the wireless networks within range, I just can't connect.  If I use manual connect mode I can't connect to any webservers.  If I use roaming mode I can see all the nearby networks with signal strength, I just can't connect.  I've typed in many of the commands listed in this thread and all of them have returned the correct result.

One of two things happens when I try to connect in roaming mode...either the network icon turns into totally grey signal strength bars, or I'm prompted for a password and it turns into the two swirly dots connecting icon and neither of them ever turn green and it just goes on forever.

it could be that the driver file needs to be modified in this line

    %RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200 

if you run the sudo lsusb command it shows usb connected hardware.. then replace the PID with your PID number then unload the old driver file using ndiswrapper then go thru the steps with the new driver file..

---

### Post by post_erasmus on 2008-04-19
ercork's directives are definitely solid, but the other option and the one I originally used, is to load the modified driver using the ndisgtk utility.  It's basicaly a GUI for ndiswrapper.

---

### Post by heavenslade23 on 2008-04-20
> **post_erasmus said:**
> ercork's directives are definitely solid, but the other option and the one I originally used, is to load the modified driver using the ndisgtk utility.  It's basicaly a GUI for ndiswrapper.

This is what eventually got everything working for me with my Toshiba A205-S5804.  Once you've got the Win98 driver from Realtek's site and the modified inf, it's like a 3-4 click process to get it installed.  Once I had done that I was able to see and log on to my network without any further issues.  I only tried roaming mode but I suppose manual connect would have worked just as well.

I don't know what the earlier issue was....I think maybe I got my wires crossed reading so many different conflicting solutions for getting it working that I was trying the original inf file instead of the modified one.

---

### Post by dougtron on 2008-04-24
The modded drivers by cuervo and others are not currently working in Hardy distro. Anyone who has knowledge on this subject please see this forum, we need help.

[http://ubuntuforums.org/showthread.php?t=765671](http://ubuntuforums.org/showthread.php?t=765671)

---

### Post by pana.corbului on 2008-04-26
I have a toshiba l40-14f with a rtl8187b chipset wireless card. I've been google it all day long trying to connect to my linksys router and the only solution in hardy was to install using ndiswrapper this modified win98 driver.

It connects on unsecured wifi and wep using 128 hexa key using cli:

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "your_network_essid"
sudo iwconfig wlan0 key your_wep_key
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Hoping that someone will manage to connect to wifi usings wpa.

---

### Post by Danny1262 on 2008-04-26
To all trying to install windows wireless drivers with ndiswrapper,
after you install the driver, you must (gasp!) REBOOT the machine (yeap, just like Windows) so the driver will load. You may have to reboot a couple more times after each major step, but it will work!

Ubuntu's BIGGEST weakness is the wireless support for cards that do not use free drivers. 
Aslo, I just installed 8.04 and discovered that ndiswrapper and ndisgtk (ndiswrapper gui) are not inlcuded in the live cd. 
Not good guys!

I have dowloaded ndiswrapper and hope to get my bellsouth wireless going this evening. I know it will work because I made it work work in Gutsy.

Otherwise the OS delivers!!

---

### Post by Daniel591992 on 2008-04-27
> **post_erasmus said:**
> lacie,
the following dirver got me, a linux/ubuntu newbie most of the way there.  I'm having some minor WEP issues, but I don't think that's the driver's fault.

Go to [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B") and download the windows driver near the bottom of the page.  

When you extract it, open up the Win98 subdirectory, open up the .inf file,  and go to the section that says IDs for 98Se/ME/2K/XP. These two lines should be there

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB/VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200

Add the line

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

after them. Load it with ndiswrapper and you ought to have a wlan0 at your disposal.  

This ONLY worked for me when starting out with the 98 driver, so make sure you don't edit one of the other myriad .inf files in the zip from realtek.  Let me know if it works.

So, that worked for me, but I'm having the same WEP issues as you. It just wont connect at all. Anyone have any suggestions?

To get the wireless working in the first place, I downloaded Realtek's Win 98 driver, modified it with the instructions from the post above, installed NDISWRAPPER and the GUI, installed the Win 98 driver, and rebooted.

What can I do to make WEP work?

---

### Post by pana.corbului on 2008-04-30
> What can I do to make WEP work?

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "your_network_essid"
sudo iwconfig wlan0 key your_wep_key
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

LATER EDIT:[b]
I've managed to connect using wpa and wpa2 [AES] on realtek 8187b! All from knetwork manager [I'm using kubuntu] Didn't worked from cli. All I had to do is to click 'connect to other network' [althought my network was displayed but when i was trying to connect it was letting me to select only wep encryption] and select the encryption type and there you go![/b]

---

### Post by Midnightsun on 2008-05-09
I downloaded the modified driver from here: [http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/]("http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/") but seem to be falling at the first hurdle.
```
$ sudo ./makedrv
[sudo] password for m1dn1ght: 
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

```

So unless I'm mistaken, it's not compiling correctly? 

I'm running Hardy.  My lsusb output is:
```

7$ lsusb
Bus 003 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Don't know why there's 2 entries there for Realtek.  Under windows it shows as Realtek 8187b.

The sick irony is that the other day I was fiddling around with it so much that I must have inadvertedly fixed it as it worked briefly, but following a reboot I must have changed something and it ceased to work.  The output I get from typing ./wlan0up (even after ./wlan0down) is:

```
$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device

```

I may be missing something blatantly obvious, but can't figure this out.

Thanks in advance for any advice

---

### Post by Serdna on 2008-05-13
> **Midnightsun said:**
> I downloaded the modified driver from here: [http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/]("http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/") 

Same problem here. You have to download the patch for the 2.6.24 kernel from [http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/"), apply it (inside rtl8187b-modified I executed "patch <2.6.24.patch" and I went giving the correct path/filename each time it asked).

Good luck!

---

### Post by mryddlin on 2008-06-05
Hey all,

I am having the same issues with the realtek drivers (modified linux and ndiswrapper).

I have a Toshiba A210 with a realtek wireless USB card (8197 from lsusb). I can get the system connected using the either driver but only on unsecured connections.

I have gotten it to connect a few times using WPA but it drops two seconds afterwards.

I am using Hardy with all the latest patches installed, going to try Kubuntu instead to see if that helps at all (some people have had better luck with Kubuntu and WEP).

I now some people have been able to get WEP to work from the cli but I haven't had any luck, only open wireless connections work.

---

### Post by Pedro_Pdr on 2008-06-11
I tried everything spend hours searchig info done everything and cant conect. So i bought USB pen Wireless WUSB54GC. And works fine now with USB pen. Only 15&#8364; (here in Portugal) and works fine.

---

### Post by bravo331 on 2008-07-05
pedro_pdr I LOVE your solution. I have already spent way more than $30-$40 dollars worth of my time to try to resolve this issue. I am trying real hard to love linux but issues like this are driving me up the wall and making me wonder why I bother when I have a perfectly good and fully functional Windows partition on my Gateway T1616...

 Compiz Fusion Cube by itself makes Ubuntu better than Windows.

---

### Post by Bobmatt on 2008-07-13
I have a Tosh L40-17M which uses the Realtek 8187b i have tried everything and still Ubuntu doesn't see the card, my Negear WG111v2 works fine straight from the box. i would prefer to use the internal but have spent to many hours trying to find the solution this is my lsusb-

bob@bob-laptop:~$ lsusb
Bus 007 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

I'm giving up now. but if anyone has a solution please post it.

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ

---

### Post by funkythumb on 2008-07-20
> **dougtron said:**
> Ok so from what you're saying, Ubuntu isn't even regonizing the internal wireless at all. Where do I go from here?

I've got some possible good news, and some very possible bad news. I've been trying to set up my sister-in-law's brand new Toshiba Satellite 205 (I think same as yours.)

It took me a while, but I found out there's a physical switch at the front of the laptop (left of the blue status lights) that turn the wireless on/off. Slide it to the right, and you'll see an orange light turn on, along with the wireless card!

Bad news, I've had NO luck getting wireless to work with Hardy. Tried Ndiswrapper, madwifi, and no luck. By default, Hardy does detect the wireless loads the resticted drivers, but just won't work. Looks like my sister-in-law will have to keep Vista... {shudder}.

---

