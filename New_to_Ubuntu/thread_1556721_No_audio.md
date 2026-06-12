---
title: "No audio"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by ltnemo2000 on 2010-08-19
I know this is a fairly common problem for ubuntu 10.04 on a laptop but I can't seem to find a solution that I can understand. I have next to no experience with unix and the only solutions I can find assume I know how to code. the sound cards are recognized under sound preferences>hardware
Thanks

---

### Post by corrytonapple on 2010-08-19
Sir/Mam, can you be more specific with your issue? Does the sound not work system wide or in Firefox? Is your sound card in a extra slot or built in to the computer? What are your system specs?
Thank you.

---

### Post by ltnemo2000 on 2010-08-19
no sound system wide. integrated radeon sound card in a sony vaio E series. brand new.

---

### Post by corrytonapple on 2010-08-19
Install hardware drivers. See this:
[http://ubuntuforums.org/showpost.php?p=9724443&postcount=2](http://ubuntuforums.org/showpost.php?p=9724443&postcount=2)
It is the same thing except you are looking for video drivers.

---

### Post by ltnemo2000 on 2010-08-21
I don't have windows anymore.
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ dmesg | grep HDA
 [   10.669593] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 [   10.669633] HDA Intel 0000:00:14.2: setting latency timer to 64
 [   10.757279] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input10
 [   10.799836] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
 [   10.799856] HDA Intel 0000:01:05.1: setting latency timer to 64

tried without success:
sudo apt-get purge pulseaudio && sudo apt-get install pulseaudio

---

### Post by corrytonapple on 2010-08-21
Sorry, forget that first line about Windows. They were trying to get Internet and I was unsure if it worked in windows or not.

---

### Post by ltnemo2000 on 2010-08-21
one more thing...
```
~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Sony Corporation Device 9602
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f4100000-f42fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00006000-00009fff
    Memory behind bridge: f3100000-f40fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: f3000000-f30fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 28
    I/O ports at b038 [size=8]
    I/O ports at b04c [size=4]
    I/O ports at b030 [size=8]
    I/O ports at b048 [size=4]
    I/O ports at b010 [size=16]
    Memory at f4308000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4307000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4308600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4306000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4308500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Subsystem: Sony Corporation Device 9077
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at b000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f4300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4305000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=10, sec-latency=0
    I/O behind bridge: 00002000-00005fff
    Memory behind bridge: f2000000-f2ffffff
    Prefetchable memory behind bridge: 00000000f1000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4304000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4308400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at a000 [size=256]
    Memory at f4200000 (32-bit, non-prefetchable) [size=64K]
    Memory at f4100000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at 6000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e017
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f3000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k
```

---

### Post by corrytonapple on 2010-08-21
Hardware drivers should work since now it's trying to use intel drvers. If you post code output, please post it between ```

```

---

### Post by ltnemo2000 on 2010-08-22
so i need a driver for a radeon hd 4200...
where can I find one that works for ubuntu?
I didn't see one on the ATI website

---

### Post by corrytonapple on 2010-08-22
At the top of the screen, go to **System>Administration>Hardware Drivers**  and download and install any drivers for your sound card. See picture (I have no drivers  to install)

---

### Post by ltnemo2000 on 2010-08-22
installed drivers
still no sound
lspci -v
```
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```
 no change

---

### Post by corrytonapple on 2010-08-22
Has this worked in Windows (If you have it)? Have you tried restarting after driver install? Try listening out of headphones or another pair of speakers.

---

### Post by ltnemo2000 on 2010-08-22
I did reboot and still have no sound from built in speakers or elsewhere. I also do not have windows although when I did there was perfect sound.

---

### Post by corrytonapple on 2010-08-22
OK that makes it so all hardware is fine. Run this for me: it will show all connected devices.
```

lspci

```

---

### Post by ltnemo2000 on 2010-08-22
~$  lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Sony Corporation Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

---

### Post by jmfal on 2010-08-23
Welcome to ubuntu

Getting a good hands-on w/the terminal, good, excellent.

what are you using to play sound/music???

You stated that your hardware is recognized, but what do you have it set at???

open sound preferences>hardware, in the settings  for selected box click dropdown box

and select analog stereo or analog stereo duplex

you only need digital output if you are using  hdmi or toslink cable, if you are trying to use usb speakers unplug them and we will get your sound working first

open a terminal and enter 

     ```
 alsamixer
```
make sure l/r  volume ,pcm are at least 75-90%

use l/r arrows on keypad to change selections, up/down arrows to raise/lower input/output, mute mike,and line input if you have them, play some music

post back, will be here for awhile

---

### Post by ltnemo2000 on 2010-08-23
I have tried using Firefox movie player and rhythm box and none of them work. I also get no sound when I first boot and log in. 
attached are screen shots of my alsamixer and sound preferences

---

### Post by jmfal on 2010-08-23
Everthing in the screenshot seems to be good

In alsamixer when you press f6-select sound card, are there more than one option?

try this: system>administration>users and groups>manage groups>audio>preferences and make sure there is a check in the box in front of your username.

do that for pulse and pulse-access.

Have sound?  If not there is a thread in the multimedia/video section by markbuntu
>hda-snd options database< take a look at that as you might have to edit some files,
there is too much for me to try and explain.

good luck

---

### Post by ltnemo2000 on 2010-08-26
no luck with giving myself permission to use audio although the box was not checked.
I think I made some headway into what is causing this problem.
my audio device is listed as:

```
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```
as far as I can tell this is a video card.
while when I input lspci I found:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
```
which sounds more like an audio device.
tell me if I'm wrong.
I'm here to learn.

---

### Post by corrytonapple on 2010-08-26
> **ltnemo2000 said:**
> no luck with giving myself permission to use audio although the box was not checked.
I think I made some headway into what is causing this problem.
my audio device is listed as:

```
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Sony Corporation Device 9077
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```as far as I can tell this is a video card.
while when I input lspci I found:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
```which sounds more like an audio device.
tell me if I'm wrong.
I'm here to learn.
Well, it says it is the audio device. Now, the drivers must not be installing. Look:
```
00:14.2 Audio device: **ATI Technologies** Inc SBx00 Azalia (**Intel HDA**) (rev 40)
```
Intel drivers with ATI sound? Maybe. ATI does not make sound cards that I knew. Maybe a Intel sound card with ATi drivers? Have you restarted recently? Make sure the drivers are installed.

---

### Post by ltnemo2000 on 2010-08-29
i have restarted several times since installing the drivers.
is looks like there was an available video driver but not a sound driver to be installed (see screenshot)

---

### Post by corrytonapple on 2010-08-29
It is already being used. Do they work in the Live CD? Do you have a way of testing the sound with Windows? I think you should try Debian on a live CD. Also, you CD or USB stick could be corrupted so try another CD or stick and reinstall again.

---

### Post by ltnemo2000 on 2010-08-29
no. I have no way of testing windows. it always worked before windows crashed but never worked in ubuntu. I have installed from 2 different cds and never had sound. might try debian later when i get home again.

---

### Post by corrytonapple on 2010-08-30
I do not know what to say. It seems like I have had you try everything I know. I do not want to lead you away from Ubuntu, because it is a great distro and the Administers might throw me out. :lolflag: Debian comes out with its releases when they are ready to. The hardware support is great. Try it and I think you will like it. Oh yeah, and congratulations on "Spilling the Beans". You now have Ubuntu coffee beans all over your floor that you might slip on. Don't run them over with the Office Chair!

---

