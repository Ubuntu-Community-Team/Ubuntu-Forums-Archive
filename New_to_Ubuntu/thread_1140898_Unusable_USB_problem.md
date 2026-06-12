---
title: "Unusable USB problem"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by icyest on 2009-04-28
So my machine refuses to recognize my LG 720 Shine cell phone when it's in USB Mass Storage mode. I don't know whats wrong. All I know is that there's just suppose to be an icon on my desktop that I can click on to access the files on my phone like every other usb mass storage device. It's just not there.



Oh, and before you say anything about my hardware or if you're just wondering: it worked perfectly with 8.10.

More info: 
Machine=Dell Latitude|D620


PS:
So as expected, each new release of ubuntu is bound to have as many problems as a windows machine (I don't just mean that as a joke). I've been around the beginner's forums for quite some time and I'd like to ask why is it so cumbersome to maintain a Linux machine? Even if it's Ubuntu? Why is Ubuntu just so hard to maintain? Isn't it not suppose to have this many simple problems? I don't even do anything complex with my OS.

---

### Post by cariboo on 2009-04-28
Could you open an Applications-->Accessories-->Termianl and type:

```
dmesg | tail -n15
```

when you plug your phone in and paste the output in your next post.

The reason you may run into problems when upgrading, is that there are so many different hardware configurations, that it is hard to test every on every different platform. 

Personally I have installed Jaunty on two different computers, and every thing just worked.

---

### Post by icyest on 2009-05-12
Sorry for the late reply, but I'm a really busy student.

```
t@t:~$ dmesg | tail -n15
[  399.550166] usb 3-2.3: new low speed USB device using uhci_hcd and address 4
[  399.551306] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.1/3-2.1:1.1/input/input9
[  399.557197] generic-usb 0003:413C:2010.0002: input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2.1/input1
[  399.557235] usbcore: registered new interface driver usbhid
[  399.557242] usbhid: v2.6:USB HID core driver
[  399.730291] usb 3-2.3: configuration #1 chosen from 1 choice
[  399.746956] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.3/3-2.3:1.0/input/input10
[  399.772116] generic-usb 0003:046D:C00E.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2.3/input0
[ 2321.553552] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 3742.600066] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 3742.761248] usb 4-1: configuration #1 chosen from 1 choice
[ 3742.839373] Initializing USB Mass Storage driver...
[ 3742.843178] usb-storage: probe of 4-1:1.0 failed with error -5
[ 3742.843226] usbcore: registered new interface driver usb-storage
[ 3742.843233] USB Mass Storage support registered.

```

Can anyone help?

---

### Post by tjwilli on 2009-10-20
I have the same problem. Did you ever get it resolved? There is another thread that talks about this, but it didn't seem to help me.

[http://ubuntuforums.org/showthread.php?t=1145846](http://ubuntuforums.org/showthread.php?t=1145846)

---

