---
title: "Realtek RTL8822BE bluetooth not working .. tried just about everything"
date: 2018-08-29
forum: Networking &amp; Wireless
---

### Post by arcooke on 2018-08-29
I am at a loss here. I'm on 18.04.1, with a bleeding edge 4.18.5 kernel.  The rtl8822be in my AMD ThinkPad E585 is a wifi+bt combo chip; wifi works bt does not.  I've tried everything I can find.  This chip has been supported several months now. It's in the kernel, I have the firmware.

Any ideas?

thanks


I've been through all 5 pages of this thread as well as others:

[https://ubuntuforums.org/showthread.php?t=2364383&page=2](https://ubuntuforums.org/showthread.php?t=2364383&page=2)

Device ID is 0bda:b023

[https://certification.ubuntu.com/catalog/component/usb/286/0bda%3Ab023/](https://certification.ubuntu.com/catalog/component/usb/286/0bda%3Ab023/)


```
hcitool scan
Device is not available: No such device

```

```
sudo dmesg | grep firm
[    1.992840] [drm] Found VCN firmware Version: 1.73 Family ID: 18
[    3.571724] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[    3.858047] psmouse serio2: trackpoint: Elan TrackPoint firmware: 0x10, buttons: 3/
```


```
lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15d0
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 15d1
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:01.6 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15db
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15dc
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e8
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e9
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ea
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15eb
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ec
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ed
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ee
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ef
01:00.0 Non-Volatile memory controller: Lenovo Device 0003
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c4)
05:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
05:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df
05:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e0
05:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e1
05:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Device 15e3
06:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61)

```


```
sudo lspci -k -s 04:00.0
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
        Subsystem: Lenovo Device b024
        Kernel driver in use: r8822be
        Kernel modules: r8822be
```


```
bluetoothctl
Agent registered
[bluetooth]# power on
No default controller available
[bluetooth]# exit
Agent unregistered

```

```
lsmod | grep btusb
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                20480  1 btusb
bluetooth             548864  11 btrtl,btintel,btbcm,bnep,btusb

```

```
/lib/firmware/rtl_bt$ ls -l
total 520
-rw-r--r-- 1 root root 38764 Mar 29  2017 rtl8192ee_fw.bin
-rw-r--r-- 1 root root 37904 Mar 29  2017 rtl8192eu_fw.bin
-rw-r--r-- 1 root root 24548 Mar 29  2017 rtl8723a_fw.bin
-rw-r--r-- 1 root root 45048 Mar 29  2017 rtl8723b_fw.bin
-rw-r--r-- 1 root root    10 May 18 13:09 rtl8723d_config.bin
-rw-r--r-- 1 root root 47028 May 18 13:09 rtl8723d_fw.bin
-rw-r--r-- 1 root root 74488 Mar 29  2017 rtl8761a_fw.bin
-rw-r--r-- 1 root root 40520 Mar 29  2017 rtl8812ae_fw.bin
-rw-r--r-- 1 root root 37420 Mar 29  2017 rtl8821a_fw.bin
-rw-r--r-- 1 root root    10 May 18 13:09 rtl8821c_config.bin
-rw-r--r-- 1 root root 37356 May 18 13:09 rtl8821c_fw.bin
-rw-r--r-- 1 root root    14 Aug 29 19:49 rtl8822b_config.bin
-rw-r--r-- 1 root root    14 Apr 24 09:28 rtl8822b_config.bin.bak
-rw-r--r-- 1 root root 51176 Aug 29 19:49 rtl8822b_fw.bin
-rw-r--r-- 1 root root 51176 Apr 24 09:28 rtl8822b_fw.bin.bak

```

```
/lib/firmware/rtlwifi$ ls -l
total 1076
-rw-r--r-- 1 root root  11216 Mar 29  2017 rtl8188efw.bin
-rw-r--r-- 1 root root  13904 Mar 29  2017 rtl8188eufw.bin
-rw-r--r-- 1 root root  16192 Nov 17  2017 rtl8192cfw.bin
-rw-r--r-- 1 root root  16332 Nov 17  2017 rtl8192cfwU_B.bin
-rw-r--r-- 1 root root  14818 Mar 29  2017 rtl8192cfwU.bin
-rw-r--r-- 1 root root  16116 Mar 29  2017 rtl8192cufw_A.bin
-rw-r--r-- 1 root root  16096 Mar 29  2017 rtl8192cufw_B.bin
-rw-r--r-- 1 root root  16014 Mar 29  2017 rtl8192cufw.bin
-rw-r--r-- 1 root root  16116 Mar 29  2017 rtl8192cufw_TMSC.bin
-rw-r--r-- 1 root root  31376 Nov 17  2017 rtl8192defw.bin
-rw-r--r-- 1 root root  31818 Nov 17  2017 rtl8192eefw.bin
-rw-r--r-- 1 root root  25264 Nov 17  2017 rtl8192eu_ap_wowlan.bin
-rw-r--r-- 1 root root  31818 Nov 17  2017 rtl8192eu_nic.bin
-rw-r--r-- 1 root root  25878 Nov 17  2017 rtl8192eu_wowlan.bin
-rw-r--r-- 1 root root  80208 Mar 29  2017 rtl8192sefw.bin
-rw-r--r-- 1 root root 122328 Mar 29  2017 rtl8712u.bin
-rw-r--r-- 1 root root  22172 Mar 29  2017 rtl8723aufw_A.bin
-rw-r--r-- 1 root root  24118 Mar 29  2017 rtl8723aufw_B.bin
-rw-r--r-- 1 root root  19200 Mar 29  2017 rtl8723aufw_B_NoBT.bin
-rw-r--r-- 1 root root  31762 Nov 17  2017 rtl8723befw_36.bin
-rw-r--r-- 1 root root  30746 Nov 17  2017 rtl8723befw.bin
-rw-r--r-- 1 root root  20886 May 18 13:09 rtl8723bs_ap_wowlan.bin
-rw-r--r-- 1 root root   9120 May 18 13:09 rtl8723bs_bt.bin
-rw-r--r-- 1 root root  32108 May 18 13:09 rtl8723bs_nic.bin
-rw-r--r-- 1 root root  26398 May 18 13:09 rtl8723bs_wowlan.bin
-rw-r--r-- 1 root root  20886 Nov 17  2017 rtl8723bu_ap_wowlan.bin
-rw-r--r-- 1 root root  32108 Nov 17  2017 rtl8723bu_nic.bin
-rw-r--r-- 1 root root  26398 Nov 17  2017 rtl8723bu_wowlan.bin
-rw-r--r-- 1 root root  27726 May 18 13:09 rtl8723defw.bin
-rw-r--r-- 1 root root  22996 Mar 29  2017 rtl8723fw_B.bin
-rw-r--r-- 1 root root  11662 Mar 29  2017 rtl8723fw.bin
-rw-r--r-- 1 root root  28348 Nov 17  2017 rtl8821aefw_29.bin
-rw-r--r-- 1 root root  28984 Mar 29  2017 rtl8821aefw.bin
-rw-r--r-- 1 root root  19858 Mar 29  2017 rtl8821aefw_wowlan.bin
-rw-r--r-- 1 root root 127496 Apr 24 09:34 rtl8822befw.bin

```

---

### Post by praseodym on 2018-08-30
[https://ubuntuforums.org/showthread.php?t=2383787&p=13739449#post13739449](https://ubuntuforums.org/showthread.php?t=2383787&p=13739449#post13739449)

Check this one

---

### Post by jeremy31 on 2018-08-30
Can you post results for ```
lsusb
```

---

### Post by arcooke on 2018-08-31
Ah-ha... OK, so I've been through that, except I used the rtlwiwi-next repository [https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next)

Reason being, the rtl8822be isn't shown in the source code in lwfinger's rtlwifi_new repo.  However, I just now saw a note in that repo about this in the readme:

> If you are looking for the driver for rtl8822be or rtl8723de, then execute the following command:

git checkout origin/extended -b extended

[https://github.com/lwfinger/rtlwifi_new/search?q=rtl8822be&unscoped_q=rtl8822be](https://github.com/lwfinger/rtlwifi_new/search?q=rtl8822be&unscoped_q=rtl8822be)

So that might help.  I will give it a shot, as well as the bluetooth 4.4 driver mentioned in that post.  Thanks. 

I will have to try it later this evening, I'm using the laptop in windows for work at the moment.



> **jeremy31 said:**
> Can you post results for ```
lsusb
```


I will do that this evening as well if the previous suggestion doesn't help.

---

### Post by arcooke on 2018-09-01
Well.. I Installed the wifi from that link.  I was unable to install bluetooth-4.4 from source because mismatched kernel version (expects 4.15, I have 4.18.5)

I was able to install the patch on post #6 of that forum thread though.  I was very hopeful that would work but bluetooth still not showing up.


lsusb -v output (this is an m.2 wifi+bt card though, not USB):

```

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            4.18
  iManufacturer           3 Linux 4.18.5-041805-generic xhci-hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:05:00.4
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0
Hub Descriptor:
  bLength               0
  bDescriptorType       0
  nNbrPorts             0
  wHubCharacteristic 0x0000
    Ganged power switching
    Ganged overcurrent protection
  bPwrOn2PwrGood        0 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  bHubDecLat          0.0 micro seconds
  wHubDelay             0 nano seconds
  DeviceRemovable    0xaa
 Hub Port Status:
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           35
  bNumDeviceCaps          2
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x02
      Latency Tolerance Messages (LTM) Supported
    wSpeedsSupported   0x0008
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   3
      Lowest fully-functional device speed is SuperSpeed (5Gbps)
    bU1DevExitLat           0 micro seconds
    bU2DevExitLat           0 micro seconds
  ** UNRECOGNIZED:  14 10 0a 00 01 00 00 00 01 00 00 00 34 00 05 00 b4 00 05 00
Device Status:     0x0001
  Self Powered

Bus 003 Device 003: ID 04f2:b604 Chicony Electronics Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.01
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x04f2 Chicony Electronics Co., Ltd
  idProduct          0xb604 
  bcdDevice            0.27
  iManufacturer           3 Chicony Electronics Co.,Ltd.
  iProduct                1 Integrated Camera
  iSerial                 2 0001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          955
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 USB Camera
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               5 Integrated Camera
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              5 Integrated Camera
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength          107
        dwClockFrequency       15.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x0000000e
          Auto-Exposure Mode
          Auto-Exposure Priority
          Exposure Time (Absolute)
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000157f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x 9
          None
          SECAM - 625/50
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               6
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                27
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 4
        guidExtensionCode         {8ca72912-b447-9440-b0ce-db07386fb938}
        bNumControl             2
        bNrPins                 1
        baSourceID( 0)          2
        bControlSize            2
        bmControls( 0)       0x00
        bmControls( 1)       0x06
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                29
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 6
        guidExtensionCode         {5a10b826-1307-7048-979d-da79444bb68e}
        bNumControl             8
        bNrPins                 1
        baSourceID( 0)          4
        bControlSize            4
        bmControls( 0)       0x3c
        bmControls( 1)       0x18
        bmControls( 2)       0x0c
        bmControls( 3)       0x00
        iExtension              6 Realtek Extended Controls Unit
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               6
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            15
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         2
        wTotalLength                      689
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       3
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    11
        bmaControls( 1)                    11
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        1
        bNumFrameDescriptors                9
        bFlags                              1
          Fixed-size samples: Yes
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                442368000
        dwMaxBitRate                442368000
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           180
        dwMinBitRate                 27648000
        dwMaxBitRate                 27648000
        dwMaxVideoFrameBufferSize      115200
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 36864000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                 48660480
        dwMaxBitRate                 48660480
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            424
        wHeight                           240
        dwMinBitRate                 48844800
        dwMaxBitRate                 48844800
        dwMaxVideoFrameBufferSize      203520
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           360
        dwMinBitRate                110592000
        dwMaxBitRate                110592000
        dwMaxVideoFrameBufferSize      460800
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                147456000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         8
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            848
        wHeight                           480
        dwMinBitRate                195379200
        dwMaxBitRate                195379200
        dwMaxVideoFrameBufferSize      814080
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         9
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            960
        wHeight                           540
        dwMinBitRate                248832000
        dwMaxBitRate                248832000
        dwMaxVideoFrameBufferSize     1036800
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               9
        wWidth( 0)                       1280
        wHeight( 0)                       720
        wWidth( 1)                        320
        wHeight( 1)                       180
        wWidth( 2)                        320
        wHeight( 2)                       240
        wWidth( 3)                        352
        wHeight( 3)                       288
        wWidth( 4)                        424
        wHeight( 4)                       240
        wWidth( 5)                        640
        wHeight( 5)                       360
        wWidth( 6)                        640
        wHeight( 6)                       480
        wWidth( 7)                        848
        wHeight( 7)                       480
        wWidth( 8)                        960
        wHeight( 8)                       540
        bNumCompressionPatterns             9
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        2
        bNumFrameDescriptors                9
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                147456000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval        1000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           180
        dwMinBitRate                 27648000
        dwMaxBitRate                 27648000
        dwMaxVideoFrameBufferSize      115200
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 36864000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                 48660480
        dwMaxBitRate                 48660480
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            424
        wHeight                           240
        dwMinBitRate                 48844800
        dwMaxBitRate                 48844800
        dwMaxVideoFrameBufferSize      203520
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           360
        dwMinBitRate                110592000
        dwMaxBitRate                110592000
        dwMaxVideoFrameBufferSize      460800
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                147456000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  1
        dwFrameInterval( 0)            333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         8
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            848
        wHeight                           480
        dwMinBitRate                130252800
        dwMaxBitRate                130252800
        dwMaxVideoFrameBufferSize      814080
        dwDefaultFrameInterval         500000
        bFrameIntervalType                  1
        dwFrameInterval( 0)            500000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         9
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            960
        wHeight                           540
        dwMinBitRate                124416000
        dwMaxBitRate                124416000
        dwMaxVideoFrameBufferSize     1036800
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            666666
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               9
        wWidth( 0)                       1280
        wHeight( 0)                       720
        wWidth( 1)                        320
        wHeight( 1)                       180
        wWidth( 2)                        320
        wHeight( 2)                       240
        wWidth( 3)                        352
        wHeight( 3)                       288
        wWidth( 4)                        424
        wHeight( 4)                       240
        wWidth( 5)                        640
        wHeight( 5)                       360
        wWidth( 6)                        640
        wHeight( 6)                       480
        wWidth( 7)                        848
        wHeight( 7)                       480
        wWidth( 8)                        960
        wHeight( 8)                       540
        bNumCompressionPatterns             9
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0b00  2x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13fc  3x 1020 bytes
        bInterval               1
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           53
  bNumDeviceCaps          2
Device Status:     0x0000
  (Bus Powered)

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            4.18
  iManufacturer           3 Linux 4.18.5-041805-generic xhci-hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:05:00.4
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x06
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0503 highspeed power enable connect
Device Status:     0x0001
  Self Powered

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            4.18
  iManufacturer           3 Linux 4.18.5-041805-generic xhci-hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:05:00.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0
Hub Descriptor:
  bLength               1
  bDescriptorType       0
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  bHubDecLat          0.6 micro seconds
  wHubDelay          4086 nano seconds
  DeviceRemovable    0xff
 Hub Port Status:
   Port 1: 0000.02a0 lowspeed
   Port 2: 0000.02a0 lowspeed
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           91
  bNumDeviceCaps          2
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            4.18
  iManufacturer           3 Linux 4.18.5-041805-generic xhci-hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:05:00.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0001
  Self Powered
```

---

### Post by jeremy31 on 2018-09-01
Most bluetooth devices are on the USB bus even if they are part of a PCI wifi, the kernel source code supports 2 different bluetooth chips on the rtl8823be
```
	/* Additional Realtek 8822BE Bluetooth devices */
	{ USB_DEVICE(0x13d3, 0x3526), .driver_info = BTUSB_REALTEK },
	{ USB_DEVICE(0x0b05, 0x185c), .driver_info = BTUSB_REALTEK },

```

I don't think I noticed either of them in your results

---

### Post by arcooke on 2018-09-01
Oh OK.  I didn't know that, I don't work with bluetooth much.  Any thoughts what to try next?  

I managed to get bluetooth working during one session, one time.  And then it disappeared again after next reboot.  No clue what I did to get it to work that one time


Thanks

---

### Post by defcon2 on 2018-09-16
It works for me on the ThinkPad A485 after enabling the bluetooth module with the Function Key Fn+F10. Really embarassing I missed that in the first place.

---

### Post by jontis on 2018-09-17
Hijacking / contributing... I'm in the same or similar boat. I have a HP Omen Desktop with mobo mounted wifi BT combo card (I'm pretty sure it has BT).
The wifi works great.
Bluetooth: no trace of any device.
If I understand you correctly, it should show up in lsusb as a bluetooth device, but it doesn't.
Can it be that the USB ID is not yet in drivers associated with a bluetooth device? Or is some old ID misidentifying the device?

$ lspci
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter

$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0bc2:231a Seagate RSS LLC 
Bus 002 Device 003: ID 2109:0813 VIA Labs, Inc. 
Bus 002 Device 002: ID 2109:0813 VIA Labs, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 001 Device 005: ID 2109:2813 VIA Labs, Inc. 
Bus 001 Device 003: ID 2109:2813 VIA Labs, Inc. 
Bus 001 Device 012: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 007: ID 0416:e00c Winbond Electronics Corp. 
Bus 001 Device 006: ID 0bda:0153 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Poking around following other forums, firmware files are there:
/lib/firmware/rtl_bt/rtl8822b_config.bin
/lib/firmware/rtl_bt/rtl8822b_fw.bin

Which I believe means that it should have support in my kernel 4.15.0-34-generic

Please correct me when I misunderstood something.

[    9.603435] r8822be: module is from the staging directory, the quality is unknown, you have been warned.
[    9.603782] r8822be: module verification failed: signature and/or required key missing - tainting kernel
[    9.605573] r8822be 0000:04:00.0: enabling device (0100 -> 0103)
[    9.635874] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[    9.638877] r8822be: rtlwifi: wireless switch is on

Booted up a Fedora live usb to check if bluetooth was there. It was.
ls usb did not differ from Mint.

Kernel 4.16

dmesg contained:
[   11.472990] Bluetooth: hci0: rtl: examining hci_ver=07 hci_rev=000b lmp_ver=07 lmp_subver=8822
[   11.472992] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_config.bin
[   11.487522] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_fw.bin
[   11.494980] Bluetooth: hci0: rom_version status=0 version=2
[   11.494989] Bluetooth: hci0: cfg_sz 14, total size 20270

Booting back into Mint.
Now bluetooth is here too. Without me changing anything.
I did move one usb device but that's it...?

After a while of flawless bluetooth functionality, it just stopped working.

Rebooting again and the it says device is not there.

I'm not sure what to look for now. Ideas are welcome.

---

### Post by jeremy31 on 2018-09-21
jontis, I can't help any if the device doesn't appear in lsusb results.  This part of the forum is for official Ubuntu flavors, not Mint, EOS, and the others

---

### Post by Thalandor on 2018-11-06
What happens when you resume from sleep? I have another wifi/bt chip and it is only visible in **lsusb** after resuming from sleep.

---

### Post by shengyangwei on 2018-11-20
I was suffering the same Bluetooth issue with you, and my motherboard is ROG Maximus X which has the rtl8822be.

If you do not mind reinstalling your system, I would recommend you to check the

"Install third-party software for graphics and Wi-Fi hardware and additional media formats" 

option during the installation.

Although I have not figured out what is installed in this option, at least it is the only working method for me.

---

### Post by quo2 on 2018-12-26
On the Ubuntu (Offical) 18.10 live disk its in GNOME Settings.

---

### Post by him610 on 2018-12-28
My (active) bluetooth controller does not show up in the listing of devices when using *lsusb*; however, the driver shows up using 
```

hugh@G4560:~$ dmesg | grep bt
[    3.635566] usbcore: registered new interface driver btusb
hugh@G4560:~$ 

```

and shows up here too,
```
hugh@G4560:~$ sudo lshw | grep btusb
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s

```

I have no idea why it does not show up using *lsusb*. Perhaps some cognizant individual will provide some enlightenment.

---

### Post by praseodym on 2018-12-28
Check if its an integrated one WLAN/BT combo:
```

lspci -nnk
```

---

### Post by him610 on 2018-12-28
Here is another way the Bluetooth adapter can be displayed, 
```

hugh@G4560:~$ sudo lshw -c communication
  *-usb:2                   
       description: Bluetooth wireless interface
       vendor: Intel Corp.
       physical id: d
       bus info: usb@1:d
       version: 0.01
       capabilities: bluetooth usb-2.00
       configuration: driver=btusb maxpower=100mA speed=12Mbit/s
  *-communication
       description: Communication controller
       product: 200 Series PCH CSME HECI #1
       vendor: Intel Corporation
       physical id: 16
       bus info: pci@0000:00:16.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=mei_me latency=0
       resources: irq:129 memory:df34d000-df34dfff

```

By the way, my Intel Wireless 3160 is soldered to the MB and appears to have both PCI and USB interfaces.

---

### Post by jeremy31 on 2018-12-28
Are you sure it is not listed in lsusb results as a lot of times the description is not going to say bluetooth

---

### Post by him610 on 2018-12-28
Color me purple! It does indeed show up *ID 8087:07dc Intel Corp.*
```

hugh@G4560:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 2001:f103 D-Link Corp. DUB-H7 7-port USB 2.0 hub
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 007: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 006: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 001 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by praseodym on 2018-12-28
```
modprobe -c | grep -i "8087.*07dc"
```
Does it give an output? Here, it doesn't.

---

### Post by jeremy31 on 2018-12-28
It doesn't but that exact device is listed in btusb source code
```
	/* Intel Bluetooth devices */
	{ USB_DEVICE(0x8087, 0x0025), .driver_info = BTUSB_INTEL_NEW },
	{ USB_DEVICE(0x8087, 0x0026), .driver_info = BTUSB_INTEL_NEW },
	{ USB_DEVICE(0x8087, 0x0029), .driver_info = BTUSB_INTEL_NEW },
	{ USB_DEVICE(0x8087, 0x07da), .driver_info = BTUSB_CSR },
	{ USB_DEVICE(0x8087, 0x07dc), .driver_info = BTUSB_INTEL },
	{ USB_DEVICE(0x8087, 0x0a2a), .driver_info = BTUSB_INTEL },
	{ USB_DEVICE(0x8087, 0x0a2b), .driver_info = BTUSB_INTEL_NEW },
	{ USB_DEVICE(0x8087, 0x0aa7), .driver_info = BTUSB_INTEL },
	{ USB_DEVICE(0x8087, 0x0aaa), .driver_info = BTUSB_INTEL_NEW },
```

---

### Post by Lars Gottlieb on 2019-01-28
Hullo Ubuntu people.

I appear to have similar troubles with my [COLOR=#333333][FONT=&quot]RTL8822BE under Manjaro Linux, latest kernel, everything fully updated. 

[/FONT][/COLOR]The BT device occasionally simply stops working, and there is Very little I can do to get it back up. First time it happened, after a lot of frustration, I reset and updated the BIOS, then when that did nothing, reinstalled the OS completely. No joy, the OS simply doesn't see a BT device. 

By accident, I did find something that actually works though: 
Turn off the computer. Pull the plug, leave it out for at least 30 seconds. Put it back in again, turn it on, and hey presto, there's a BT device, and it works fine. For a while ..

---

