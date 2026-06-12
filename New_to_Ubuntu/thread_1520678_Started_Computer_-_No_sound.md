---
title: "Started Computer - No sound?"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by ehderube on 2010-06-29
Hi,

I just started my machine today and I have no sound but had sound previously.  I checked the alsamixer and all the volumes are up and the right sound card is selected.  I checked pulseaudio and it is running with right sound card. I type in aplay -l and get the correct hardware.  I run lspci -v and get this 

```
01:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at c000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

```


So I'm at a lost, I didn't change anything and I just lost my sound, any theories?

---

### Post by kostkon on 2010-06-29
In alsamixer, check the Analog/Digital switch's state; if it is enabled then try disabling it or vice versa.

---

### Post by ehderube on 2010-06-29
How do you do that?  when I load alsamixer I get a gui in terminal with limited options.

---

### Post by blues2use on 2010-06-29
This may be worth taking a look at: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I had a similar sound problem recently (login sound just stopped working) and this article helped me.

Good luck...

---

### Post by ehderube on 2010-06-30
Still no sound....

I'm starting to lose faith in ubuntu.

---

### Post by ehderube on 2010-06-30
Well to who ever has the same problem here my fix:

Apparently it was the analog / digital switch.

in terminal type alsamixer

scroll to a column that does not have a volume bar mine was called just S/PDIF (there are other called S/PDIF F or C, etc.)

once on the column type "m" to toggle it on or off.  My sound came back on.

---

### Post by cwmoser on 2010-06-30
I have no sound too.

When I run Alsa Mixer, there is essentially a blank window - just a couple of sliders that don't work.

Never had a sound issue with Ubuntu with prior installations.  Looks like 10.04 Lucid Lynx is going to be a dud.

Carl

---

### Post by ehderube on 2010-06-30
you use the left and right arrow keys to move from column to column and up and down to change the volume. This is what mine looks like, is your's the same?

[IMG]http://imgur.com/HtKSB.png[/IMG]

---

