---
title: "[SOLVED] What wireless driver am I using?"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by absolutezero1287 on 2008-06-15
I'm using the wireless G USB adapter from linksys (wusb54gc) and it worked flawlessly from the get-go. But what driver is it using? I'd like to know because I'm working on another distro for the same comp and I'm trying to get the internet to work on it.

Selected output of lsusb:

Bus 004 Device 004: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 004 Device 002: ID 13b1:0020 Linksys 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Ayuthia on 2008-06-16
> **absolutezero1287 said:**
> I'm using the wireless G USB adapter from linksys (wusb54gc) and it worked flawlessly from the get-go. But what driver is it using? I'd like to know because I'm working on another distro for the same comp and I'm trying to get the internet to work on it.

Selected output of lsusb:

Bus 004 Device 004: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 004 Device 002: ID 13b1:0020 Linksys 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Have you tried using 'lshw -C network' (without quotes)?  I think that it works with the USB wireless devices.

---

### Post by kevdog on 2008-06-16
lshw -C network only works for PCI based devices.  For USB devices there is no easy way.  The only way I know is to do a lsmod (which lists all the currently loaded kernel modules) and then just peruse the output.  If you have an idea of the chipset of the device it would make things easier.

---

### Post by absolutezero1287 on 2008-06-16
After looking at this [http://www.decimation.com/markw/2007/12/04/wusb54gc-and-vista/](http://www.decimation.com/markw/2007/12/04/wusb54gc-and-vista/) I discovered that my wireless USB adapter uses the Ralink RT2501USB chipset. 


:: This is the output of lsmod (some parts removed to conserve space) ::

root@desktop:~# lsmod
Module                  Size  Used by
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
cfg80211               15112  1 mac80211
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
button                  9232  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_i810                5636  0 
i2c_algo_bit            7300  1 i2c_i810
intel_agp              25492  1 
i2c_core               24832  2 i2c_i810,i2c_algo_bit
agpgart                34760  3 drm,intel_agp
iptable_nat             8324  0 
nf_nat                 20396  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  8 iptable_nat
nf_conntrack           66752  7 
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_piix               19588  2 
ssb                    34308  1 b44
mii                     6400  1 b44
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  8 rt73usb,rt2x00usb,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd


:: Continued ::
The parts that I find interesting are rt73usb, rt2x00usb, mac80211, and rt2x00lib. I'm pretty sure that the driver is rt73usb but I'm not 100% sure. What is mac80211, can anyone help?

---

### Post by absolutezero1287 on 2008-07-04
After some research I have found that my wireless USB adapter (WUSB54GC) uses the rt73usb driver.

---

