---
title: "Help! Configuration Problems!"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Mickey_079 on 2009-02-07
Hey. 

Well my name is Michael and I'm new to Ubuntu, so I have pretty much no idea when it comes to it.

So I installed my graphics driver but keep getting an error message on start up about it not being configured. Which is where my question comes to.

I am trying to use xorg-edit to configure it all but I just don't seem to know whats going on. So its a tar.bz2 file which was extracted to my home directory, I go to the Terminal and type: 

>  cd ~/xorg-edit-08.08.06

and then it opens. Going by the instructions it then tells me to type 

> ./xorg-edit

Only for me to get an error, I will paste it here:  ./xorg-edit: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory

The problem is that the file IS there. Sigh :(

Can anyone help me configure my card please as this is annoying me! 
Remember I am very new to this so try and keep the jargon to minimal :)

Thanks to anyone that helps me.

---

### Post by mpl34 on 2009-02-07
Could you please give the details of the card, this can be found by using the following command,
```
lspci -v
```
this should also give information about the driver in use

---

### Post by Mickey_079 on 2009-02-07
0:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at d000 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at c000 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fc205000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: fc000000-fc0fffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: 00000000c4000000-00000000c40fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at c800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at cc00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fc204000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fc100000-fc1fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: medium devsel, IRQ 5
        Memory at fc206000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at d800 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at e000 [size=8]
        I/O ports at e400 [size=4]
        I/O ports at e800 [size=16]
        I/O ports at ec00 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300] (prog-if 00 [VGA])
        Subsystem: Unknown device 0001:0001
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, prefetchable) [size=64M]
        Memory at f9000000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 7000 [size=256]
        [virtual] Expansion ROM at f8000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
        Subsystem: Unknown device 0001:0000
        Flags: bus master, fast devsel, latency 0
        Memory at f9010000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Unknown device b000
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fc000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 8000 [size=8]
        I/O ports at 8400 [size=4]
        I/O ports at 8800 [size=8]
        I/O ports at 8c00 [size=4]
        I/O ports at 9000 [size=16]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fb000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        [virtual] Expansion ROM at c4000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
        Subsystem: Compro Technology, Inc. Videomate DVB-T300
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at fc108000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

05:01.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Subsystem: RaLink Unknown device 2561
        Flags: bus master, slow devsel, latency 32, IRQ 17
        Memory at fc100000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

05:02.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Unknown device 1021
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at b000 [size=64]
        Capabilities: <access denied>

---

### Post by mpl34 on 2009-02-07
This was all i was looking for ```
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300] (prog-if 00 [VGA])
 Subsystem: Unknown device 0001:0001
 Flags: bus master, fast devsel, latency 0, IRQ 16
 Memory at f4000000 (64-bit, prefetchable) [size=64M]
 Memory at f9000000 (64-bit, non-prefetchable) [size=64K]
 I/O ports at 7000 [size=256]
 [virtual] Expansion ROM at f8000000 [disabled] [size=128K]
 Capabilities: <access denied>
```the driver information.

Now if you haven't done already you will need to download your ati driver from [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") and then follow the instructions given [here]("http://www2.ati.com/drivers/linux/linux_8.24.8.html#172579") to complete the install... which it looks like you've already done... making sure you run fglrxconfig in the terminal as i would expect that this will automatically update your xorg.conf for your new driver.

However i may be wrong as i have only worked with NVidia drivers but it looks like a similar process, sorry i didn't reply earlier

---

### Post by Mickey_079 on 2009-02-07
Thanks for your help.

I'm currently on Vista at the moment but will switch over any minute to let you know if it worked or not.

I did come across another problem. Whenever I use Ubuntu and then go back to Vista for some reason my Compro DTV driver goes missing and I have to install it again. Do you know whats going on?

Cheers

EDIT: Well I just tried it and nothing. Look the driver is already installed, its configuring it so I can dual screen that I can't do.

---

### Post by mpl34 on 2009-02-07
well to configure you xorg file you can use ```
sudo nano /etc/X11/xorg.conf
```but i do not now how to edit it for dual screen. You may want to try the link given [here]("https://help.ubuntu.com/community/XineramaHowTo"), on how-to set up multiple monitors.

Sorry i didn't quite understand the problem.

---

### Post by Mickey_079 on 2009-02-07
Alright I typed in what you told me to do and this is what I got.

```
org.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
                               [ Read 96 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
```

Again I'm very new at this so I have no idea what I need to do. Thanks for your help!

---

### Post by mpl34 on 2009-02-08
sorry i haven't been in contact iv'e been having a few issues myself. You haven't quite included the full xorg.conf. You'll need to search through the pages either using the arrow keys or ctrl+V to go to the next page.

Again i have never modified my xorg.conf file manually but i  believe it may be required to run dual screens. Have you tried using the menu name display settings or something similar, it might be under systems settings. I'm using a KDE environment so the menu may differ slightly.

I the display setting there may be an option to clone monito or something. I'm at work so i can't check for you but may be possible.

---

