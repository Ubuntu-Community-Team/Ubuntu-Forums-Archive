---
title: "Wireless USB stick doesn't work"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by El Torito on 2007-05-29
Hi,

I have a US Robotics wireless USB stick (USR805422) and whenever I plug it in, all USB ports stop working. When I unplug the wireless stick and reboot, everything works fine.

I'm using a brand new installation of Feisty Fawn. The following error appears in my logbook when I plug the stick in:

```
May 29 20:25:27 tim kernel: [  112.952000] usb 4-2: new high speed USB device using ehci_hcd and address 3 
May 29 20:25:27 tim kernel: [  113.104000] usb 4-2: configuration #1 chosen from 1 choice 
May 29 20:25:28 tim kernel: [  113.300000] usb 4-1: USB disconnect, address 2 
May 29 20:25:28 tim kernel: [  113.304000] usb 4-2: USB disconnect, address 3 
May 29 20:25:28 tim kernel: [  113.308000] prism54usb: probe of 4-2:1.0 failed with error -108 
May 29 20:25:28 tim kernel: [  113.312000] usbcore: registered new interface driver prism54usb 
May 29 20:25:28 tim kernel: [  113.592000] usb 1-1: new full speed USB device using uhci_hcd and address 3 
May 29 20:25:28 tim kernel: [  113.732000] usb 1-1: not running at top speed; connect to a high speed hub 
May 29 20:25:28 tim kernel: [  113.756000] usb 1-1: configuration #1 chosen from 1 choice 
May 29 20:25:28 tim kernel: [  113.760000] scsi1 : SCSI emulation for USB Mass Storage devices 
May 29 20:25:28 tim kernel: [  114.000000] usb 1-2: new full speed USB device using uhci_hcd and address 4 
May 29 20:25:28 tim kernel: [  114.144000] usb 1-2: not running at top speed; connect to a high speed hub 
May 29 20:25:29 tim kernel: [  114.184000] usb 1-2: configuration #1 chosen from 1 choice 
May 29 20:25:31 tim kernel: [  116.200000] prism54usb: probe of 1-2:1.0 failed with error -110 
May 29 20:25:31 tim kernel: [  116.200000] usb 1-1: USB disconnect, address 3 
May 29 20:25:31 tim kernel: [  116.200000] usb 1-2: USB disconnect, address 4 
May 29 20:25:31 tim kernel: [  116.200000] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device() 
May 29 20:25:31 tim kernel: [  116.200000]  [<e089b255>] usb_autopm_do_device+0xd5/0xe0 [usbcore] 
May 29 20:25:31 tim kernel: [  116.200000]  [<e0895622>] usb_disconnect+0x122/0x130 [usbcore] 
May 29 20:25:31 tim kernel: [  116.200000]  [<e0895674>] hub_pre_reset+0x44/0x70 [usbcore] 
May 29 20:25:31 tim kernel: [  116.200000]  [<e0896152>] hub_thread+0xc2/0xc20 [usbcore] 
May 29 20:25:31 tim kernel: [  116.200000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50 
May 29 20:25:31 tim kernel: [  116.200000]  [<e0896090>] hub_thread+0x0/0xc20 [usbcore] 
May 29 20:25:31 tim kernel: [  116.200000]  [kthread+186/240] kthread+0xba/0xf0 
May 29 20:25:31 tim kernel: [  116.200000]  [kthread+0/240] kthread+0x0/0xf0 
May 29 20:25:31 tim kernel: [  116.200000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10 
May 29 20:25:31 tim kernel: [  116.200000]  =======================

```

I've looked around for anwsers on other forums but there are very few topics regarding this problem. Can anybody help me? Thanks!!

---

