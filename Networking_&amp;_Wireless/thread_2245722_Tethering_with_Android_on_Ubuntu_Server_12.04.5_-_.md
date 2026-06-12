---
title: "Tethering with Android on Ubuntu Server 12.04.5 - Sometimes works, mostly doesn't"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by Leif_Bloomquist on 2014-09-25
Hi all,

I'm running Ubuntu Server 12.04.5 LTS in VMWare 6.0.3 build-1895310 in a Windows 7 64-bit host.

I've run into a weird problem when tethering to Samsung Galaxy SII with Android 4.0.4.   Most of the time it doesn't work, but sometimes it does and I can't figure out what the magic conditions to do so are. 

  I had this working a while ago on an old computer - didn't have the presence of mind to back up the VM as it "just worked" before.  Same issue in 14.04, but I wasn't able to get it to work a single time, and haven't dug as deeply there.


Here's the output from dmesg with some commentary IN CAPS.  I plugged my phone in with USB, the device is picked up by VMWare, and then I checked "USB tethering" on the phone.  Worked fine (I had usb0 under ifconfig -a, had an IP address, etc.)   I then disconnected it and reconnected it a few hours later - instant disconnect (and USB tethering auto-unchecks on the phone).   Same over and over.  Any suggestions?


WORKING:


[96995.027235] usb 1-1: new high-speed USB device number 18 using ehci-pci
[96995.333427] usb 1-1: New USB device found, idVendor=04e8, idProduct=6863
[96995.333437] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[96995.333442] usb 1-1: Product: Android
[96995.333446] usb 1-1: Manufacturer: Android
[96995.333449] usb 1-1: SerialNumber: 5f58589f
[96995.371425] usbcore: registered new interface driver cdc_ether
[96995.390505] rndis_host 1-1:1.0 usb0: register 'rndis_host' at usb-0000:02:03.0-1, RNDIS device, 02:0d:5f:53:38:35
[96995.391213] usbcore: registered new interface driver rndis_host


NORMAL DISCONNECT:


[100509.148595] usb 1-1: USB disconnect, device number 18
[100509.166440] rndis_host 1-1:1.0 usb0: unregister 'rndis_host' usb-0000:02:03.0-1, RNDIS device


NOT WORKING:


[163524.720035] usb 1-1: new high-speed USB device number 19 using ehci-pci
[163525.043247] usb 1-1: New USB device found, idVendor=04e8, idProduct=685d
[163525.043254] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[163525.043257] usb 1-1: Product: Android
[163525.043259] usb 1-1: Manufacturer: Android
[163525.043261] usb 1-1: SerialNumber: 5f58589f
[163985.026801] usb 1-1: USB disconnect, device number 19
[170044.179081] usb 1-1: new high-speed USB device number 20 using ehci-pci
[170044.465170] usb 1-1: New USB device found, idVendor=04e8, idProduct=685d
[170044.465180] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[170044.465189] usb 1-1: Product: Android
[170044.465194] usb 1-1: Manufacturer: Android
[170044.465198] usb 1-1: SerialNumber: 5f58589f
[170054.655667] usb 1-1: USB disconnect, device number 20
[170057.781428] usb 1-1: new high-speed USB device number 21 using ehci-pci
[170058.083536] usb 1-1: New USB device found, idVendor=04e8, idProduct=685d
[170058.083546] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[170058.083552] usb 1-1: Product: Android
[170058.083556] usb 1-1: Manufacturer: Android
[170058.083559] usb 1-1: SerialNumber: 5f58589f

etc. etc.


Thanks for any insight!

---

