---
title: "Sierra Wireless 340U (AT&amp;T Beam)"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by Rob_Klingsten on 2013-09-11
Hi folks, I just got this USB modem from AT&T in the USA. I am running 13.04. After fighting with the card in Linux for awhile, I moved it over to my Mac and it works fine over there, so it's not the card or activation problems, etc.

Inserting the card, I see in dmesg:
```
[105915.704555] usb 2-1.6: new high-speed USB device number 17 using ehci-pci
[105915.797576] usb 2-1.6: config 1 has an invalid interface number: 8 but max is 4
[105915.797581] usb 2-1.6: config 1 has an invalid interface number: 9 but max is 4
[105915.797584] usb 2-1.6: config 1 has no interface number 1
[105915.797586] usb 2-1.6: config 1 has no interface number 4
[105915.798072] usb 2-1.6: config 2 has an invalid interface number: 12 but max is 1
[105915.798076] usb 2-1.6: config 2 has an invalid interface number: 13 but max is 1
[105915.798079] usb 2-1.6: config 2 has an invalid interface number: 13 but max is 1
[105915.798081] usb 2-1.6: config 2 has no interface number 0
[105915.798083] usb 2-1.6: config 2 has no interface number 1
[105915.799056] usb 2-1.6: New USB device found, idVendor=1199, idProduct=9051
[105915.799061] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[105915.799063] usb 2-1.6: Product: AirCard 340U
[105915.799066] usb 2-1.6: Manufacturer: Sierra Wireless, Incorporated
[105915.799068] usb 2-1.6: SerialNumber: 013323000430257
[105915.801733] cdc_mbim 2-1.6:2.12: cdc-wdm0: USB WDM device
[105915.801964] cdc_mbim 2-1.6:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:1d.0-1.6, CDC MBIM, 1a:df:3e:d0:e9:a0
```

I can see the device at /dev/cdc-wdm0 but if I try to get it to connect like so:

qmi-network /dev/cdc-wdm0 start

it does this:
```
Starting network with 'qmicli -d /dev/cdc-wdm0 --wds-start-network= --client-no-release-cid'...
error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (12): (null)
verbose call end reason (0,0): [(null)] (null)
Saving state ... (CID: 2)
error: network start failed, no packet data handle
Clearing state...
```

When that command runs, the little LCD on the modem briefly goes from "Ready to connect" to "Searching for network" and then back to "Ready to connect".

What am I missing? Thanks for any help!

---

### Post by Dan_Therrien on 2013-09-17
Hello,

This modem has multiple interfaces that are present the first one as you can see is the mbim driver that attaches to it first (default config which is number 2). You would have to install the libmbim and mbimcli to use it the same way as QMI. The other way I use it is to force the modem to use the other interface by sending a 1 to the bConfigurationValue of the modem this will set it to QMI mode.

Dan

> **Rob_Klingsten said:**
> Hi folks, I just got this USB modem from AT&T in the USA. I am running 13.04. After fighting with the card in Linux for awhile, I moved it over to my Mac and it works fine over there, so it's not the card or activation problems, etc.

Inserting the card, I see in dmesg:
```
[105915.704555] usb 2-1.6: new high-speed USB device number 17 using ehci-pci
[105915.797576] usb 2-1.6: config 1 has an invalid interface number: 8 but max is 4
[105915.797581] usb 2-1.6: config 1 has an invalid interface number: 9 but max is 4
[105915.797584] usb 2-1.6: config 1 has no interface number 1
[105915.797586] usb 2-1.6: config 1 has no interface number 4
[105915.798072] usb 2-1.6: config 2 has an invalid interface number: 12 but max is 1
[105915.798076] usb 2-1.6: config 2 has an invalid interface number: 13 but max is 1
[105915.798079] usb 2-1.6: config 2 has an invalid interface number: 13 but max is 1
[105915.798081] usb 2-1.6: config 2 has no interface number 0
[105915.798083] usb 2-1.6: config 2 has no interface number 1
[105915.799056] usb 2-1.6: New USB device found, idVendor=1199, idProduct=9051
[105915.799061] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[105915.799063] usb 2-1.6: Product: AirCard 340U
[105915.799066] usb 2-1.6: Manufacturer: Sierra Wireless, Incorporated
[105915.799068] usb 2-1.6: SerialNumber: 013323000430257
[105915.801733] cdc_mbim 2-1.6:2.12: cdc-wdm0: USB WDM device
[105915.801964] cdc_mbim 2-1.6:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:1d.0-1.6, CDC MBIM, 1a:df:3e:d0:e9:a0
```

I can see the device at /dev/cdc-wdm0 but if I try to get it to connect like so:

qmi-network /dev/cdc-wdm0 start

it does this:
```
Starting network with 'qmicli -d /dev/cdc-wdm0 --wds-start-network= --client-no-release-cid'...
error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (12): (null)
verbose call end reason (0,0): [(null)] (null)
Saving state ... (CID: 2)
error: network start failed, no packet data handle
Clearing state...
```

When that command runs, the little LCD on the modem briefly goes from "Ready to connect" to "Searching for network" and then back to "Ready to connect".

What am I missing? Thanks for any help!

---

### Post by ben24 on 2013-09-19
I just got an AirCard ("AT&T Beam AC340U") or Sierra Wireless 340U or Netgear 340U, last week, and I'm running Ubuntu 13.04.  I've tried it in Windows and verified that it does indeed connect, so it's not a problem on that end.  

I'm trying to get it to work in Ubuntu then potentially migrate it over to a debian based raspberry-Pi.  I'm fairly new at configuring remote connectivity via Ubuntu, so if anyone who's had this work in the past/present can provide step-by-step on how they got it to work, I'd very much appreciate it.

My dmesg spits out the following:
```
[    2.690358] usb 2-2: New USB device found, idVendor=1199, idProduct=9051
[    2.690362] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.690365] usb 2-2: Product: AirCard 340U
[    2.690368] usb 2-2: Manufacturer: Sierra Wireless, Incorporated
[    2.690372] usb 2-2: SerialNumber: 013323000444647
[    2.928049] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    3.252227] EXT4-fs (sda5): recovery complete
[    3.257887] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
```

I then, per your implied work, installed the Qualcomm MSM Interface protocol (sudo apt-get install libqmi-glib0 and apt-get install libqmi-utils)

In going into /dev, I also see that it's filled out cdc-wdm0 as the device, and I get your exact same error mentioned.

Dan, I'd love to use the method you've described, but could you please clarify (step-by-step for the uber newbie) how to go about [COLOR=#000000]sending a 1 to the bConfigurationValue of the modem to set it to QMI mode?
 I assume this would also remove the need to install the [/COLOR][COLOR=#000000]libmbim and mbimcli libraries?
[/COLOR]
Till then, I'll keep trying.
Thanks for any information.

> **Rob_Klingsten said:**
> Hi folks, I just got this USB modem from AT&T in the USA. I am running 13.04. After fighting with the card in Linux for awhile, I moved it over to my Mac and it works fine over there, so it's not the card or activation problems, etc.

Inserting the card, I see in dmesg:
```
[105915.704555] usb 2-1.6: new high-speed USB device number 17 using ehci-pci
[105915.797576] usb 2-1.6: config 1 has an invalid interface number: 8 but max is 4
[105915.797581] usb 2-1.6: config 1 has an invalid interface number: 9 but max is 4
[105915.797584] usb 2-1.6: config 1 has no interface number 1
[105915.797586] usb 2-1.6: config 1 has no interface number 4
[105915.798072] usb 2-1.6: config 2 has an invalid interface number: 12 but max is 1
[105915.798076] usb 2-1.6: config 2 has an invalid interface number: 13 but max is 1
[105915.798079] usb 2-1.6: config 2 has an invalid interface number: 13 but max is 1
[105915.798081] usb 2-1.6: config 2 has no interface number 0
[105915.798083] usb 2-1.6: config 2 has no interface number 1
[105915.799056] usb 2-1.6: New USB device found, idVendor=1199, idProduct=9051
[105915.799061] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[105915.799063] usb 2-1.6: Product: AirCard 340U
[105915.799066] usb 2-1.6: Manufacturer: Sierra Wireless, Incorporated
[105915.799068] usb 2-1.6: SerialNumber: 013323000430257
[105915.801733] cdc_mbim 2-1.6:2.12: cdc-wdm0: USB WDM device
[105915.801964] cdc_mbim 2-1.6:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:1d.0-1.6, CDC MBIM, 1a:df:3e:d0:e9:a0
```

I can see the device at /dev/cdc-wdm0 but if I try to get it to connect like so:

qmi-network /dev/cdc-wdm0 start

it does this:
```
Starting network with 'qmicli -d /dev/cdc-wdm0 --wds-start-network= --client-no-release-cid'...
error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (12): (null)
verbose call end reason (0,0): [(null)] (null)
Saving state ... (CID: 2)
error: network start failed, no packet data handle
Clearing state...
```

When that command runs, the little LCD on the modem briefly goes from "Ready to connect" to "Searching for network" and then back to "Ready to connect".

What am I missing? Thanks for any help!

---

