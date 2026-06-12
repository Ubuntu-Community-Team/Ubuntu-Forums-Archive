---
title: "touchpad problem"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by neuthor on 2010-08-20
hi everyone! :D

I'm new to this forum (and also new to Ubuntu). My pc is Asus X64J Laptop. I use Windows 7 (64 bit) + Ubuntu 10.04 (dual boot with Wubi- 64 bit). I really have a problem typing. When I type something, my hand touches to the touchpad, and cursor moves to somewhere else, and i keep on writing, and I end up with something messed up. The worst thing is selecting the text without asking, and when I continue with typing without understanding it,** IT ERASES WHATEVER I HAVE WRITTEN!!!** :evil:

So what I want to do is basically lock my touchpad when my usb connected wireless mouse is connected  my laptop, so I won't be bothered typing. 

What I tried to solve these problems?

1) When I click System> Preferences > Mouse, touchpad tab does not appear, and in the other tabs, nothing related to touchpad.
2) I typed cat /proc/bus/input/devices in Terminal and I found this list:

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus Laptop extra buttons"
P: Phys=asus_laptop/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=rfkill kbd event5 
B: EV=3
B: KEY=10000000000400 0 506c00900000 27801501000 e000000000000 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/LNXVIDEO:01/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b00000000 0 0 0

I: Bus=0003 Vendor=13d3 Product=5122 Version=0202
N: Name="USB2.0 UVC 2M WebCam"
P: Phys=usb-0000:00:1a.0-1.2/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0003 Vendor=046d Product=c51b Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:07:00.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/usb3/3-3/3-3:1.0/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0001 Vendor=10ec Product=0269 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse2 event10 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103
 
As we can see, there is **no synaptics product defined**,** but I can use it **:eek:

3) I searched through net and I found something called **gsynaptics**, which configures your touchpad settings. I installed it but it did not run, instead it said:

> GSynaptics couldn't initialize.

You have to set 'GHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.

4) So I searched through net again and I found the way to edit this file, (it was useful because I learned how to open root account on terminal by **sudo -i**) as following.

[IMG]http://i36.tinypic.com/28b4sjn.png[/IMG]

And it didn't work again!!!

5) I found this website [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543) as someone having a problem as their touchpad is being recognized as something else, so that might be my problem I thought. They suggested some command called tpconfig, and I run it : 
> thor@ubuntu:~$ sudo tpconfig --info
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;        no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.


And now, I get confused, some programs don't found anything, and some do found but does not do anything!!!

I can send you my Xorg.0.log if you want, or anything else you need to solve the problem.

Thanks for helping out.

---

### Post by jtarin on 2010-08-20
[Maybe]("https://help.ubuntu.com/community/SynapticsTouchpad")

[and another]("http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/")

---

### Post by neuthor on 2010-08-20
**@jtarin:**

**1st link you have sent:**

since the touchpad tab does not appear in the Mouse menu, I have done the troubleshooting in the website you have told, and I got the following results:


xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC 2M WebCam                        id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons                   id=14    [slave  keyboard (3)]


as you can see, there is nothing like Synaptics, or ALPS, or Touchpad...

ps. I have also edited SHMConfig by doing 
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

**2nd link you have sent:**
I'm not familiar with UDEV commands, I mean i wrote what the guy did write, but what do I do next, there is no save option and if i close terminal, it says I'll kill the operation.

Thanks for helping though.
Any other ideas?

---

### Post by jtarin on 2010-08-20
Do you have synclient installed as per thos instructions at the bottom? Did you try thr alternate link I gave?

---

### Post by neuthor on 2010-08-20
> **jtarin said:**
> Do you have synclient installed as per thos instructions at the bottom? Did you try thr alternate link I gave?


yes i have installed, and yes i tried that one, the explanation is on the message above. I didn't want to flood the forum with over messaging so i just edited my message.

thor@ubuntu:~$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

From this message, I understand I don't have the driver of it, but since I don't know the product, how I am supposed to find the driver? And I don't think Asus is providing drivers for Linux...

---

### Post by jtarin on 2010-08-20
For the second link try another editor than vim.

```
sudo nano /etc/udev/rules.d/10-local.rules
```the menu for operating nano can be found at the bottom of the editor. Reboot for any effect to take place.

---

### Post by neuthor on 2010-08-20
Sorry for reposting but i found something else, yet, did not work again:

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

as you can see in the website above; in the chapter of 
**Example: Disabling middle-mouse button paste on a scrollwheel mouse**

it tells you about how to disable the middle-mouse button. So I wanted to take the example and apply into the touchpad, so i tried:

thor@ubuntu:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC 2M WebCam                        id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons                   id=14    [slave  keyboard (3)]
thor@ubuntu:~$ xinput get-button-map 13
1 2 3 4 5 
thor@ubuntu:~$ sudo -i
[sudo] password for thor: 
root@ubuntu:~# xinput set-button-map 13 0 0 0 0 0
root@ubuntu:~# xinput get-button-map 13
0 0 0 0 0 


I've rebooted my pc after this, and it didn't work again.

Any help would be appreciated.

---

### Post by neuthor on 2010-08-20
> **jtarin said:**
> For the second link try another editor than vim.

```
sudo nano /etc/udev/rules.d/10-local.rules
```the menu for operating nano can be found at the bottom of the editor. Reboot for any effect to take place.

just a second, trying, might take some time...

---

### Post by neuthor on 2010-08-20
I've written the UDEV rule with nano as you suggested and saved, but when i run 

[COLOR=#000000]#!/bin/bash
synclient TouchpadOff=0 MaxTapTime=0;
syndaemon -i 1 -d[/COLOR]


it says:** Couldn't find synaptics properties. No synaptics driver loaded?**



I'll do a reboot and comeback with the result.


-------------
[SIZE=3][COLOR=Red]**Done a reboot, the same result again...**[/COLOR][/SIZE]

---

### Post by jtarin on 2010-08-20
Google that message... ```
Couldn't find synaptics properties. No synaptics driver loaded?
```looks like its a problem with more than one configuration. Maybe someone with more experience with this problem will help on this post. Try searching also with using the term WUBI along with that.

---

### Post by neuthor on 2010-08-20
i rebooted again, with my external mouse taken off... and asked for xinput list, it still gave me these 2 mouses. (btw my external mouse is a logitech wheel mouse :eek: )

&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]

so i edited these by these commands:

root@ubuntu:~# xinput get-button-map 13
root@ubuntu:~# xinput set-button-map 13 0 0 0 0 0

root@ubuntu:~# xinput get-button-map 12
root@ubuntu:~# xinput set-button-map 12 0 0 0 0 0 0 0

now, my touchpad moves but it does not click(tap) anywhere. I know it is a funny solution, but that works :lolflag:. At least it doesn't block my working anymore...

Thank you jtarin for helping me.

By the way, if anyone had the same (or similar) problem, and reached for a REAL solution, please tell me.


Cheers :biggrin:

---

### Post by jtarin on 2010-08-20
Glad to be of the smallest help. Good you got it working. Now remember what you've done when you decide to install Ubuntu in its own partition.

---

