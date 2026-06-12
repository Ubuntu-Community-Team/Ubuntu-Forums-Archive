---
title: "Logitech Wireless Keyboard/Mouse"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by hearnden on 2006-09-13
Hi,

I've got a Logitech wireless keyboard and mouse (Cordless MX Duo, bluetooth), and whenever I boot into Ubuntu, neither the keyboard nor the mouse work.  They work fine in the BIOS and GRUB menus, and appear to work all the way through the boot process until X starts.   However when the X login screen comes up, nothing works.  There's a bright blue "Connect" button on the wireless hub that the mouse and keyboard talk to, and pressing that usually makes it flash while the hub tries to find the keyboard and mouse.  But when the X login screen comes up, pressing the big blue button does nothing - the hub is frozen.

The hub is connected to the computer with a USB and keyboard PS/2 plug, and if I unplug the USB and replug it, then after a few seconds things usually work fine.  Sometimes I have to unplug and replug a few times, but it never works first time from boot.

Has anyone else had this experience, or does anyone have any ideas about what could cause this behaviour?

P.S. I suspect that this is an X configuration issue, but I've tried just about every combination of options I could think of.

---

### Post by hearnden on 2006-09-16
Some updated info in case anyone else is experiencing a similar problem.  The keyboard certainly works fine until X starts.  So it's something to do with X.  However it is only the first time X starts.  Once the unplug-replug dance has got them working, then they work fine if X is restarted (Ctrl-Alt-Backspace).

Xorg.0.log:
```

(**) Logitech Elite Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Logitech Elite Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Logitech Elite Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "logiinkseusb"
(**) Logitech Elite Keyboard: XkbModel: "logiinkseusb"
(**) Option "XkbLayout" "us"
(**) Logitech Elite Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Logitech Elite Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Logitech MX900 Mouse: Device: "/dev/input/mice"
(**) Logitech MX900 Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Logitech MX900 Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Logitech MX900 Mouse: ZAxisMapping: buttons 4 and 5
(**) Logitech MX900 Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Logitech MX900 Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Logitech Elite Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Logitech MX900 Mouse: ps2EnableDataReporting: succeeded

```

One idea might be something to do with the USB input device numbers.  Initially, these devices are given input numbers starting from 1 (/class/input/input1):

```

Sep 16 16:47:48 localhost kernel: [17179588.004000] input: Logitech USB Receiver as /class/input/input1
Sep 16 16:47:48 localhost kernel: [17179588.004000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.1
Sep 16 16:47:48 localhost kernel: [17179588.024000] Floppy drive(s): fd0 is 1.44M
Sep 16 16:47:48 localhost kernel: [17179588.036000] input: PC Speaker as /class/input/input2
Sep 16 16:47:48 localhost kernel: [17179588.040000] input: Logitech USB Receiver as /class/input/input3
Sep 16 16:47:48 localhost kernel: [17179588.040000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.1

```

And they work fine until X starts.  Once X starts, it kills the keyboard/mouse.  When the devices are replugged, they get higher numbers, like /class/input/input4:

```

Sep 16 16:48:15 localhost kernel: [17179721.988000] usb 1-2: new full speed USB device using uhci_hcd and address 7
Sep 16 16:48:15 localhost kernel: [17179722.128000] hub 1-2:1.0: USB hub found
Sep 16 16:48:15 localhost kernel: [17179722.132000] hub 1-2:1.0: 2 ports detected
Sep 16 16:48:15 localhost kernel: [17179722.452000] usb 1-2.1: new low speed USB device using uhci_hcd and address 8
Sep 16 16:48:15 localhost kernel: [17179722.624000] input: Logitech USB Receiver as /class/input/input4
Sep 16 16:48:15 localhost kernel: [17179722.624000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2.1
Sep 16 16:48:15 localhost kernel: [17179722.660000] input: Logitech USB Receiver as /class/input/input5
Sep 16 16:48:15 localhost kernel: [17179722.660000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2.1
Sep 16 16:48:16 localhost kernel: [17179722.864000] usb 1-2.2: new full speed USB device using uhci_hcd and address 9
Sep 16 16:48:16 localhost hcid[4903]: HCI dev 0 registered
Sep 16 16:48:16 localhost hcid[4903]: HCI dev 0 up

```

and then thinks work fine again.

So why does X barf with the initial numbers?

---

### Post by hearnden on 2006-09-16
Further testing results:  it's something to do with the mouse.  If the computer is started with the hub's keyboard PS/2 connector connected, but without the USB connector, then the keyboard works fine in X.

---

### Post by acegolfer on 2006-12-07
hearnden,

Have you fixed the problem? I'm considering Logitech Elite Duo (wireless usb, no bluetooth). I hope it works in my system.

---

### Post by mortenkri on 2006-12-07
I'm experiencing the same problem with my diNivo keyboard and mx900 mouse.

---

### Post by wieman01 on 2006-12-09
I had a Logitech Cordless Duo. HAD... I replaced it because my mouse kind of malfunctioned. Not sure if it had to do with a hardware failure, but a couple of minutes after booting my computer, my mouse would start going crazy & behaving very erratically. So I gave up on it.

But these are 2 guides, perhaps they help. I would avoid Logitech Cordless Duo though:

[http://www.ubuntuforums.org/showthread.php?t=191107&highlight=mx700]("http://www.ubuntuforums.org/showthread.php?t=191107&highlight=mx700")
[http://www.ubuntuforums.org/showthread.php?t=188302]("http://www.ubuntuforums.org/showthread.php?t=188302")

---

### Post by hearnden on 2007-01-25
I 'fixed' the problem by ditching the wireless mouse and just using a wired mouse.  Wireless keyboard works fine though.

---

### Post by baarney on 2007-01-27
I had a similar problem with a cordless elite duo. I think it dies when the bluez-utils package loads. Certainly for my system I 'fixed' the problem by renaming the /etc/init.d/bluez-utils package, so that it never gets called from the startup scripts. This probably doesn't help if you want to use the hub for other bluetooth devices.

---

