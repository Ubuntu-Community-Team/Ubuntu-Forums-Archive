---
title: "Airlink 5026 usb wireless on Hardy"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by ultianimal on 2008-11-12
Hi all.  I'm trying to come forward to top Ubuntu.  I've been running Feisty for over 6 months now with an Airlink USB wireless.  I upgraded to Gutsy and lost the wireless but was able to get it back.  Then I went to Hardy and now I'm dead in the water.  I've been following different threads on installing the drivers for my card but nothing has worked.  Here's my (I believe) relevant information.

iwconfig output:
lo no wireless extensions
eth0 no wireless extensions

lsusb output:
Bus 002 Device 003: ID 0951:1607 Kingston Technology 
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lsmod |grep rt  output:
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
rt2500usb              26368  0 
rt2x00usb              14720  1 rt2500usb
rt2x00lib              25344  2 rt2500usb,rt2x00usb
rfkill                 10144  1 rt2x00lib
input_polldev           6928  1 rt2x00lib
crc_itu_t               3584  1 rt2x00lib
mac80211              192532  2 rt2x00usb,rt2x00lib
usbcore               170288  7 usb_storage,libusual,rt2500usb,rt2x00usb,ehci_hcd,ohci_hcd

contents of /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid My Airport
wireless-key 9999999999

contents of /etc/modprobe.d/blacklist

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist rt73usb
blacklist rt2570

As evidenced by my iwconfig output, I can't even see
wlan0 anymore.  (sigh)  Any help out there.
I've got the latest rt2570 drivers from serial monkey but hesitate to reinstall them as I've done it once before and got nowhere.  I feel like I've forgotten a step and don't know what it is.

---

