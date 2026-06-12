---
title: "wlanctl-ng trouble"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by BIS on 2005-10-31
Hallo,

posted this in the desktop forum as well - so apologies for the double post...

Trying to get my prism2 usb nic working, Did

apt-get install linux-wlan-ng
modprobe prism2_usb
depmod -a

then

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

I get

wlanctl-ng: No such device

lsmod lists (edited):

prism2_usb 67204 0
p80211 30992 1 prism2_usb
usbcore 104188 4 prism2_usb,usbhid,uhci_hcd


Any ideas on where to begin?

---

### Post by ranf on 2005-10-31
[QUOTE=BIS]
Trying to get my prism2 usb nic working, Did

apt-get install linux-wlan-ng
modprobe prism2_usb
depmod -a

then

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

I get

wlanctl-ng: No such device

lsmod lists (edited):

prism2_usb 67204 0
p80211 30992 1 prism2_usb
usbcore 104188 4 prism2_usb,usbhid,uhci_hcd
[/QUOTE]

Have a look at /etc/modules.conf if the following line is not commented out:
```

alias wlan0 prism2_usb

```

---

### Post by az on 2005-10-31
Look in the log tool.  Post the output of /var/log/messages just as you plug in the device.


Also, do you have any other wireless hardware on that box?

---

### Post by BIS on 2005-11-01
Many thanks,

I don't seem to have a /etc/modules.conf file anywhere though. Could it be called something else. An alias seems to make sense to this problem.

---

### Post by BIS on 2005-11-01
Oh, by the way, this is in /var/log/messages:


Nov  1 17:48:32 localhost kernel: [4296023.885000] prism2usb_init: prism2_usb.o: 0.2.2 Loaded
Nov  1 17:48:32 localhost kernel: [4296023.885000] prism2usb_init: dev_info is: prism2_usb
Nov  1 17:48:32 localhost kernel: [4296023.894000] usbcore: registered new driver prism2_usb

---

### Post by az on 2005-11-01
Okay, please do not be insulted by this but did you do 

*sudo* wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable?


Also, what does 
iwconfig
and ifconfig
say?

---

### Post by BIS on 2005-11-01
I am logged in as root, thanks anyway... :-)

I am seriously beginning to think that this is not a prism2 chipset afterall. It's a Philips cpwua054/00, but I can't sem to determine the chipset... Reason for going prism2 was "A knowledgable friend toll me so" - yes I know...

Any idea how to determine the chipset on this thing? 

root@laptop:~# more /var/log/dmesg | grep usb
[4294679.471000] usbcore: registered new driver usbfs
[4294679.471000] usbcore: registered new driver hub
[4294679.723000] usb 1-1: new full speed USB device using uhci_hcd and address 2

Doesn't seem to be found on boot.

---

### Post by az on 2005-11-01
Well, if you get the prism2_usb messages in /var/log/messages when you put it in, then that is the chipset.

You are not loading the module yourself, are you?  It should hotplug.

---

### Post by BIS on 2005-11-01
I was modprobing it yes...

When I just plug it in I get:

localhost kernel: [4310233.476000] usb 1-1: new full speed USB device using uhci_hcd and address 3

...that's all

---

### Post by ranf on 2005-11-01
[QUOTE=BIS]I was modprobing it yes...

When I just plug it in I get:

localhost kernel: [4310233.476000] usb 1-1: new full speed USB device using uhci_hcd and address 3

...that's all[/QUOTE]
Run `lsusb' before and after plugging it in.
Then you have at least a Vendor-ID:Product-ID to feed google with:
```

Bus 001 Device 003: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
                       ^^^^^^^^^

```

---

### Post by BIS on 2005-11-01
He! never knew lsusb... thanks!!!

I get:

Bus 001 Device 004: ID 083a:5501 Accton Technology Corp.

But google only gives me three hits. Seems to be prism54 - does that mean ndiswrapper or do we have a neater solution?

---

### Post by ranf on 2005-11-01
Did you also try [http://groups.google.com?](http://groups.google.com?)

I am not familiar with Accton or prism54.

---

