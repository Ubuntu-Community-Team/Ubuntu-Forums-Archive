---
title: "WUSBC54GC worked once on ndiswrapper then anymore"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by mamendes on 2008-08-29
Hi,

I have the WUSB54GC adapter and using ndiswrapper I could use it for an entire day on Ubuntu.
I left the computer on during the nights but on the third day it went off.
I tried to reload ndiswrapper

```
sudo modprobe -r ndiswrapper
sudo depmod -a
<unplug and plug again>
sudo modprobe ndiswrapper
```

I tried and tried, rebooted, pluged and unpluged but nothing. 
It is not even shown on lsusb anymore.

Here is what dmesg shows:
```

[ 1918.692780] usbcore: deregistering interface driver ndiswrapper
[ 1925.657848] usb 4-5: new high speed USB device using ehci_hcd and address 47
[ 1926.520741] usb 4-5: new high speed USB device using ehci_hcd and address 51
[ 1931.326409] usb 4-5: new high speed USB device using ehci_hcd and address 76
[ 1931.813775] usb 4-5: new high speed USB device using ehci_hcd and address 78
[ 1931.894744] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1931.906476] usbcore: registered new interface driver ndiswrapper

```

Does anyone have an idea on what should I do to have it working again? I'm assuming the driver is installed ok (since it worked once).

Btw, the adapter is not damaged, I tested it on windows.

Thanks.

---

### Post by caljohnsmith on 2008-08-29
If you do:
```
ndiswrapper -l
```
Does it show the installed Windows driver, and does it say anything about an "alternate" driver? After you do the "sudo modprobe ndiswrapper", then try:
```
sudo iwlist wlan0 scan
```
Does that show any available wireless networks? If not, does the following return anything:
```
lsmod | grep ndiswrapper
```

---

### Post by mamendes on 2008-08-29
> **caljohnsmith said:**
> If you do:
```
ndiswrapper -l
```
```
rt73 : driver installed
```

> **caljohnsmith said:**
> Does it show the installed Windows driver, and does it say anything about an "alternate" driver? After you do the "sudo modprobe ndiswrapper", then try:
```
sudo iwlist wlan0 scan
```

```
wlan0     Interface doesn't support scanning.
```

> **caljohnsmith said:**
> Does that show any available wireless networks? If not, does the following return anything:
```
lsmod | grep ndiswrapper
```
```

ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

```

Thanks for the help. Does it look like anything?

---

### Post by caljohnsmith on 2008-08-29
Might be that another driver is getting in the way of ndiswrapper, so please post:
```
lsmod
```

---

### Post by mamendes on 2008-08-30
I got it running on openSuse just by installing it using live CD (no ndiswrapper).
I'll keep on that by now, in a couple of weeks I'll try again on Ubuntu.

Thanks for the help.

---

### Post by Tom--d on 2008-08-30
Do:

Unplug the wireless
then
```
sudo modprobe -d ndiswrapper
```
Then do:
```
sudo modprobe rt73usb
``` (Thats if its a USB if not, just change it to rt73)

---

