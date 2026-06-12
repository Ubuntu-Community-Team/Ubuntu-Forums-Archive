---
title: "Youtube"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2006-12-24
My default sound card has been digital but there has been no sound out of my card at all under edgy. Then I switched device in the volume controller to analog and hear a youtube film's  sound. I stop the recording, restart: no sound at all on any films. I have tried switching back and forth between analog AD1968A (oss mixer) and HDA via VT82XX(Alsa mixer) and no sound comes out at any time. 

When I scroll block down the Terminal screen I can hear a clicking sound on my headphones.
So there is some sound.

I wonder if it is a media player fault.

I tried mplayer plug-in for mozilla and everytime I click on a radio connection it soon says stopped!



Robin

robin@robin-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

robin@robin-desktop:~$ lspci -v
```
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: VIA Technologies, Inc. PT894 Host Bridge
        Flags: bus master, medium devsel, latency 8
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: VIA Technologies, Inc. PT894 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: VIA Technologies, Inc. PT894 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: VIA Technologies, Inc. PT894 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
        Subsystem: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
        Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f9000000-fbafffff
        Prefetchable memory behind bridge: c0000000-cfffffff
        Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
        Subsystem: VIA Technologies, Inc. VT8237A SATA 2-Port Controller
        Flags: bus master, medium devsel, latency 64, IRQ 193
        I/O ports at dc00 [size=8]
        I/O ports at d880 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=16]
        I/O ports at d000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at c880 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 193
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at c480 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 64, IRQ 193
        Memory at f8ffbc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Flags: medium devsel
        Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. Unknown device 337e
        Flags: bus master, medium devsel, latency 128
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at c000 [size=256]
        Memory at f8ffb800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCIE Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fbb00000-fbbfffff
        Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fbc00000-fbffffff
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0392 (rev a1) (prog-if 00 [VGA])
        Subsystem: LeadTek Research Inc. Unknown device 2a52
        Flags: bus master, fast devsel, latency 0, IRQ 225
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at ec00 [size=128]
        [virtual] Expansion ROM at fbae0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at fbbfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

04:04.0 Communication controller: Intel Corporation 536EP Data Fax Modem
        Subsystem: Intel Corporation Unknown device 1000
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at fbc00000 (32-bit, non-prefetchable) [size=4M]
        Capabilities: <access denied>
```

robin@robin-desktop:~$ 



sudo modprobe snd- TAB ENTER 
   Result:

   FATAL: Module snd_ not found.
   robin@robin-desktop:~$

---

### Post by Robbyx on 2006-12-24
Much to my surprise I now have the sound working. I went into Automatrix and looked for any codec or related programs.

It is also running the digital form the sound via the Alsa Mixer. 

What is a bit anoying is that I am not getting stereo. Only the right side is playing.

Robni

---

### Post by Robbyx on 2006-12-24
I have lost the sound again.

I adjusted the volume control in the Alsa mixer and the minute I touch it the sound goes. I can not get it back!

Any suggestions?

Robin

---

### Post by Robbyx on 2006-12-24
I have just run 'tgstreamer-properties' with the following results. Are they anything to do with the loss of sound?

robin@robin-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
robin@robin-desktop:~$

---

### Post by Robbyx on 2006-12-25
I have just gone through all the tests in another thread at 

[http://www.ubuntuforums.org/showthread.php?t=227469&highlight=no+sound+again](http://www.ubuntuforums.org/showthread.php?t=227469&highlight=no+sound+again)

It is reported there that the gstreamer the list of unavailable gstreamer plugins is usual.

robin@robin-desktop:~$ sudo aptitude install linux-sound-base alsa-base gstreamer0.10-alsa
sudo dpkg-reconfigure linux-sound-base
sudo dpkg-reconfigure alsa-base

Produced no problems 
----
This produces no sound:
aplay /usr/share/sounds/phone.wav

No errors with gnome-volume-control from terminal
-----
I am joined to the audio group in my system

Currently I can not hear anything from the computer's sound system. I am about to try the live CD.

Robin

---

### Post by Robbyx on 2006-12-25
The idea of running from the live CD no longer works. I use a dual screen and for some reason the live cd does not like either screens. One is blank and the other has blue dotted lines diagnally accross it with black inbetween them. I had ran the disk that I used to install the system originally and of course it woked then. I had also uesd it to do a recovery and it worked as well. 

At one stage I had a big struggle to make the two screens work but I did not expect the changes I had to make to the xorg.conf would have any difference to the livecd startup.

I am a bit stuck now. Any ideas on the sound card problem.

Robin

---

### Post by Robbyx on 2006-12-26
I swapped the monitors round at the video card and was able to run the LiveCD. I then tested the sound using:

aplay /usr/share/sounds/phone.wav

This worked except that it was single channel and no amount of adjustment of the Alsa controls made it work in stereo. The analogue sound control worked but it to was in mono.

Can I have some suggestions as to what to do next?

---

### Post by rlozano on 2006-12-26
did you try alsamixer in the terminal and see if you can get your sound if you configure your alsamixer from there

---

### Post by Robbyx on 2006-12-27
Yes I tried it in the terminal.

Thanks for replying I was beginning the think  I would have to change my deodorant.

Robin

---

### Post by malfist on 2006-12-27
YouTube is flash, I cannot get sound from flash either, although other sound works fine for me.

---

### Post by Robbyx on 2006-12-27
With the fully installed Ub no sound. With liveCD sound. None of this sound sensible to me. Any further ideas how to recover the sound?

---

