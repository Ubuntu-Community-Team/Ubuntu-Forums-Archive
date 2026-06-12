---
title: "Sound card issue :( ubuntu 10.10"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Kayuu on 2011-01-16
So I have a soundblaster audigy (CA0106) that I'm trying to get working, but after installing the GNOME ALSA Mixer as suggested by others there is still no sound output, Ive checked that nothing is muted but I'm not sure what to do~

lspci turns up: 

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:0c.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)

and sudo aplay -l shows:


**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any ideas? ><

---

### Post by diablo75 on 2011-01-16
I have an Audigy 2 and it quit working after some updates because someone decided to reverse/flip the behavior of a check mark in the mixer.  In Windows there is a checkmark in the mixer for the card that will force it to only play audio out through the digital output on the card, rather than the analog outputs.  Since those days, the mixer has been replaced but you can still gain access to a terminal based version of the ALSA mixer.  Before you do that, you should check your pulse audio output settings to see if it's set to send audio out through the Audigy, and no your on-board audio (although there's nothing preventing you from telling pulse to output audio through both cards at the same time).

The settings for Pulse can be found by clicking on the little speaker icon in the upper panel and then clicking the preferences button.  Have a look around, especially in the Hardware tab and the output tabs.  If the Audigy is already selected as an output device, check the speaker output settings.

---

### Post by Kayuu on 2011-01-16
I've got it to work now >< In pulse under output there were two options that were identical, I chose the unchecked option and problem solved, but the audio quailty doesn't seem normal like it was in Windows, is there a work around for that? Like enabling 24-bit or something like that?

---

