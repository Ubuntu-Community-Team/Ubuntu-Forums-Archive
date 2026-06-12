---
title: "Touchpad not recognized [Gnome]"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by zero_linux on 2010-09-25
Hello,

I bought a new Vaio VPCF laptop and installed Ubuntu 10.04.
I had many problems (video, sound,etc) but managed to follow some guides here and get everything working

now i just have one problem. My touchpad doesnt work. :confused:
i found many people with similar problem, but none of the fixes worked for me.

It's not even beign recognized by the system
heres my cat /proc/bus/input/devices output (omitting certain parts):

```

...

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=093a Product=2510 Version=0111
N: Name="PIXART USB OPTICAL MOUSE"
P: Phys=usb-0000:00:1d.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

```my xorg.conf (partial)

```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

```as you can see, no Synaptics or Alps reference :-k

```

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (064e:2100)                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

and finally, not sure if this helps, but

cat Xorg.0.log | grep -i mouse
```

(**) |-->Input Device "Mouse0"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(==) NVIDIA(0): Silken mouse enabled
(II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event4)
(**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
(**) PIXART USB OPTICAL MOUSE: always reports core events
(**) PIXART USB OPTICAL MOUSE: Device: "/dev/input/event4"
(II) PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
(II) PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
(II) PIXART USB OPTICAL MOUSE: Found relative axes
(II) PIXART USB OPTICAL MOUSE: Found x and y relative axes
(II) PIXART USB OPTICAL MOUSE: Configuring as mouse
(**) PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
(**) PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE)
(II) PIXART USB OPTICAL MOUSE: initialized for relative axes.
(II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse1)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse2)
(II) PIXART USB OPTICAL MOUSE: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) PIXART USB OPTICAL MOUSE: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.

```Any help would be greatly appreciated
i really didnt want to have to switch distros because of this :(

---

### Post by zero_linux on 2010-09-25
by the way, i have tried this [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33)

and i get the following error, which is very odd, considering the **sound**

```
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
```

---

### Post by notanumber67890 on 2010-09-27
I have the exact same issue on my Sony Vaio VCPF127FX.  

I think the touchpad is being incorrectly identified as the devices "Virtual core XTEST pointer" and "Macintosh mouse button emulation". 

It seems like xorg.conf needs some custom entries, or maybe some other tweak to help Lucid correctly autodetect the hardware.

Unfortunately my linux-fu is weak and I don't know where to go from here.

Can anyone help??

---

### Post by johnh44 on 2011-10-30
same problem on Toshiba Satellite C655. Any solution yet? I'd be satisfied with even the ability to delay the touchpad sensitity, but the solution in another thread to install mouseemu does not work because the system recognizes the touchpad as a PS2 mouse (not a single-button mouse).

---

### Post by y3kready on 2012-06-30
This solution is available on this [thread]("http://ubuntuforums.org/showthread.php?t=1623030").

Tested working on Sony Vaio Y Series with RHEL Server 6.3

---

