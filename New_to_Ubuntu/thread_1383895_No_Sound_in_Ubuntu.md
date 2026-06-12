---
title: "No Sound in Ubuntu"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Phantomhive on 2010-01-17
I know this has already been posted probably, but most of the threads/sites I've seen are too advanced for me. I'm a darn noob, hehe.

But yeah. There is no sound and I'm wondering if there is an easy way to fix the issue. I don't get sound either from external speakers or my laptop's speakers. Just say what you need me to post for specifics and I will.

(Currently writing this on Windows 7, actually)

---

### Post by Rayve on 2010-01-17
Have you tried ensuring your sound is not muted?  Click on the volume icon at the top panel, but also go into System > Preferences > Sound and ensure everything is set there (all of the devices have the speakers/headset/whatever you're using for sound, selected from the drop-down menu).

It's an easy one to overlook.  :)  If it's more involved than that, let us know, and we'll do some more looking.

---

### Post by Phantomhive on 2010-01-17
> **Rayve said:**
> Have you tried ensuring your sound is not muted?  Click on the volume icon at the top panel, but also go into System > Preferences > Sound and ensure everything is set there (all of the devices have the speakers/headset/whatever you're using for sound, selected from the drop-down menu).

It's an easy one to overlook.  :)  If it's more involved than that, let us know, and we'll do some more looking.

I may be nooby, but not that nooby. xD

Yeah, it's all un-muted.

---

### Post by Rayve on 2010-01-17
The comprehensive guide here is pretty good to start troubleshooting: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)  Apologies if you've seen it already.  Taken from that guide, to ensure your sound card is detected, post the output of:

```
 aplay -l 
```and ```
 lspci -v 
```If there's a part you don't understand or if something doesn't work right, post back and the good folks here can help you through.  :)  

I'm off to work, but will check this thread again in the morning.  Hopefully you're up and running successfully by then!

---

### Post by Phantomhive on 2010-01-17
From the first one: **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mike@ubuntu:~$ 



From the second one: 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: f2200000-f23fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00006fff
    Memory behind bridge: f1200000-f21fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: f1100000-f11fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f2500000-f25fffff
    Prefetchable memory behind bridge: 00000000f1000000-00000000f10fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8038 [size=8]
    I/O ports at 804c [size=4]
    I/O ports at 8030 [size=8]
    I/O ports at 8048 [size=4]
    I/O ports at 8010 [size=16]
    Memory at f2408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f2407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f2406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f2408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f2405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f2404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f2408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f2400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=64

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

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=256]
    Memory at f2300000 (32-bit, non-prefetchable) [size=64K]
    Memory at f2200000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel modules: radeon

01:05.1 Audio device: ATI Technologies Inc Device 970f
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f2310000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 303f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3635
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at 2000 [size=256]
    Memory at f1010000 (64-bit, prefetchable) [size=4K]
    Memory at f1000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at f1020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

mike@ubuntu:~$

---

### Post by garvinrick4 on 2010-01-17
> **Phantomhive said:**
> I know this has already been posted probably, but most of the threads/sites I've seen are too advanced for me. I'm a darn noob, hehe.

But yeah. There is no sound and I'm wondering if there is an easy way to fix the issue. I don't get sound either from external speakers or my laptop's speakers. Just say what you need me to post for specifics and I will.

(Currently writing this on Windows 7, actually)

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Have to reboot when done.

Worked for me on three installs of 9.10 with Intel sound.
Go to Synaptic  package manager and install Alsa backports for your kernel
if you have to.

---

### Post by Phantomhive on 2010-01-17
> **garvinrick4 said:**
> [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Have to reboot when done.

Worked for me on three installs of 9.10 with Intel sound.
Go to Synaptic  package manager and install Alsa backports for your kernel
if you have to.

Before I do that I'd like to know how install ALSA?

I download the alsa-driver-1.0.22.1.tar.bz2 from the website but it saves as a folder of stuff, where as I am just so used to clicking an .exe ******* I feel like a noob here LOL. I will learn eventually...

---

### Post by Rayve on 2010-01-18
When you get a "folder of stuff" and it ends in something like "tar.bz2" (or just "tar"), that means it's compressed, much like ".zip" which should be more familiar to you.

To extract (I've also heard it called "unpack") the files, head on over to the command line and enter:

```
tar xjvf alsa-driver-1.0.22.1.tar.bz2
```This should be done while in the same directory as wherever you downloaded the file - so directly from the command prompt if you have it in your home directory, or cd as needed and then enter the command.

What you're telling the "tar" program is -

x = extract
j = bz2 format
v = verbose
f = file

See here for more information (read: this is where I copied/pasted from): [http://ubuntuforums.org/showthread.php?t=656836](http://ubuntuforums.org/showthread.php?t=656836)

---

### Post by Phantomhive on 2010-01-18
> **Rayve said:**
> When you get a "folder of stuff" and it ends in something like "tar.bz2" (or just "tar"), that means it's compressed, much like ".zip" which should be more familiar to you.

To extract (I've also heard it called "unpack") the files, head on over to the command line and enter:

```
tar xjvf alsa-driver-1.0.22.1.tar.bz2
```This should be done while in the same directory as wherever you downloaded the file - so directly from the command prompt if you have it in your home directory, or cd as needed and then enter the command.

What you're telling the "tar" program is -

x = extract
j = bz2 format
v = verbose
f = file

See here for more information (read: this is where I copied/pasted from): [http://ubuntuforums.org/showthread.php?t=656836](http://ubuntuforums.org/showthread.php?t=656836)

Gah. I feel so dumb ROFL.

I have the alsa-driver-1.022.1.tar.bz2 on my desktop. When I go to the terminal and enter what you said, tar: alsa-driver-1.0.22.1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

---

### Post by alpha-buntu on 2010-01-18
installed alsa-mixer?

are all channels on 100 percent?

---

### Post by Rayve on 2010-01-25
PhantomHive,

Sorry for the delay, maybe you've got this up and running now, but I wanted to reply to your tar question.  If you are just opening the terminal the first time, you're likely in your /home/<username> directory.  The file will be on your desktop, which is at /home/<username>/Desktop.  Try the following:

```

cd /home/<yourusernamehere>/Desktop
tar xjvf  alsa-driver-1.022.1.tar.bz2

```

See if that doesn't solve the error.

---

### Post by Phantomhive on 2010-01-27
> **Rayve said:**
> PhantomHive,

Sorry for the delay, maybe you've got this up and running now, but I wanted to reply to your tar question.  If you are just opening the terminal the first time, you're likely in your /home/<username> directory.  The file will be on your desktop, which is at /home/<username>/Desktop.  Try the following:

```

cd /home/<yourusernamehere>/Desktop
tar xjvf  alsa-driver-1.022.1.tar.bz2

```See if that doesn't solve the error.

Sorry, it may be an obvious thing but I get an error.

> cd /home/<mike>/Desktoptar xjvf  alsa-driver-1.022.1.tar.bz2

Even though it is on the desktop 

> bash: mike: No such file or directory

---

### Post by head2head on 2010-01-27
You don't need the <  >' in the command;

```
cd /home/yourusernamehere/Desktop
tar xjvf  alsa-driver-1.022.1.tar.bz2
```

At least I think you don't..I'm still learning too!

---

