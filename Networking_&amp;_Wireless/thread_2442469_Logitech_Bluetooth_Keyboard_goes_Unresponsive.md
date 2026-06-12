---
title: "Logitech Bluetooth Keyboard goes Unresponsive"
date: 2020-05-04
forum: Networking &amp; Wireless
---

### Post by lng-babie on 2020-05-04
Hi
  I am using Logitech K350 Bluetooth keyboard and M235 Bluetooth mouse using single Unity dongle, received with the Mouse. I Paired the Keyboard to this dongle using a windows machine one year back. Recently I started facing issues with the Keyboard that it goes unresponsive after some time. Even if the keyboard was in use, it will not respond to all the keys. But some of the key combinations such as, ctrl + alt + F1 could work and in the virtual console, My keyboard could work normal. Usually Once I switch back to the X server environment (ctrl + alt + F7) Keyboard will function again.
I am running Ubuntu 16.04 with gnome fallback. 

```
Linux 4.15.0-29-generic #31~16.04.1-Ubuntu SMP Wed Jul 18 08:54:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

Weird thing is, The default keyboard of my laptop also goes unresponsive at this state - unless the dongle is removed. Also the mouse (Bluetooth mouse and touchpad) can navigate but clicks wouldn't work. The *dmesg* after the error recovery is as follows.
```
[   96.024376] logitech-hidpp-device 0003:046D:4055.0004: HID++ 4.5 device connected.
[  116.689151] logitech-djreceiver 0003:046D:C52B.0008: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-1/input2
[  116.902528] input: Logitech Wireless Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.2/0003:046D:C52B.0008/0003:046D:4055.0009/input/input18
[  116.902853] logitech-hidpp-device 0003:046D:4055.0009: input,hidraw2: USB HID v1.11 Mouse [Logitech Wireless Mouse] on usb-0000:00:14.0-1:1
[  122.844170] input: Logitech K350 as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.2/0003:046D:C52B.0008/0003:046D:200A.000A/input/input19
[  122.844396] logitech-hidpp-device 0003:046D:200A.000A: input,hidraw0: USB HID v1.11 Keyboard [Logitech K350] on usb-0000:00:14.0-1:2
[  484.042460] logitech-hidpp-device 0003:046D:200A.000A: HID++ 3.0 device connected.
[  484.050484] logitech-hidpp-device 0003:046D:200A.000A: unable to retrieve the name of the device
[ 3026.694686] perf: interrupt took too long (2528 > 2500), lowering kernel.perf_event_max_sample_rate to 79000
[ 3743.215589] perf: interrupt took too long (3175 > 3160), lowering kernel.perf_event_max_sample_rate to 63000
[ 5520.019167] perf: interrupt took too long (4000 > 3968), lowering kernel.perf_event_max_sample_rate to 50000
[ 5823.634539] atkbd serio0: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 5823.634546] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[ 5823.644915] atkbd serio0: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[ 5823.644920] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
```

One possible issue was any particular Key on the external keyboard remaining pressed. But As I try 
```
xinput test-xi2 --root
```

No continuous key-press is observed with this. Also, I have installed new batteries in the keyboard to avoid issues due to lack of power. Please help me to identify the root cause and how to get this resolved.

*- Thanks*

---

### Post by akash172 on 2020-05-16
I have a similar problem

Raspberry Pi 4b, Logitech Keyboard, mouse combo... Ubuntu 19

If I wait hours to login, no problem.

If I login and immediately start using programs for  as long as I want, no problem. 

When I stop using the mouse or keyboard  for 5 to 10 mins they no longer work. The cursor will move around the  screen but clicks do nothing and the keyboard doesn't work either. That ctrl+alt+f7 does nothing.

I have to power cycle to get back in. System power sleep mode is set to  never. Display Power management is turned off. Under Security Light  locker Automatically lock the session is set to never and lock the  screen when system is going to sleep is unchecked.

All seems updated ... though I have yet to find where the version of the OS is hidden.

The only things Ive changed are adding qbittorrent, VLC, Firefox and the  power settings (after the problem showed itself). Oh and changed the  desktop wall paper. 

Some one must have some idea!

Thanks

---

### Post by lng-babie on 2020-05-29
can you share the dmesg kernel logs. Lets see if its similar behaviour to that of mine. 
For the last couple of weeks, I switched to Unity and and so far havent observed the behaviour. Will update if I obsereve it again.

*- Thanks*

---

