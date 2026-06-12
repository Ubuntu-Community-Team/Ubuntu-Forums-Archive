---
title: "Unable to use USB WiFi adapter"
date: 2017-04-18
forum: Networking &amp; Wireless
---

### Post by benjikcf001 on 2017-04-18
Hello everyone, I am new to ubuntu. I have bought a TP Link t4uhp driver and downloaded the zip file. 
[http://www.tp-link.com/en/download/Archer-T4UHP.html#Driver](http://www.tp-link.com/en/download/Archer-T4UHP.html#Driver)

I am not sure how to install the zip file and I have tried to search the usb wifi adapter in the additional driver, but nothing is there.
Unfortunately, TP Link doesn't provide instruction for how to install driver on Linux. 
Can anyone share the solution?? THank you

---

### Post by howefield on 2017-04-18
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by benjikcf001 on 2017-04-18
Thank you for the moving.

---

### Post by kc1di on 2017-04-18
Hello benjikcf001 and Welcome to Ubuntu and Linux,

TP-link says they include instructions with the download [see here]("http://www.tp-link.com/ca/faq-1076.html")
with that said you'll need to extract the driver from the zip file first in order to see the instructions.
if you right click on the zip file it should offer to extract here or open with depending upon which desktop your using you want to open the zip file with the archive manager.
once you've extracted the files one should be a read me file or installation text file that should provide instructions. 

I've never personally installed a tplink dongle so can't be of much help there as to the process.  but best of luck getting it going.

---

### Post by benjikcf001 on 2017-04-18
Hi kc1di, thank you for the reply. They said they have the instruction but I couldn't find the instruction inside the zip file. I think they didn't do it for this one.

---

### Post by benjikcf001 on 2017-04-18
here is further information:
computer~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 2357:010f  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04e8:61b6 Samsung Electronics Co., Ltd M3 Portable Hard Drive 1TB
Bus 001 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
computer~$ uname -r
4.8.0-36-generic

---

### Post by chili555 on 2017-04-18
Wow. Just wow.

Could you please double-triple check this:> computer~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID [COLOR="#FF0000"]2357:010f [/COLOR]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04e8:61b6 Samsung Electronics Co., Ltd M3 Portable Hard Drive 1TB
Bus 001 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubIf, indeed, you have an 010f, then neither the driver you downloaded nor any driver I or Google is aware of covers it. We might do some driver hacking to see if we can trick the driver into action.

The usual process is to right-click the zip file and select 'extract here'. The resultant folder is called 8812au. Now, in a terminal:```
cd ~/Downloads/8812au
make
```Does it make with warnings or errors? Or both??

If it makes all the way to the creation of the driver, usually rtl8812au.ko, then do:```
sudo make install
```Check to see if your device is covered:```
modinfo rtl8812au.ko | grep 010F
```No? I didn't think so.

I will await your results before we proceed.

---

### Post by jeremy31 on 2017-04-18
The code from TP Link includes
```
{USB_DEVICE(0x2357, 0x010F),.driver_info = RTL8812}, /* TP-Link - Cameo */
```
If it compiles is another question as most of the source code is 2 years old

---

### Post by cyraxs on 2018-02-11
I did all the things from the other forum, and finally was able to compile after rectifying rtl_cmd.c with **the patch**&#8203;. This is my result from running *sudo make*:

```

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-32-generic/build M=/home/sr71/Documents/rtl8812au  modulesmake[1]: Entering directory '/usr/src/linux-headers-4.13.0-32-generic'
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_cmd.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_security.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_debug.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_io.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_ioctl_query.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_ioctl_set.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_ieee80211.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_mlme.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_mlme_ext.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_wlan_util.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_vht.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_pwrctrl.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_rf.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_recv.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_sta_mgt.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_ap.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_xmit.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_p2p.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_tdls.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_br_ext.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_iol.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_sreset.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/efuse/rtw_efuse.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/osdep_service.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/os_intfs.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/usb_intf.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/ioctl_linux.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/xmit_linux.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/mlme_linux.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/recv_linux.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/sr71/Documents/rtl8812au/os_dep/linux/rtw_android.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/hal_intf.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/hal_com.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/hal_com_phycfg.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/hal_phy.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/led/hal_usb_led.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/HalPwrSeqCmd.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/Hal8812PwrSeq.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/Hal8821APwrSeq.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_xmit.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_sreset.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_hal_init.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_phycfg.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_rf6052.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_dm.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_rxdesc.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_cmd.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/usb/usb_halinit.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/usb/rtl8812au_led.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/usb/rtl8812au_xmit.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/usb/rtl8812au_recv.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/usb/usb_ops_linux.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_mp.o
/home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_mp.c: In function &#8216;Hal_SetAntenna&#8217;:
/home/sr71/Documents/rtl8812au/hal/rtl8812a/rtl8812a_mp.c:640:7: warning: statement will never be executed [-Wswitch-unreachable]
   u32 reg0xC50 = 0;
       ^~~~~~~~
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/odm_debug.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/odm_interface.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/odm_HWConfig.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/odm.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/HalPhyRf.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_FW.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_MAC.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_BB.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_RF.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8812a/odm_RegConfig8812A.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_MAC.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_BB.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_RF.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.o
  CC [M]  /home/sr71/Documents/rtl8812au/hal/OUTSRC/rtl8821a/odm_RegConfig8821A.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_mp.o
  CC [M]  /home/sr71/Documents/rtl8812au/core/rtw_mp_ioctl.o
  LD [M]  /home/sr71/Documents/rtl8812au/8812au.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sr71/Documents/rtl8812au/8812au.mod.o
  LD [M]  /home/sr71/Documents/rtl8812au/8812au.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-32-generic'



```

... and this is what I got from running *sudo make install*:
```

install -p -m 644 8812au.ko  /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.13.0-32-generic

```

However, I still cannot see my usb adapter. What gives? (FYI linux-header4.15rc+ will not work; I had to use ukuu to "update" to 4.13 again.)

Excerpt from *sudo lsusb -v*:
```
Bus 002 Device 002: ID 0bda:b812 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0xb812 
  bcdDevice            2.10
  iManufacturer           1 Realtek
  iProduct                2 USB3.0 802.11ac 1200M Adapter
  iSerial                 3 123456
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 USB3.0 802.11ac 1200M Adapter
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
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
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               3
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x0006
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat          10 micro seconds
    bU2DevExitLat        1023 micro seconds
Device Status:     0x0000
  (Bus Powered)


```

---

### Post by chili555 on 2018-02-11
What does this tell us?```
modinfo 8812au | grep B812
```Nothing, I suspect.

---

### Post by dsmalinsky on 2018-07-28
Hi, I also have the same TP-LINK usb adapter, which in the box is advertised as Archer T4UHP.
Running just released Ubuntu 18.04.1 with kernel 4.15.0-29 on my pc
Cannot make the USB Adapter to work after trying several alternatives 

The output from lsusb is slightly different from the one mentioned in this thread by benjikcf001

```
diego@kush:~$ lsusb
Bus 002 Device 004: ID 1a2c:0042 China Resource Semico Co., Ltd 
Bus 002 Device 005: ID 2357:0122  
Bus 002 Device 003: ID 258a:0001  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5149:13d3  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Tried downloading the driver from [https://static.tp-link.com/Archer%20T4UHP(UN)_V1_161213_Linux.zip](https://static.tp-link.com/Archer%20T4UHP(UN)_V1_161213_Linux.zip) (which says Operating System: Linux (kernel 2.6.18 ~ 3.19.3) so it's pretty old) but 'make' is returning an error:

```
"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
----- extra_cflags=-DCONFIG_IOCTL_CFG80211=1 -DRTW_USE_CFG80211_STA_EVENT=1  -O1 -Wno-unused-variable -Wno-unused-value -Wno-unused-label -Wno-unused-parameter -Wno-unused-function -Wno-unused -I/include -I/platform -DCONFIG_RTL8812A -DCONFIG_MP_INCLUDED -DCONFIG_POWER_SAVING -DCONFIG_TRAFFIC_PROTECT -DCONFIG_LOAD_PHY_PARA_FROM_FILE -DREALTEK_CONFIG_PATH="" -DCONFIG_RTW_ADAPTIVITY_EN=0 -DCONFIG_RTW_ADAPTIVITY_MODE=0 -DCONFIG_BR_EXT '-DCONFIG_BR_EXT_BRNAME=br0' -DCONFIG_LITTLE_ENDIAN
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-29-generic/build M=/home/diego/Downloads/Archer T4UHP(UN)_V1_161213_Linux/8812au  modules
/bin/sh: 1: Syntax error: "(" unexpected
Makefile:1635: recipe for target 'modules' failed
make: *** [modules] Error 2

```

So here am I a bit frustrated and asking for help.
Can anyone help me?

Thanks in advance,

---

### Post by praseodym on 2018-07-28
Install the package

rtl8812au-dkms

---

### Post by dsmalinsky on 2018-07-29
Already installed the package and rebooted, not seing any differences.
Is there a way to diagnose is that this driver (rtl8812au-dkms) is being used?

---

### Post by praseodym on 2018-07-29
Check
```

lsmod
dmesg | grep key
```

---

### Post by jeremy31 on 2018-07-29
I would do a ```
sudo apt-get purge rtl8812au-dkms
sudo apt install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU-8821AU_linux
sudo make -f Makefile.dkms install
```
Check Secure Boot status with
```
mokutil --sb-state
```
Reboot and disable Secure Boot if above command reported Secure Boot in use

---

### Post by dsmalinsky on 2018-07-29
jeremy31 answer did the trick! 
I don't have Secure Boot enabled so after installing driver from [COLOR=#000000][FONT=&quot]https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git [/FONT][/COLOR]and rebooting my TPLINK Archer T4UHP is working.

Thank you all for the support, you guys rock!

---

