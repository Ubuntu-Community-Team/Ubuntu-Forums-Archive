---
title: "Bluetooth Adapter Exists, not discovering &amp; not discoverable"
date: 2015-01-12
forum: Networking &amp; Wireless
---

### Post by taylor15 on 2015-01-12
Im really lost on this one, I must have gone through 100 forum threads on bluetooth. 

_**SHORT VERSION**_
Essentially, as the title says, I can see my bluetooth adapter exists and is powered, but it is not discovering, nor is it discoverable when I make it.
[U]
[B]LONG VERSION
[/B][/U]I recently got this Toshiba Satellite C50-B03E as a cheapy to nuke and hack around on. It came with windows, which I nuked, and put on 14.10. The laptop comes with an integrated bluetooth adapter (no specifics given in documentation, just a toshiba bluetooth adapter). Anyway, it seems that ubuntu detects it, and powers it etc, however when I search for bluetooth devices (I have many different types discoverable around it), it cant pick up any of them.

I've tried simple - from making sure its unblocked, and restarting the service, to more complicated - reinstalling the stack, updating to bluez 5.23 (over stock 4.101), recompiling ath3k and btusb making sure that my device and vendor id is included. I just cant get it to discover!! Any help would be greatly appreciated, i will post outputs of tests below

**uname -a**
```
Linux taylor-dev 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


```

[B]hcitool scan
[/B]```
Scanning ...


```

[B]hcitool dev  
[/B]```
Devices:
    hci0    30:10:B3:03:36:66


```
(note the output address suggests the internal device is manufactured by Liteon Technology Corp.)

[B]hciconfig -a
[/B]```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 30:10:B3:03:36:66  ACL MTU: 1022:8  SCO MTU: 183:5
    UP RUNNING PSCAN 
    RX bytes:612 acl:0 sco:0 events:37 errors:0
    TX bytes:942 acl:0 sco:0 commands:37 errors:0
    Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'ubuntu-0'
    Class: 0x00010c
    Service Classes: Unspecified
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x3101
    LMP Version: 4.0 (0x6)  Subversion: 0x1
    Manufacturer: Atheros Communications, Inc. (69)


```

[B]rfkill list
[/B]```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

**lsmod | grep blue**
```
bluetooth             446190  24 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
toshiba_bluetooth      12867  0 


```

[B]lsusb
[/B]```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0930:0227 Toshiba Corp. 
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 002: ID 13d3:5652 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

[B]lsusb -s 001:004 -v
[/B]
```
Bus 001 Device 004: ID 0930:0227 Toshiba Corp. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0930 Toshiba Corp.
  idProduct          0x0227 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          185
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass        224 Wireless
      bFunctionSubClass       1 Radio Frequency
      bFunctionProtocol       1 Bluetooth
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1


```[B]dmesg | grep bluetooth
[/B]```
[   13.499247] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   13.499624] toshiba_bluetooth: Re-enabling Toshiba Bluetooth


```

[B]bluetoothctl
[/B]```
[NEW] Controller 30:10:B3:03:36:66 ubuntu-0 [default]


```

[bluetooth]# **scan on**
```

Discovery started
[CHG] Controller 30:10:B3:03:36:66 Discovering: yes

```

[bluetooth]# **show**
```

Controller 30:10:B3:03:36:66
    Name: taylor-dev
    Alias: ubuntu-0
    Class: 0x00010c
    Powered: yes
    Discoverable: no
    Pairable: yes
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0517
    Discovering: yes

```

and for good measure, a screenshot of gnome-bluetooth

[ATTACH=CONFIG]259193[/ATTACH]

No idea whats going wrong, because all signs say that it should be working. I know that all my bluetooth devices (phones, mice, etc) all work and are discoverable, and can detect each other.

---

### Post by jeremy31 on 2015-01-12
Post the results of ```
lspci -nnk | grep -iA2 net
``` and the model of the wifi card- Toshiba usually puts a sticker on the bottom

---

### Post by taylor15 on 2015-01-12
results of **lspci** [B]-nnk | grep -iA2 net

[/B]```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:f91b]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0832]
    Kernel driver in use: ath9k


```

And as far as i can tell, the model of the wifi card is **QCNFA335**

---

### Post by jeremy31 on 2015-01-12
You should file a bug report here [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug) 
That bluetooth chip isn't supported correctly in linux yet.  I have patched modules to attempt to get some of them to work but fail because the correct firmware is not available

---

### Post by taylor15 on 2015-01-12
Thanks for your help jeremy31. I guess there's no guarantee that they will support it in future if its been out for around a year now. I'll submit the bug later today and post a link for anyone who may have a similar issue.

One other question, where can I find an official list of supported bluetooth/wireless chips?

---

### Post by jeremy31 on 2015-01-12
The best bet might be Intel 7260 wifi bluetooth combo chips unless they need different firmware with the form factor you have

---

### Post by Ephialta on 2015-01-14
Hi, I found your thread by searching my bluetooth adapter's HWID (**0930:0227**). I have a **Toshiba C55-B5276** that I recently bought. After a week of researching this problem I narrowed it down to a lack of driver support.

Put simply, the **QCNFA335** isn't supported in kernels under **3.18.2**. I examined the driver source of Kernel **3.18.2** and **3.17.8**. The HWID simply isn't there to be recognized.

But the most frustrating part is that the support in **3.18.2** and above is incomplete. The driver recognizes the device but there's no firmware file to accompany it. If you upgrade to **3.18.2** or above dmesg will output something about not being able to load **AthrBT_0x31010100.dfu** and **ramps_0x31010100_40.dfu**. 

Somebody forgot to actually include the firmware. ](*,) I'm not a kernel programmer, and I'm not entirely sure what the proper channels to resolve this would be. I solved it by retrieving Windows drivers from one of Microsoft's Windows update servers, extracting the .cab file and placing the missing firmware into **/usr/lib/firmware/ar3k/.**

After a cold boot several days of frustration came to an end. Bluetooth can discover and be discovered by other devices. Three cold boots in and it's still working.

So a solution to this problem would be to **upgrade to at least the 3.18.2 kernel and implement the aforementioned workarounds.** This should be simple enough in Ubuntu.

Cheers from Arch Linux.

---

### Post by jeremy31 on 2015-01-14
What does the license with the windows drivers say?  It would be great if it could be included in linux-firmware

---

### Post by taylor15 on 2015-01-14
Are you able to link the particular download from toshiba you used Ephialta?

---

### Post by Ephialta on 2015-01-14
Yes, I should have mentioned that. I found the driver by doing a Google search on the firmware files, leading me to this:

[http://download.windowsupdate.com/d/msdownload/update/driver/drvs/2014/01/20623393_919a4673931aa789f0b1c3eeafb360b36097894a.cab](http://download.windowsupdate.com/d/msdownload/update/driver/drvs/2014/01/20623393_919a4673931aa789f0b1c3eeafb360b36097894a.cab)

These are actually Qualcomm's drivers packaged as Windows update files. There doesn't appear to be any licensing information included in the archive. So I can't say what their stance on this would be.

---

### Post by johnthesoftware on 2015-02-02
Blimey.

A grateful Fedora user salutes you.

As Ephialta says, copy the latest ramps and AthrBT files to /usr/lib/firmware/ar3k and Bob's your uncle.

Ta

John

---

### Post by Pilot6 on 2015-02-02
> **taylor15 said:**
> Thanks for your help jeremy31. I guess there's no guarantee that they will support it in future if its been out for around a year now. I'll submit the bug later today and post a link for anyone who may have a similar issue.

One other question, where can I find an official list of supported bluetooth/wireless chips?
Firmware is available in Windows drivers. If the bugreport is filed, I will look at it.

---

### Post by Pilot6 on 2015-02-02
But I do not see this PID in any Windows drivers.

---

### Post by Pilot6 on 2015-02-02
I found it. It is a AR3012 chip with 0930:0227. It is already supported in 3.16 kernel.
The problem must be somewhere else.

---

### Post by jeremy31 on 2015-02-02
> **Pilot6 said:**
> I found it. It is a AR3012 chip with 0930:0227. It is already supported in 3.16 kernel.
The problem must be somewhere else.

It is likely the firmware issue with the new cards.  I found a case that had the same chipset reported that I have but was looking for firmware that wasn't part of linux-firmware.  And I can't find the post anymore but it was one of the QCNFA cards
There was a error in dmesg ```
*Bluetooth: Configuration file not **found ar3k/ ramps_0x00000200_0.dfu*&#8203;
``` and that file is not part of my windows firmware

---

### Post by fburolo on 2015-05-04
Ephialta, thank you very much! My Toshiba laptop is finally fully functional now. :-)

However, now I have noticed WiFi connection weakening, and occasionally breaking, while a device is connected via Bluetooth...

---

