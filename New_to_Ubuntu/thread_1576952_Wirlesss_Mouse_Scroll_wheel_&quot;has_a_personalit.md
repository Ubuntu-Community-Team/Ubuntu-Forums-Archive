---
title: "Wirlesss Mouse Scroll wheel &quot;has a personality&quot;."
date: 2010-09-18
forum: New to Ubuntu
---

### Post by suomalainen on 2010-09-18
Ubunteros,

I use a wireless mouse with my laptop that has 10.04LTS.

The scroll wheel hasn't been working properly for weeks now. It kinda just died.....

While a friend was over for a visit, I borrowed his to see if his works on my laptop. And it did!!!!!! 

When I re-attached my mouse, it came back to life too!!!! Cool.... But only seconds later it returned back to the grave... And stopped working...

I don't like this thing acting like a zombie so how big of a cross do I need?

Is there any terminal command that will force the scroll wheel back on and permanently?

The mouse I use doesn't use a bluetooth connector but it's some other like 2.4 Mhz plug.

Thanks!

---

### Post by suomalainen on 2010-09-21
Bump...

---

### Post by jtarin on 2010-09-21
Turn off your mouse for a few seconds and then back on.Then in a terminal issue the command ```
dmesg 
```and post the last 30 or so lines.

---

### Post by suomalainen on 2010-09-21
Does this help jtarin?

[   34.702159] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.718072] type=1505 audit(1285041407.787:10):  operation="profile_load" pid=802 name="/usr/bin/evince-previewer"
[   34.766395] type=1505 audit(1285041407.835:11):  operation="profile_load" pid=802 name="/usr/bin/evince-thumbnailer"
[   34.901192] usb 6-2: new low speed USB device using uhci_hcd and address 2
[   34.977218] fb0: inteldrmfb frame buffer device
[   34.977223] registered panic notifier
[   34.977238] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   34.977315] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   34.977359] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   34.990720] vga16fb: initializing
[   34.990727] vga16fb: mapped to 0xc00a0000
[   34.990735] vga16fb: not registering due to another framebuffer present
[   35.081095] usb 6-2: configuration #1 chosen from 1 choice
[   35.103794] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/0000:03:00.0/usb6/6-2/6-2:1.0/input/input10
[   35.103973] generic-usb 0003:046D:C50E.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:03:00.0-2/input0
[   35.154283] Console: switching to colour frame buffer device 128x48
[   35.228046] ppdev: user-space parallel port driver
[   35.812039] intel8x0_measure_ac97_clock: measured 55305 usecs (2665 samples)
[   35.812046] intel8x0: clocking to 48000
[   45.644026] eth1: no IPv6 routers present
[   65.338158] ISO 9660 Extensions: Microsoft Joliet Level 1
[   65.355415] ISOFS: changing to secondary root
[   77.507221] PPP BSD Compression module registered
[   77.538263] PPP Deflate Compression module registered

---

### Post by suomalainen on 2010-09-21
The command "dmesg" was run both before and after having removed the battery from the mouse and removing it's USB receiver.

After placing the battery and receiver back in place the scroll wheel started to work and dmeg gave results below.

But shouldn't this happen when Laptop is powered off.... What's happening exactly?


[   34.702159] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.718072] type=1505 audit(1285041407.787:10):  operation="profile_load" pid=802 name="/usr/bin/evince-previewer"
[   34.766395] type=1505 audit(1285041407.835:11):  operation="profile_load" pid=802 name="/usr/bin/evince-thumbnailer"
[   34.901192] usb 6-2: new low speed USB device using uhci_hcd and address 2
[   34.977218] fb0: inteldrmfb frame buffer device
[   34.977223] registered panic notifier
[   34.977238] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   34.977315] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   34.977359] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   34.990720] vga16fb: initializing
[   34.990727] vga16fb: mapped to 0xc00a0000
[   34.990735] vga16fb: not registering due to another framebuffer present
[   35.081095] usb 6-2: configuration #1 chosen from 1 choice
[   35.103794] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/0000:03:00.0/usb6/6-2/6-2:1.0/input/input10
[   35.103973] generic-usb 0003:046D:C50E.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:03:00.0-2/input0
[   35.154283] Console: switching to colour frame buffer device 128x48
[   35.228046] ppdev: user-space parallel port driver
[   35.812039] intel8x0_measure_ac97_clock: measured 55305 usecs (2665 samples)
[   35.812046] intel8x0: clocking to 48000
[   45.644026] eth1: no IPv6 routers present
[   65.338158] ISO 9660 Extensions: Microsoft Joliet Level 1
[   65.355415] ISOFS: changing to secondary root
[   77.507221] PPP BSD Compression module registered
[   77.538263] PPP Deflate Compression module registered
[ 4570.808081] usb 6-2: USB disconnect, address 2
[ 4599.780050] usb 6-2: new low speed USB device using uhci_hcd and address 3
[ 4599.955216] usb 6-2: configuration #1 chosen from 1 choice
[ 4599.981683] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/0000:03:00.0/usb6/6-2/6-2:1.0/input/input11
[ 4599.983741] generic-usb 0003:046D:C50E.0004: input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:03:00.0-2/input0

---

### Post by suomalainen on 2010-09-21
Instance # 1

Mouse scroll wheel just died again ! I was looking email in Evolution then went to new desktop to open Firefox and scroll wheel was dead....


Instance # 2
Just took the battery and receiver away again and put back.... This time scrol wheel was dead..

---

### Post by jtarin on 2010-09-21
I think your mouse is bad. Plugging it in after your friends and having it work for a few seconds gave you false hope. Try the mouse on another machine and make certain that it has a good battery. Corded mice are cheap....it would be less headache.

---

### Post by Ripfox on 2010-09-21
I was gonna say, has anyone considered the mouse just died? Hardware fails. Plug it into a windows computer to see if it's Ubuntu...

---

### Post by suomalainen on 2010-09-21
Ripfox, I got a dual boot machine and it appears there too....

I did go online a few days ago and bought 3 SONY USB mice for just $6 from an outfit in Hong Kong. Be interesting to see when they make it to Finland?

Don't understand how my mouse could have died? It hasn't any moving parts. Doesn't eat and never needs any sleep.

---

### Post by duhblow7 on 2010-09-23
I'm having this exact same issue after the recent kernel upgrade over the last week.

[  564.864065] usb 4-2: USB disconnect, address 2
[  570.164021] usb 4-2: new low speed USB device using uhci_hcd and address 3
[  570.397194] usb 4-2: configuration #1 chosen from 1 choice
[  570.414390] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input10
[  570.414484] logitech 0003:046D:C517.0003: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2/input0
[  570.446084] logitech 0003:046D:C517.0004: fixing up Logitech keyboard report descriptor
[  570.446851] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input11
[  570.447005] logitech 0003:046D:C517.0004: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2/input1



after i disconnected and reconnected I was able to scroll down only after the wheel was scrolling for a few seconds.  no up scroll at all.

---

### Post by jtarin on 2010-09-23
> **duhblow7 said:**
> I'm having this exact same issue after the recent kernel upgrade over the last week.

[  564.864065] usb 4-2: USB disconnect, address 2
[  570.164021] usb 4-2: new low speed USB device using uhci_hcd and address 3
[  570.397194] usb 4-2: configuration #1 chosen from 1 choice
[  570.414390] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input10
[  570.414484] logitech 0003:046D:C517.0003: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2/input0
[  570.446084] logitech 0003:046D:C517.0004: fixing up Logitech keyboard report descriptor
[  570.446851] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input11
[  570.447005] logitech 0003:046D:C517.0004: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2/input1



after i disconnected and reconnected I was able to scroll down only after the wheel was scrolling for a few seconds.  no up scroll at all.

I'm gonna say this for the gazillionth time.There is no reason to upgrade your kernel unless your having problems with hardware or software and you know for certain that that particular upgrade will solve the problem. My recommendation to you is to use your old kernel if you still have it and rid yourself of the newer version. Newer is not always better.

---

### Post by suomalainen on 2010-09-25
I agree. It it ain't broken don't fix it!

---

### Post by duhblow7 on 2012-01-23
> **jtarin said:**
> I'm gonna say this for the gazillionth time.There is no reason to upgrade your kernel unless your having problems with hardware or software and you know for certain that that particular upgrade will solve the problem. My recommendation to you is to use your old kernel if you still have it and rid yourself of the newer version. Newer is not always better.

The last time I logged into Ubuntuforums.com was September 23rd, 2010.  It's been almost a year and a half now.  Still on that old *** kernel you recommended.  Still annoyed as **** as my mouse scrolling functionality won't work properly on a new kernel.  Is it common for you to recommend people stick with a kernel for 16+ months for mouse scroll functionality?

---

### Post by pete2bec2 on 2012-03-14
I have a corded mouse and have the same problem with the scroll wheel. Scrolling works on the same laptop if I plug in a different hard drive running other distros. I like Xubuntu best, but the scrolling is bothering me.

If I unplug the mouse it might work for a few seconds. Sometimes it will work for a few seconds if I reverse the scroll direction and then reverse it back again. It works longer when I reverse the scroll, but I don't like it and it only lasts about a minute at the most.

I will try to grab another mouse and see if it improves.

---

### Post by pete2bec2 on 2012-03-16
I replaced the mouse with new identical mouse and the scroll wheel feels different and works, perfectly.

---

