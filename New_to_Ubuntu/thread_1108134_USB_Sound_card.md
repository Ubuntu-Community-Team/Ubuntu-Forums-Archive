---
title: "USB Sound card"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by mistaPJ on 2009-03-27
I have problems specifying to my system that I want it to use an external sound card. The original internal card doesn't work for very long after the computer boots. A friend of mine managed to get ubuntu 7.10 to work with the external sound card but since I have updated to ubuntu 8.4 some programs have reverted back to trying to use the internal card.

I have the external card connected to external speakers and the internal card is still connected to the internal speakers. 

When I try to play a file (film or music) it uses the internal defective card so most of the time it doesn't work. However, flash applications use the external card. I have a Dell inspiron 6000 and have tried to use BIOS to disbale the sound card but it wont let me.

Here is some info...

aplay -l

gives me

```
**** List of PLAYBACK Hardware Devices ****
card 0: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I don't like the fact that Audio (external) and ICH6 (internal) both have the same device numbers, but I dont know how to change that

aplay -L

gives me 

```

default:CARD=Audio
    USB Audio, USB Audio
    Default Audio Device
front:CARD=Audio,DEV=0
    USB Audio, USB Audio
    Front speakers
surround40:CARD=Audio,DEV=0
    USB Audio, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audio,DEV=0
    USB Audio, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audio,DEV=0
    USB Audio, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audio,DEV=0
    USB Audio, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audio,DEV=0
    USB Audio, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audio,DEV=0
    USB Audio, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=ICH6
    Intel ICH6, Intel ICH6
    Default Audio Device
front:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    Front speakers
surround40:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers

```

lspci -v

gives me

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Unknown device 0188
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 0188
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec38 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Unknown device 0188
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	Memory behind bridge: dfd00000-dfdfffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Inspiron 6000 laptop
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ed00 [size=256]
	I/O ports at ec40 [size=64]
	Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
	Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Conexant Unknown device 5423
	Flags: medium devsel, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at ec80 [size=128]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Unknown device 0188
	Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 0188
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Dell Unknown device 0188
	Flags: medium devsel, IRQ 10
	I/O ports at 10c0 [size=32]

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Inspiron 6000 laptop
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at dfdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: Dell Inspiron 6000 laptop
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at dfd00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 34000000-37fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001

03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
	Subsystem: Dell Inspiron 6000 laptop
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at dfdfc800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) (prog-if 01)
	Subsystem: Dell Inspiron 6000 laptop
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dfdfc700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 1021
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```

I tried removing ALSA and installing it from fresh.

I tried this

> 1. open a terminal
2. install the package by typing : sudo apt-get install asoundconf-gtk
3. start the app by typing : asoundconf-gtk
4. select your default soundcard from the drop down menu
5. quit the app and close the terminal window
6. reboot a couple of times and test. But it should work fine like this.

less /proc/asound/modules

gives me

```
 0 snd_usb_audio
 1 snd_intel8x0
```

I tried blackslisting snd_intel8x0.

Also originally I could control the volume using a single click on the speaker icon in the bottom right, now it doesn't work. However, the volume buttons on the laptop didn't work before but they do now.

I would really appreciate some help, but remember I am new to this so if you tell me to do something the chances are I wont know how, I need to see the commands that I should use, cheers.

---

### Post by Nero147 on 2009-03-27
I used to have a similar problem. What worked for me was 
asoundconf list
This lists all of the names of the active cards, then 
asoundconf set-default-card name_of_card
Where name_of_card is the name listed in the list.
Also you might try changing your default mixer from pulse-audio in sound preferences. I've never had anything but problems with pulse audio on multi soundcard systems.

---

### Post by mistaPJ on 2009-03-27
Thanks for the speedy answer, I think I tried that one earlier too, I just tried it again anyway, no luck.

I should also say that

sudo nano /etc/modprobe.d/alsa-base

gives me

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd$
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --q$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe$
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --q$
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modp$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq$
# Prevent abnormal drivers from grabbing index 0
options snd-usb-audio index=-1
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-3
options bt87x index=-4
options cx88_alsa index=-5
options saa7134-alsa index=-6
options snd-atiixp-modem index=-7
options snd-intel8x0m index=-8
options snd-via82xx-modem index=0
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

```

I played with the index values a bit, nothing seems to change though.

I'll have a look at changing the setting you mention too, cheers.

---

### Post by maddog39 on 2009-03-27
Yea I use a HeadRoom Total Bithead headphone amplifier and DAC and have the same issue. Basically I just went into my alsa config file and changed the default card to 1 (in your case 0) and the default PCM to 1 (in your case 0) and that solved my problem completely. Although I am forced to use my headphones all the time as its not easy to switch back to intel HDA at my leisure like I would like.

---

### Post by mistaPJ on 2009-03-28
Ok that sounds like a good plan, the only problem is that I don't know how to do it. I tried following so many suggestions from other threads yesterday that I really don't know exactly what I've done and what I haven't. I'm really a learner when it comes to all this stuff, it's difficult to take in so many new commands and try to come to terms with the internal workings of a computer, but I do enjoy it so I'll keep going.

Could anybody help explain how I open the ALSA config file? Cheers.

---

### Post by mistaPJ on 2009-03-28
I'm starting to think that I should change the device numbers since 

aplay -l 

shows that both devices are numbered 0. How would I go about doing that? Surely this could be leading to the complication? I've had a little look and haven't found any way to do it yet, cheers.

---

### Post by mistaPJ on 2009-03-29
This was the thread which solved my problem

[http://ubuntuforums.org/archive/index.php/t-402293.html](http://ubuntuforums.org/archive/index.php/t-402293.html)

---

### Post by mistaPJ on 2009-06-10
Hello again, I have a new problem now, I get sound when I use a flash player or the like from the internet, however, when I try to use Totem or VLC media players I get nothing. 

Does anybody have any ideas what I could do to solve this?

Cheers

---

