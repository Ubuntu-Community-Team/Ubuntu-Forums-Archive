---
title: "no sound, no secondary display. pls help"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by jonattonyeah on 2009-01-30
greetings y'all

have recently made the switch from the pile of stinking pants that is vista. ubuntu is ace. i really, really love it. the thing is, i dont think my laptop does. indeed, i am currently reinstalling ubuntu right this minute having been trying to sort out two rather annoying problems.

firstly, while i hear the drums when ubuntu first boots up, i cant get any sound after this. secondly, i have a secondary big monitor but ubuntu just wont accept that its plugged into my computer (not a problem when i used vista).

i have been scouring the forum but maybe (i hope) i have missed something. thing is, i think its to do with the nvidia drivers.

my computer spec is as follows:

Hp pavilion dv7 notebook pc
intel core 2 duo cpu t9400 @2.53 ghz
4gb ram
32-bit operating system
display adapters: nvidia geforce 9600m gt
sound video and game controllers: idt high definition audio codec
nvidia hdmi audio (driver version: 1.0.023; driver date 22/3/08 )

going through the nvidea website i cant see any linux drivers for the geforce 9600m. the restricted driver offered to me by ubuntu (i'm using 8.04) doesnt help when i enable it - the second monitor still not recognised when i go to screen resolution. and when i try testing my sound, noise does come out but it all goes mental and the computer crashes (amid a racket akin to a drum n bass percussionist freaking out on crack).

if you can, please help. is my laptop useless or is it just me? i really hope its the latter. can some code help or should i just grab a hammer and vent my spleen?

hope all that makes sense.

cheers

jonattonyeah?

---

### Post by halovivek on 2009-01-30
Can you post this output?
please type this in terminal and post the output

lspci

---

### Post by jonattonyeah on 2009-01-30
thanks for the reply! here it is...

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0649 (rev a1)
02:00.0 Network controller: Intel Corporation Unknown device 4237
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
06:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

---

