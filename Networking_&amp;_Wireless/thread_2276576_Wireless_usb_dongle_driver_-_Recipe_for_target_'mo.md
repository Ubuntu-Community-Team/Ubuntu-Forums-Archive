---
title: "Wireless usb dongle driver - Recipe for target 'modules' failed"
date: 2015-05-03
forum: Networking &amp; Wireless
---

### Post by cagdasalagoz-m on 2015-05-03
Hi everyone,

I recently buy a usb dongle for my old computer. It says on the box that supports "Windows, OS X, Linux" it was a cheap device. It comes with a little CD that has drivers for every OS's in it. 

They have a script in it for linux named "install.sh" i started it first it has some authentication problems so i started it again as root (sudo su) it has some warnings while installing than it shows 2 error and stops installing. By the way I checked the lsusb and it sees the product. I can connect with the ethernet without problem. I used the dongle with Windows doesn't have a problem. This is the device: [Link]("http://www.aliexpress.com/item/Free-Shipping-Brand-New-USB-Wifi-adapter-dongle-wireless-N-150Mbps-RALINK-RA5370-for-Raspberry-Pi/689095682.html")

Here is my scripts output, i will be happy if someone can help.

Lsusb -v output for device:
```
Bus 001 Device 006: ID 148f:7601 Ralink Technology, Corp. Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.01
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x7601 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           74
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              160mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           8
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
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
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
        bEndpointAddress     0x09  EP 9 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0



```

```
torak@torak-desktop:~/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ sudo su[sudo] password for torak: 
root@torak-desktop:/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911# ./install.sh 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911.tar.gz
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/runwpa
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_tdls.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_security.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sreset.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_io.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ap.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/wlan0dhcp
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/pci_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/hal_com.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/wifi.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/HalPwrSeqCmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_android.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/nic_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ieee80211.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_ops.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ethernet.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_sreset.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_ops_linux.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_conf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/linux/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/linux/wireless.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_version.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/h2clbk.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_ops.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_tdls.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_event.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ap.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/hal_intf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/sta_info.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/autoconf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_security.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_io.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/circ_buf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/basic_types.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ip.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/if_ether.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_sdio.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/Makefile
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/Kconfig
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_com.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/HalPwrSeqCmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/clean
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.19.0-15-generic/build M=/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-15-generic'
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_security.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_debug.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_io.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_query.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_set.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ieee80211.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme_ext.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_wlan_util.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_pwrctrl.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_rf.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_recv.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sta_mgt.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ap.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_xmit.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_p2p.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_tdls.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_br_ext.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_iol.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sreset.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/rtw_efuse.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_intf.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_com.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.o
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.c: In function ‘PHY_RFShadowRefresh’:
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.c:1020:37: warning: iteration 63u invokes undefined behavior [-Waggressive-loop-optimizations]
    RF_Shadow[eRFPath][Offset].Value = 0;
                                     ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.c:1018:3: note: containing loop
   for (Offset = 0; Offset <= RF6052_MAX_REG; Offset++)
   ^
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_xmit.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/osdep_service.o
  CC [M]  /home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:3: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
   ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:11: warning: assignment makes pointer from integer without a cast
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
           ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:3: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
   ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:9: warning: assignment makes pointer from integer without a cast
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
         ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:326:9: warning: assignment makes pointer from integer without a cast
   entry = create_proc_read_entry("log_level", S_IFREG | S_IRUGO,
         ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:332:8: error: dereferencing pointer to incomplete type
   entry->write_proc = proc_set_log_level;
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:348:21: warning: assignment makes pointer from integer without a cast
   padapter->dir_dev = create_proc_entry(dev->name,
                     ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:379:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("write_reg", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:385:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_write_reg;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:387:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("read_reg", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:393:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_read_reg;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:396:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("fwstate", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:404:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("sec_info", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:412:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("mlmext_state", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:420:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("qos_option", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:427:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("ht_option", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:434:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("rf_info", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:441:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("ap_info", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:448:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("adapter_state", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:455:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("trx_info", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:462:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("mac_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:469:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("mac_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:476:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("mac_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:483:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("bb_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:490:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("bb_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:497:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("bb_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:504:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("rf_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:511:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("rf_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:520:9: warning: assignment makes pointer from integer without a cast
   entry = create_proc_read_entry("rf_reg_dump3", S_IFREG | S_IRUGO,
         ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:527:9: warning: assignment makes pointer from integer without a cast
   entry = create_proc_read_entry("rf_reg_dump4", S_IFREG | S_IRUGO,
         ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:537:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("all_sta_info", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:555:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("best_channel", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:561:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_best_channel;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:564:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("rx_signal", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:570:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_signal;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:572:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("ht_enable", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:578:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ht_enable;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:580:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("cbw40_enable", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:586:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_cbw40_enable;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:588:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("ampdu_enable", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:594:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ampdu_enable;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:596:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("rx_stbc", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:602:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_stbc;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:605:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("path_rssi", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:608:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("vid", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:615:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("pid", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:622:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("rssi_disp", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:628:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rssi_disp;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:631:8: warning: assignment makes pointer from integer without a cast
  entry = create_proc_read_entry("sreset", S_IFREG | S_IRUGO,
        ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:637:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_sreset;
       ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c: At top level:
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:999:2: warning: initialization from incompatible pointer type
  .ndo_select_queue = rtw_select_queue,
  ^
/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:999:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’)
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o' failed
make[2]: *** [/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] Error 1
Makefile:1394: recipe for target '_module_/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911' failed
make[1]: *** [_module_/home/torak/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-15-generic'
Makefile:584: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```

---

### Post by Vladlenin5000 on 2015-05-04
Hi and welcome.

First of all, you're using a script to install Realtek drivers and your hardware is Ralink/Mediatek, supposedly.
Now, you probably missed it but there's a sticky in this section: [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108")
It provides instructions for the initial troubleshooting and a script to find out more info about your system. Please run it and post the results. Please use code tags for posting the script results.

---

### Post by Bucky Ball on 2015-05-04
Welcome. Plug it in, open a terminal and:

```
sudo lshw -C network
```

Hit enter. Post the output here.

You say you can connect with the internet without a problem. You mean on Ubuntu or Windows? Silly question perhaps, but it was a bit unclear.

---

### Post by chili555 on 2015-05-04
Please try: [http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation)

---

