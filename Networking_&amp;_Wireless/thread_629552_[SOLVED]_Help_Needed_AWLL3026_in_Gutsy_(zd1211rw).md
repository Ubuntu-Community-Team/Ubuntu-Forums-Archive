---
title: "[SOLVED] Help Needed: AWLL3026 in Gutsy (zd1211rw)"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by sceo on 2007-12-02
Sorry for the repost; my subject line was wrong and while you can edit the post - I couldn't find that you could edit your subject.

I got an Airlink 101 cuz I heard they worked pretty well out of the box on Ubuntu. My bcm43xx wasn't working too well with ndiswrapper or without (same behavior as I will describe with this card), so I bought this Airlink USB.

The card is recognized as being plugged in (lsusb shows a Zydas), vendor # is 0ace:1215. When I run iwlist scanning (as superuser) then it displays all kinds of wonderful information (about my channel, the MAC addr of my access point, my broadcasted ssid, everything). nm-applet shows the network and a very strong signal, and when I click it it asks me for my WPA personal key. I enter the correct key, and nm-applet icon starts the spinning motion. It goes for a long time (the tooltip says something like 'waiting for network key from <mynetwork>'), then just stops and there's no connection.

It seems so close, and ironically - this is the same behavior that my broadcom was exhibiting when I tried that one. This is a fresh install of Gutsy on a brand new drive. I intend to install Gutsy from bare, get wireless working, then take care of everything else. What's getting in the way of it connecting?

I tried switching from WPA, to WEP, to no encryption. Same behavior every time. Would LOVE some thinking on this! I made a commitment to rid myself of Micro$oft and so this brand new SATA drive is itching for some Free Software - but can't download any!

I have an ipw3945 in my Dell Laptop which connects to this network with WPA no problem.

Thanks in advance for any help or suggestions, Community!

---

### Post by sceo on 2007-12-02
I've tried disabling extraneous hardware in the BIOS (onboard firewire, onboard sound) and removing an additional PCI USB card I had... trying to slim down the hardware in case there is some sort of conflict.  No help there.  I also read that possibly disabling IPv6 might help; did that, but also no help.  I'm seeing some stuff in my /var/log folder that could be relevant; will post soon.

---

### Post by sceo on 2007-12-03
I've tried to post what I thought were relevant sections of each file.  Please let me know if any of this is helpful.

**daemon.log**
```

Dec  3 09:37:31 whitegold NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Dec  3 09:37:31 whitegold NetworkManager: <info>  SUP: response was 'OK' 
Dec  3 09:37:31 whitegold NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Dec  3 09:37:31 whitegold NetworkManager: <info>  SUP: response was 'OK' 
Dec  3 09:37:31 whitegold NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec  3 09:37:31 whitegold NetworkManager: <info>  SUP: response was 'OK' 
Dec  3 09:37:31 whitegold NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec  3 09:37:36 whitegold NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Dec  3 09:38:09 whitegold last message repeated 6 times
Dec  3 09:38:30 whitegold last message repeated 4 times
Dec  3 09:38:31 whitegold NetworkManager: <info>  Activation (eth0/wireless): association took too long (>60s), failing activation. 
Dec  3 09:38:31 whitegold NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec  3 09:38:31 whitegold NetworkManager: <info>  Activation (eth0) failed for access point (its530somewhere) 
Dec  3 09:38:31 whitegold NetworkManager: <info>  Activation (eth0) failed. 
Dec  3 09:38:31 whitegold NetworkManager: <info>  Deactivating device eth0. 
Dec  3 09:38:31 whitegold NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Dec  3 09:38:31 whitegold NetworkManager: <info>  SUP: response was 'OK' 
Dec  3 09:38:31 whitegold NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Dec  3 09:38:31 whitegold NetworkManager: <info>  SUP: response was 'OK' 
Dec  3 09:38:31 whitegold NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Dec  3 09:38:31 whitegold NetworkManager: <info>  SUP: response was 'OK' 

```

**dmesg**
```

[   54.655849] usb 7-3: reset high speed USB device using ehci_hcd and address 3
[   54.873841] zd1211rw 7-3:1.0: firmware version 4725
[   54.915802] zd1211rw 7-3:1.0: zd1211b chip 0ace:1215 v4810 high 00-11-a3 AL2230_RF pa0 ---NS
[   54.918332] zd1211rw 7-3:1.0: eth0
[   54.918344] usbcore: registered new interface driver zd1211rw

```

**kern.log**
```

Dec  3 09:37:31 whitegold kernel: [   96.575659] NET: Registered protocol family 17
Dec  3 09:37:31 whitegold kernel: [   97.014750] SoftMAC: Open Authentication completed with 00:e0:b8:6c:c1:f8
Dec  3 09:40:05 whitegold kernel: [  250.621464] usb 7-4: new high speed USB device using ehci_hcd and address 4
Dec  3 09:40:05 whitegold kernel: [  250.754255] usb 7-4: configuration #1 chosen from 1 choice
Dec  3 09:40:05 whitegold kernel: [  250.831574] usbcore: registered new interface driver libusual

```

**messages**
```

Dec  3 09:37:20 whitegold dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec  3 09:37:31 whitegold kernel: [   96.575659] NET: Registered protocol family 17
Dec  3 09:37:31 whitegold kernel: [   97.014750] SoftMAC: Open Authentication completed with 00:e0:b8:6c:c1:f8
Dec  3 09:40:05 whitegold kernel: [  250.621464] usb 7-4: new high speed USB device using ehci_hcd and address 4
Dec  3 09:40:05 whitegold kernel: [  250.754255] usb 7-4: configuration #1 chosen from 1 choice
Dec  3 09:40:05 whitegold kernel: [  250.831574] usbcore: registered new interface driver libusual

```

**user.log**
```

Dec  2 20:51:57 whitegold dhcdbd: Started up.
Dec  2 20:54:50 whitegold dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec  2 20:56:57 whitegold dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec  3 09:20:00 whitegold dhcdbd: Started up.
Dec  3 09:36:53 whitegold dhcdbd: Started up.
Dec  3 09:37:20 whitegold dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason

```

---

### Post by sceo on 2007-12-04
As it turns out, I replaced by cheap-o ($17) Gateway router with a Linksys WRT54G and everything just worked out of the box with WPA.  I guess something just wasn't right with that router.  Perhaps if I upgraded the firmware or something - but it really is such a cheap-o router I'm sure I did the right thing getting a new one.

Incidentally, I bought the WRT54G to try to set it up as a bridge, but decided to just try it as a replacement router just to see.

So, lesson is - if you have that infinitely spinning network-applet in the corner, try swapping your router!

---

### Post by MadScientist305 on 2008-03-09
I have a Buffalo Airstation WHR-G54S as my router, and I have the same problem. I am also using Gutsy.

---

