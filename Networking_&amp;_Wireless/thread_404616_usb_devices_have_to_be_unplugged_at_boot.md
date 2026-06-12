---
title: "usb devices have to be unplugged at boot?"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by elj4176 on 2007-04-08
I just installed Feisty Fawn for a mythtv box and everything works great except my usb devices. This is not a Feisty Fawn issue either since I tried 2 versions of knoppmyth and an edgy install with the same issues.
The wireless usb stick works fine if I plug it in after the boot has completed. Same with the usb mouse. If I boot with the mouse plugged in I can unplug and the plug it back in and it works but the usb stick will not work at all.
I looked in my /var/log/dmesg (thanks PWill for the info) and found this on a boot with usb devicces plugged in:

 [   59.506620] ehci_hcd 0000:00:1d.7: fatal error 
 [   59.510497] ehci_hcd 0000:00:1d.7: HC died; cleaning up 
 [   59.510592] usb 4-4: USB disconnect, address 2 
 [   59.510599] p54usb: reset failed! 
 [   59.510613] prism54usb: probe of 4-4:1.0 failed with error -108 
 [   59.511426] usbcore: registered new interface driver prism54usb 
[   62.063112] p54usb: reset failed! 
 [   62.063136] prism54usb: probe of 2-2:1.0 failed with error -110 
 [   62.063197] usb 2-2: device_add(2-2:1.0) --> -110 
 [   62.063256] usb 2-2: USB disconnect, address 2 
 [   62.063366] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device() 
[   62.063398]  [<e0881235>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[   62.063453]  [<e087b611>] usb_disconnect+0x121/0x130 [usbcore]
[   62.063504]  [<e087b664>] hub_pre_reset+0x44/0x70 [usbcore]
[   62.063536]  [<e087c182>] hub_thread+0xc2/0xc20 [usbcore]
[   62.063586]  [<c0178ccf>] __fput+0x10f/0x170
[   62.063626]  [<c013b360>] autoremove_wake_function+0x0/0x50
[   62.063658]  [<e087c0c0>] hub_thread+0x0/0xc20 [usbcore]
[   62.063677]  [<c013b1aa>] kthread+0xba/0xf0
[   62.063688]  [<c013b0f0>] kthread+0x0/0xf0
[   62.063701]  [<c0103e43>] kernel_thread_helper+0x7/0x14


This is an old Dell Dimension 2350 if that matters. Is there a way to reset the usb devices after boot with a command?

Thanks for any help!

---

### Post by elj4176 on 2007-04-10
Nothing?? Am I not asking the right way or in the right forum? 

There must be a command to rescan/activate usb devices after boot.

---

### Post by s5GbJReJ on 2007-04-26
Please help.. I'm having the same issue except it won't work at all.
Right now I'm online with builtin ethernet - wireless would be nice again since it worked in 6.06 LTS.

---

