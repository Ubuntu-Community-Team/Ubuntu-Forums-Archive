---
title: "problem with function keys, webcam"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by dwhite on 2011-04-16
hi,

i have a problem turning my webcam on my laptop on and off, the key combination Fn+F2 should turn it off and on.  My webcam is currently set to come on at startup, when i use the key combination to turn it off, it goes off and everything seems to work fine but i get the following error in the log: 

Apr 16 13:04:11 Lake kernel: [  136.011133] usb 1-7: USB disconnect, address 2
Apr 16 13:04:11 Lake kernel: [  136.013822] atkbd serio0: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
Apr 16 13:04:11 Lake kernel: [  136.013841] atkbd serio0: Use 'setkeycodes e011 <keycode>' to make it known.

and if i try to turn it back on with the key combo, my keyboard freezes and i have to restart my computer.

how can i get the key combination to work, i don't know what the <keycode> should be, i've found a few things searching that suggest it should be '146' and that typing "setkeycodes e011 146" in a terminal should get things working, but i am reluctant to try just anything without knowing if it is correct, is there somewhere i can look up what the keycodes are?

---

### Post by pqwoerituytrueiwoq on 2011-04-16
If it a Dell Latitude/Inspiron i8kutils may help

---

### Post by dwhite on 2011-04-16
> **pqwoerituytrueiwoq said:**
> If it a Dell Latitude/Inspiron i8kutils may help


it is a Zareason Terra HD, i've also got a more complete log i'll paste here, showing point at which the keyboard freezes.

                                 [SIZE=2]**Press Fn+F2 to turn off webcam, this is written to log**[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Apr 16 21:22:35 Lake kernel: [ 7660.116867] usb 1-7: USB disconnect, address 2[/SIZE]
[SIZE=2]Apr 16 21:22:35 Lake kernel: [ 7660.120485] atkbd serio0: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).[/SIZE]
[SIZE=2]Apr 16 21:22:35 Lake kernel: [ 7660.120500] atkbd serio0: Use 'setkeycodes e011 <keycode>' to make it known.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]**Press Fn+F2 to turn on webcam, this is written to log and keyboard freezes**[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Apr 16 21:22:42 Lake kernel: [ 7667.832151] usb 1-7: new high speed USB device using ehci_hcd and address 3[/SIZE]
[SIZE=2]Apr 16 21:22:43 Lake kernel: [ 7667.990110] uvcvideo: Found UVC 1.00 device Venus USB2.0 Camera (0ac8:3420)[/SIZE]
[SIZE=2]Apr 16 21:22:43 Lake kernel: [ 7667.993621] input: Venus USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/input/input8[/SIZE]

---

