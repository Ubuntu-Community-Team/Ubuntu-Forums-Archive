---
title: "Hardy 8.04 - Prism 2.x problem"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by weegie on 2008-07-21
Everything worked fine in Gutsy 7.10. Since upgrading to Hardy 8.04 I no longer have a working wireless connection using a Sitecom WL-012 usb adapter.

Can anyone help?
Thanks in advance..

The following responses to various commands were obtained.

computer@computer-desktop:~$ lsusb 
Bus 004 Device 004: ID 13fe:1e00 Kingston Technology Company Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 09aa:3642 Intersil Corp. Prism 2.x 802.11b Adapter 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 050d:0841 Belkin Components 
Bus 002 Device 003: ID 0451:2077 Texas Instruments, Inc. TUSB2077 Hub 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

computer@computer-desktop:~$ lsmod

(Relevant results shown)
Module                  Size  Used by 
prism2_usb             75908  0 
p80211                 33160  1 prism2_usb 
usbcore               146028  7 prism2_usb,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd 


computer@computer-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.


computer@computer-desktop:~$ sudo lshw -C network
[sudo] password for computer: 
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:10:dc:28:c0:2d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

computer@computer-desktop:~$ dmesg

   28.985039] prism2usb_init: prism2_usb.o: 0.2.8 Loaded 
[   28.985045] prism2usb_init: dev_info is: prism2_usb 
[   29.655036] NET: Registered protocol family 17 
[   29.989161] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed) 
[   31.991658] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed) 
[   31.991668] hfa384x_drvr_start: cmd_initialize() failed on two attempts, results -5 and -5 
[   31.992644] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5 

computer@computer-desktop:~$

---

