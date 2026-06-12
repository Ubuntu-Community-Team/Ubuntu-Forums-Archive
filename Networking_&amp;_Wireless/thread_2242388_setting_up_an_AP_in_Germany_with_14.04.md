---
title: "setting up an AP in Germany with 14.04"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by russ12 on 2014-09-01
Hello again, I am now in Germany and the wired connection works great!  But I still can't get the AP to work.  The computer is a lenovo w530 and I am running ubuntu 14.04.  The two options I have for wireless are the WLAN card- Intel centrino ultimate-n 6300 (which says doesnt support AP?) and a netgear n600.  I dont think my computer even recognizes the netgear.  Any help would be most appreciated.

---

### Post by ian-weisser on 2014-09-01
Can the 6300 do ad-hoc? You can create an ad-hoc network instead of an access point.

Plug in the n600, then look at the last lines of /var/log/dmesg to see if the kernel recognized it. If the kernel recognizes it, we can perhaps get it to work. If the kernel does not recognize it, then it's merely decorative (worthless to you).

---

### Post by russ12 on 2014-09-01
I have an android phone and I have read ad-hoc isn't seen by them? Is this true?

is the /var/log/dmesg the same as doing lsusb?  Cause lsusb recognizes the netgear and has its ID.  I see reference to a usb device in dmesg with a failed attempt to initialize.

---

### Post by ian-weisser on 2014-09-01
> **russ12 said:**
> I have an android phone and I have read ad-hoc isn't seen by them? Is this true?

Only one way to find out for sure.


> **russ12 said:**
> is the /var/log/dmesg the same as doing lsusb?  Cause lsusb recognizes the netgear and has its ID.  I see reference to a usb device in dmesg with a failed attempt to initialize.

What's the *exact* error message, with context?

---

### Post by russ12 on 2014-09-02
```
[   25.003510] usb 1-1.4: new full-speed USB device number 5 using ehci-pci
[   25.008482] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   25.027523] systemd-udevd[512]: renamed network interface wlan0 to wlan1
[   25.103483] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21e6
[   25.103486] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   25.103488] usb 1-1.4: Product: BCM20702A0
[   25.103489] usb 1-1.4: Manufacturer: Broadcom Corp
[   25.103490] usb 1-1.4: SerialNumber: 689423EE56CF
[   25.116468] Bluetooth: Core ver 2.17
[   25.116480] NET: Registered protocol family 31
[   25.116482] Bluetooth: HCI device and connection manager initialized
[   25.116489] Bluetooth: HCI socket layer initialized
[   25.116491] Bluetooth: L2CAP socket layer initialized
[   25.116495] Bluetooth: SCO socket layer initialized
[   25.117632] usbcore: registered new interface driver btusb
[   25.117948] usb 1-1.4: Direct firmware load failed with error -2
[   25.117950] usb 1-1.4: Falling back to user helper
[   25.118456] Bluetooth: can't load firmware, may not work correctly
[   25.141537] usbcore: registered new interface driver ndiswrapper
[   25.146411] ppdev: user-space parallel port driver
[   25.184427] cfg80211: World regulatory domain updated:
[   25.184429] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.184430] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.184431] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.184432] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.184433] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.184434] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.519423] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
[   26.127811] init: failsafe main process (897) killed by TERM signal
[   26.338494] usb 1-1.4: USB disconnect, device number 5
[   26.730490] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.730492] Bluetooth: BNEP filters: protocol multicast
[   26.730499] Bluetooth: BNEP socket layer initialized
[   26.731099] Bluetooth: RFCOMM TTY layer initialized
[   26.731104] Bluetooth: RFCOMM socket layer initialized
[   26.731107] Bluetooth: RFCOMM ver 1.11
[   27.385162] init: cups main process (1039) killed by HUP signal
[   27.385171] init: cups main process ended, respawning
```

---

### Post by russ12 on 2014-09-04
Anyone?

---

### Post by ian-weisser on 2014-09-04
Well, to me it looks like:

```
[   25.027523] systemd-udevd[512]: renamed network interface wlan0 to wlan1
```

You may have an old udev rule causing the renaming of the wlan device. But that's not a failure or crash. That's the system working properly.

```
[   25.117948] usb 1-1.4: Direct firmware load failed with error -2
[   25.117950] usb 1-1.4: Falling back to user helper
[   25.118456] Bluetooth: can't load firmware, may not work correctly

[   26.730490] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.730492] Bluetooth: BNEP filters: protocol multicast
[   26.730499] Bluetooth: BNEP socket layer initialized
[   26.731099] Bluetooth: RFCOMM TTY layer initialized
[   26.731104] Bluetooth: RFCOMM socket layer initialized
[   26.731107] Bluetooth: RFCOMM ver 1.11
```

This is indeed a failure of a Bluetooth device, followed by what appears to be a successful driver initialization.
If your Bluetooth works, then the system successfully recovered from the failure

```
[   25.141537] usbcore: registered new interface driver ndiswrapper
```

Ah, you are trying to use Windows wi-fi drivers.

---

### Post by russ12 on 2014-09-04
I have installed some Windows drivers because that seemed to be the general approach for getting the n600 to work.  How can I tell for sure my WLAN card isnt't the wlan1 spot?

---

### Post by ian-weisser on 2014-09-04
> **russ12 said:**
> How can I tell for sure my WLAN card isnt't the wlan1 spot?

Your WLAN card should be the wlan1 spot.
Use the 'ifconfig' command to find out.

---

### Post by russ12 on 2014-09-06
The WLAN card is wlan1.  Unfortuneately, when I try to initiate the access point, it tells me the card doesn't support this feature.  On do the netgear card?

---

