---
title: "External hard drive"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2009-09-06
I have an ultra hard drive and an IBM lappy.  I know the hard drive used to work...just plug in the USB and its working...but while it powers on it just sits there...no recognition...I was probably using 7. something last time I tried to use it.

---

### Post by scragar on 2009-09-06
Plug it in and list devices:
```
ls -l /dev/disk/by-id 
```
And look for the device(if you don't know what it is don't worry, remove it, run the command again, and look for what's missing). When you've found the device post it's lines here and I'll take a look.

---

### Post by AutumnPhoenix on 2009-09-06
scrag...this is probably bad..absolutely no difference between when the device is plugged in and when its not.  I tried rebooting the device & my computer

---

### Post by scragar on 2009-09-06
```
dmesg | tail
```
What about the output of that? It should show the system picking up the disk
(For reference here's what it shows after I plugged in a pen drive:```

usb 3-1.2: new full speed USB device using ohci_hcd and address 15
usb 3-1.2: not running at top speed; connect to a high speed hub
usb 3-1.2: configuration #1 chosen from 1 choice
scsi39 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 15
usb-storage: waiting for device to settle before scanning
scsi 39:0:0:0: Direct-Access     Generic  USB  SD Reader   1.00 PQ: 0 ANSI: 0 CCS
sd 39:0:0:0: Attached scsi generic sg4 type 0
sd 39:0:0:0: [sdc] Attached SCSI removable disk
usb-storage: device scan complete
```)

---

### Post by AutumnPhoenix on 2009-09-06
Output the same weather plugged or unpluged

> COMPUTER@LOCATION:~$ dmesg | tail
[  262.718451] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  264.169085] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  266.004019] ath0: no IPv6 routers present
[  323.100033] Clocksource tsc unstable (delta = -269241279 ns)
[  411.118656] type=1503 audit(1252275629.171:10): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/var/run/dhclient.ath0.leases" pid=5148 profile="/sbin/dhclient3"
[  421.212027] ath0: no IPv6 routers present
[  626.965507] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  626.970689] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  637.248013] ath0: no IPv6 routers present
[ 3804.503661] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.


---

### Post by scragar on 2009-09-06
Wait, it doesn't change when you plug it in? Do other USB devices work in the same port? Can you try the device in another port?

From the looks of it linux isn't even able to detect that you've connected a device, let alone interact with it.

---

### Post by AutumnPhoenix on 2009-09-06
all the USB drives are in fine working order.

yep, it looks as if its not being recognized at all, which is strange becuase it DID recognize it nearly 2 years ago when I was running 7.something linux

---

### Post by scragar on 2009-09-06
> **AutumnPhoenix said:**
> all the USB drives are in fine working order.

yep, it looks as if its not being recognized at all, which is strange becuase it DID recognize it nearly 2 years ago when I was running 7.something linux

Any device you plug in should show up in dmesg if it identifies itself, even if it can't be used for some reason. The upgrade won't have changed anything, it's a hardware fault of some kind.

---

### Post by AutumnPhoenix on 2009-09-06
well, I'll take it to work on tuesday and see if the hd works in that pc...it may be the HD as its been a couple years since I even touched it.

---

