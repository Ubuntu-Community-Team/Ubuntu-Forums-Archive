---
title: "i need help with my sound card"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by opendevlite on 2009-04-26
this is my lspci -v

02:03.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 1004
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

i've tried with "Sound Preferences" and testing it with all the list with the "Test" button nothing makes a sound

please help me

thanks

---

### Post by kostkon on 2009-04-26
Try right-clicking on your speaker icon and select *Open Volume Control*. Then select the *Switches* tab and make sure that the *Analog/Digital* switch is *disabled*.

Also, it is better that you set your sound playbacks in sound preferences to *Autodetect*.

Hope that helps.

---

### Post by opendevlite on 2009-04-26
thanks i got it working

i had to adjust the volume to 0 of IEC958 Center, Front, Rear, Unknown and Analog Center, Rear, Side, and Capture feedback

because it was making some annoying sounds and Analog Front was the only control to have it working

---

### Post by opendevlite on 2009-04-26
i have another question

my motherboard has a PCI sound card and an onboard sound card, the PCI sound card which is my first problem got solve and is working ok

when i enable my on board sound card, when i select it on "Sound Preferences" and test it, it makes a sound but when i open a music video it doesn't make a sound, how do i make the music video make a sound?

thanks

edit
the pci sound card is connected to a headphone and the onboard sound card is connected to a speaker

---

### Post by kostkon on 2009-04-26
> **opendevlite said:**
> i have another question

my motherboard has a PCI sound card and an onboard sound card, the PCI sound card which is my first problem got solve and is working ok

when i enable my on board sound card, when i select it on "Sound Preferences" and test it, it makes a sound but when i open a music video it doesn't make a sound, how do i make the music video make a sound?

thanks

edit
the pci sound card is connected to a headphone and the onboard sound card is connected to a speaker
You need to install the *PulseAudio Device Chooser* from *Synaptic*. When you run it, right-click on its icon in the tray and select *Volume Control*. From there you will be able to select the default card for input and output (*Input Devices* and *Output Devices* tabs. Just right-click on the card you want and enable the *Default* option) and you will be able to send on-the-fly the sound of an application from one card to the other, etc... (*Playback* tab. Right-click on the stream you want and select *Move Stream...*)

And in you sound preferences you need to set your sound playbacks to *Autodetect*.

You will control your sound cards using the PulseAudio volume control and not the sound preferences.

Hope that helps.

---

### Post by opendevlite on 2009-04-27
@kostkon

installing "PulseAudio Device Chooser" fix my problem last night, but today i only hear a sssshhhh sound when playing vlc with the pci sound card, can i fix this?

thanks

---

### Post by opendevlite on 2009-04-27
i need help

---

### Post by kostkon on 2009-04-27
> **opendevlite said:**
> @kostkon

installing "PulseAudio Device Chooser" fix my problem last night, but today i only hear a sssshhhh sound when playing vlc with the pci sound card, can i fix this?

thanks
OK.

Put something playing on VLC (obviously something with sound) and then open the PulseAudio volume control and check if you can see its audio stream in the *Playback* tab.

If you can see it, then right-click on it and select *Move Stream...* and in the list that will appear select your PCI card.


If you can't see it then go to VLC's preferences and in the audio tree menu click on the *Output Modules*. You need to set the *Audio output module* to *ALSA* or *PulseAudio*, whichever is available. If both of them exist as options, then try them both.

Hope that helps.

---

