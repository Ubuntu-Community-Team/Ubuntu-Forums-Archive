---
title: "No sound in Ubuntu 8.10"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Art3mis on 2009-03-21
HI, everyone,

I NEED  STEP BY STEP HELP SO I CAN GET MY SOUND UP AND RUNNING

soundcards are detected but still there is no sound . ( IT IS A FRESH UBUNTU INSTALL)


PLS HELP I NEED THE SOUND SO I CAN LISTEN TO AUDIO FILES THAT I NEED FOR SCHOOL

---

### Post by miegiel on 2009-03-21
no reason to shout :D

Some stuff to try if you have no sound :

```
lspci
```
Verify that your soundcard is in the list, if it's not either your PC didn't see it during boot or ubuntu has no drivers installed for it.

If it's a card try sticking it in a different slot on your motherboard and verify if there is a linux driver for your card. [http://kmuto.jp/debian/hcl](http://kmuto.jp/debian/hcl) is a good place to start i assume :)

If your card is listed by lspci, than go to "System > Preferences > Volume control" to see if your sound might be muted. Under "Edit > Preferences" you can select channels that are hidden by default.

You can find more to read, including troubleshoot suggestions, at [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Art3mis on 2009-03-21
I HAVE NO CLUE WHAT MY TERMINAL SAYS

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by Art3mis on 2009-03-21
wait the link you gave me says ```
This database only verifies the PCI devices at this time. X drivers, ISA, USB, IEEE1394 or any other devices are out of the focus
```

---

### Post by rhcm123 on 2009-03-21
whoa dude, /cruise control. Now, go to System -> Preferences -> Sounds. Under "default mixer tracks", what mixer is selected, and what ones are available?

EDIT:
> **Art3mis said:**
> wait the link you gave me says ```
This database only verifies the PCI devices at this time. X drivers, ISA, USB, IEEE1394 or any other devices are out of the focus
```
yeah, thats what lspci is designed to do. This assumes that your sound card is a PCI variant

---

### Post by Art3mis on 2009-03-21
There are multiple options available

```
Capture: ALSA PCM on front:0 (STA92xx Analog)via..
Capture: Monitor Source of ALSA PCM on front:0....
HDA ATI HDMI (ALSA MIXER)
HDA ATI SB (ALSA MIXER)
IDT 92HD71B7X (OSS Mixer)
Playback: ALSA PCM on front:0 (STA92xx Analog)via.
```

---

### Post by Art3mis on 2009-03-21
When using ```
aplay -l
```

It says ```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by rhcm123 on 2009-03-21
> **Art3mis said:**
> There are multiple options available

```
Capture: ALSA PCM on front:0 (STA92xx Analog)via..
Capture: Monitor Source of ALSA PCM on front:0....
HDA ATI HDMI (ALSA MIXER)
HDA ATI SB (ALSA MIXER)
IDT 92HD71B7X (OSS Mixer)
Playback: ALSA PCM on front:0 (STA92xx Analog)via.
```

select the 4'th one on this list.
if that dosent work, try the 6th

---

### Post by miegiel on 2009-03-21
```
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This is the onboard sound of your mother board.

```
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This is (probably) the HDMI integrated sound on your graphics card. With HDMI tv connectors the sound goes through the same cable.

Since your card is there, did you try :
> If your card is listed by lspci, than go to "System > Preferences > Volume control" to see if your sound might be muted. Under "Edit > Preferences" you can select channels that are hidden by default."

yeah ... and this too :)
> **rhcm123 said:**
> select the 4'th one on this list.
if that dosent work, try the 6th

---

