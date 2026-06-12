---
title: "Aspire one 532h touchpad problems in Lucid Lunx (10.04)"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by sharan.kevryn on 2010-04-30
Installed ubuntu 10.04 netbook remix on my aspire one 532h netbook. My  touch pads vertical scroll doesnt work although i've enabled it in the  mouse preferences. And is there a way to get the multi gesture feature  to work in ubuntu?

---

### Post by busycrab on 2010-05-01
I have this problem on the Acer Aspire One 532h as well.  I fixed it by:

```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

```

You should be able to make it permanent by putting:
```

options psmouse proto=imps

```
in /etc/modprobe.d/options and rebooting

I've only done the first part on my actual machine since I was booted from a flashdrive.  I have Karmic on the laptop now, but I'm installing it.  This was what was holding me up.

---

### Post by sharan.kevryn on 2010-05-01
thanks busycrab ! that fixes it .. but if someone could get the multi gestures working, please tell  me how.

---

### Post by thered on 2010-05-03
I ve been trying to solve this since upgrading my ACER

I can't get it to work - once I run the first line of code my touchpad stops working! So I'm scuppered I can't run the second line. 

It won't paste both lines of code together for some reason. Am I missing something?


Running the second line on its own does nothing -still won't scroll

Edit: /etc/modprobe.d/options doesn't seem to exist.

---

### Post by adietisheim on 2010-05-03
> **thered said:**
> I ve been trying to solve this since upgrading my ACER

I can't get it to work - once I run the first line of code my touchpad stops working! So I'm scuppered I can't run the second line. 

It won't paste both lines of code together for some reason. Am I missing something?



It's pretty normal that the first line stops your touchpad. It unloads the kernel module that handles it. The second line, on the other hand, reloads it with special parameter that tells it to use a special protocol that knows about scroll-wheels. 
Why not just typing things by hand?

> 

Running the second line on its own does nothing -still won't scroll



sure, pretty normal, too. Kernel modules, that are already loaded are not reloaded. You have to unload them and load them again. That's pretty much what those 2 lines do. You have to type both of them.

> 
Edit: /etc/modprobe.d/options doesn't seem to exist.
[/QUOTE]

/etc/modprobe.d/options does not exist any more (does it?). Just use any filename in that directory, that ends with a .conf. 

/etc/modprobe.d/psmouse.conf sounds like a good name to me. And it works for me like a charm. 
Of course, this is only a workaround, it handles the touchpad like a scrollwheel mouse, touchpad specific features are missing. But it already helps a lot! Thanks busycrab! 
I guess we'll have to wait until the new fixed kernel's available to have proper touchpad support.

---

### Post by thered on 2010-05-03
Yes, got it working, thanks to all.

Couldn't type two commands into terminal to test first but created .conf file in /etc/modprobe.d/mouse.conf

It seems a bit jerky but works!!! :D

---

### Post by scotti on 2010-05-04
Upgrading to Kubuntu 10.04 on my DELL XPS 1210 I lost control of the touch-pad
Strange behaviour, I would need two finger on the pad to use it!
Creating the modprobe.d/options file with
                    options psmouse proto=imps
solved the problem. Many thanks.
But if
"Of course, this is only a workaround"!!
please let me know if someone discovers a more straightforward solution.
rs

QUOTE
/etc/modprobe.d/options does not exist any more (does it?). Just use any  filename in that directory, that ends with a .conf. 

/etc/modprobe.d/psmouse.conf sounds like a good name to me. And it works  for me like a charm. 
Of course, this is only a workaround, it handles the touchpad like a  scrollwheel mouse, touchpad specific features are missing. But it  already helps a lot! Thanks busycrab! 
I guess we'll have to wait until the new fixed kernel's available to  have proper touchpad support.
/QUOTE

---

### Post by ragman563 on 2010-05-08
Thanks this worked great... I miss gestures still but this helps things out.
I am running 64bit version not the Netbook version however  (via Wubi right now)... just because I can :) 
I wish there was a 64 bit Netbook edition; it is sweet. 
When I was running the Netbook version I found the touchpad would wig out if I touched it before logging into my account. I had to be careful not to touch it until I was logged it and then it worked fine. The 64bit version did this a bit as well but I think an update may have fixed it. Did this happen to anyone else on a 532H?

---

### Post by Fruitbaby on 2010-05-22
Hi I am also having scrolling issues on a gateway NV 54 series.  

I enter the first two lines of code and i get scrolling capabilities however entering the last code ' options psmouse proto=imps does not make it permanent for me  and  only results in a 'command not found message'. As such, once i reboot i have no scrolling again.

Also im not sure what is meant by "in /etc/modprobe.d/options and rebooting" so maybe this is part of my  problem.

Any help on enlightening me would be great, very very new to this having only just downloaded  and installed Ubuntu today. I have been searching everywhere for a solution and would be nice not to have to be forced back to Windows only.

Fruitbaby

---

### Post by ultravox on 2010-05-25
Thank you. Confirmed scroll working in Compaq 311c with Lucid Lynx.

---

### Post by Viau on 2010-05-26
thanks for this it helped me get the touchpad working properly

---

### Post by manas0185 on 2010-05-26
Works on sony vaio f-series too!! thanks a lot

---

### Post by BozDaBoz on 2010-06-13
Thank you for this solution!  Fixed my Gateway NV53 laptop right up! Using Ubuntu 10.04 with all updates in place and was about to tear out my hair trying to fix touchpad scrolling!

:D

---

### Post by oooh on 2010-06-14
Similar problem here:

VAIO FZ21M
Lucid Lynx

Touchpad would work randomnly (but when it was working, it was working completelly, including scrolling and gestures)

I did the:
```
modprobe -r psmouse
modprobe psmouse proto=imps. 
```

So now **[COLOR="Red"]it works, BUT I have no scrolling or gestures.[/COLOR]**

Synaptics driver is unable to load properly:
```
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
```
From /var/log/Xorg.0.log

The hardware seems to be there according to tpconfig, but not according to dmesg (se below):

**ANY IDEAS ???!?!!?**
```
sudo tpconfig 
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

```
```

cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=abba
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Keys"
P: Phys=
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:27/SNY5001:00/input/input5
U: Uniq=
H: Handlers=rfkill kbd event5 
B: EV=13
B: KEY=1f160f0000 c00000000 10000000000000 200000000 600b00102c00 380000240300400 e000000000000 0
B: MSC=10

I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Jogdial"
P: Phys=
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=40000 0 0 0 0
B: REL=100

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input7
U: Uniq=
H: Handlers=mouse2 event7 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=05ca Product=183b Version=0100
N: Name="UVC Camera (05ca:183b)"
P: Phys=usb-0000:00:1a.7-2/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input8
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic at Ext Left Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event8 
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HP Out at Ext Left Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event9 
B: EV=21
B: SW=4

I: Bus=0006 Vendor=001f Product=001f Version=0000
N: Name="Mouseemu virtual keyboard"
P: Phys=
S: Sysfs=/devices/virtual/input/input11
U: Uniq=
H: Handlers=rfkill kbd event10 
B: EV=100003
B: KEY=1ffffffffffff ffffffffffffffff ffffffffffffffff ffffffffffffffff

I: Bus=0006 Vendor=001f Product=001e Version=0000
N: Name="Mouseemu virtual mouse"
P: Phys=
S: Sysfs=/devices/virtual/input/input12
U: Uniq=
H: Handlers=mouse3 event11 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=044e Product=3013 Version=0111
N: Name="HID 044e:3013"
P: Phys=usb-0000:00:1d.2-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.2/7-1.2:1.0/input/input13
U: Uniq=
H: Handlers=kbd event12 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=044e Product=3012 Version=0111
N: Name="HID 044e:3012"
P: Phys=usb-0000:00:1d.2-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.3/7-1.3:1.0/input/input14
U: Uniq=
H: Handlers=mouse4 event13 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=3
B: MSC=10

```
```

dmesg | egrep -i 'input|touch|track'
[    0.508131] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.508868] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.554847] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.812738] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   32.902411] input: UVC Camera (05ca:183b) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input4
[   32.903165] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:27/SNY5001:00/input/input5
[   32.903235] input: Sony Vaio Jogdial as /devices/virtual/input/input6
[   32.992298] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/input/input7
[   33.239735] input: UVC Camera (05ca:183b) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input8
[   33.250590] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   33.250676] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   39.470372] input: Mouseemu virtual keyboard as /devices/virtual/input/input11
[   39.470542] input: Mouseemu virtual mouse as /devices/virtual/input/input12
[   87.820426] input: HID 044e:3013 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.2/7-1.2:1.0/input/input13
[   87.820532] generic-usb 0003:044E:3013.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 044e:3013] on usb-0000:00:1d.2-1.2/input0
[   87.954563] input: HID 044e:3012 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.3/7-1.3:1.0/input/input14
[   87.954679] generic-usb 0003:044E:3012.0002: input,hidraw1: USB HID v1.11 Mouse [HID 044e:3012] on usb-0000:00:1d.2-1.3/input0

```

---

### Post by limamil on 2010-06-17
it works on my byon, m31w laptop..
thanks a lot!!

---

### Post by oooh on 2010-07-01
Are your Aspire One using a synaptics touchpad driver ?

---

### Post by CompEngStudnt on 2010-07-27
I didn't have this problem after a recent update. But I would like to know if there is yet a way to use a dual gesture feature. I have an Acer Aspire One 532h as well.

---

### Post by NearlyThere on 2010-08-21
Thank you busycrab - I have Acer One ZG5 (cheap netbook - Grandson's cast-off!) which suffer the same touchpad problem. Your work around did the trick!

---

### Post by Josh123 on 2013-04-12
> **busycrab said:**
> I have this problem on the Acer Aspire One 532h as well.  I fixed it by:

```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

```

You should be able to make it permanent by putting:
```

options psmouse proto=imps

```
in /etc/modprobe.d/options and rebooting

I've only done the first part on my actual machine since I was booted from a flashdrive.  I have Karmic on the laptop now, but I'm installing it.  This was what was holding me up.

Worked well for me on Aspire V3-471G. Thanks a lot

---

