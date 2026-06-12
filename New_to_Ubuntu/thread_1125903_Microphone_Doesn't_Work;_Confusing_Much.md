---
title: "Microphone Doesn't Work; Confusing Much?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Unanimated on 2009-04-14
Okay, I had a Windows install side-by-side with my Kubuntu 8.10 for about a week, but then I removed it. However, my microphone worked just fine in that installation, with no work at all (except for finding the driver online). I installed Kubuntu 8.10 from an Ubuntu 8.10 installation, hoping it would be faster and just better for me (it was, by the way). However, my microphone worked flawlessly in Ubuntu 8.10, using regular ALSA drivers for my Audigy sound card. Now, in Kubuntu 8.10, I'm using those same ALSA drivers, but I cannot for the life of me figure out how to get my microphone working. When I blow into it or something, I can hear it through the speakers, but all of my applications either say that there was no microphone detected or there is just no audio at all in the result.

If it helps, I'm using the XINE engine for sound, with Phonon GStreamer as a backup.

Also, recording a sound in Audacity says that an error was made in opening the sound device. I've also attached a screenshot of that.

LSPCI Output:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/CPIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100(rev 11)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)
```

I've also attached a screenshot of my Communication and Accessibility tabs in my Multimedia page in System Settings.

---

### Post by nwadams on 2009-04-14
Hmm. interesting. Do you get similar output volume from your speakers in kubuntu vs. windows?

this could be a pulseaudio issue. Pulse audio is not supported natively by certain applications yet. (skype, etc)

But since it worked correctly in ubuntu...hmm what apps are u using specifically. Could someone more familiar with KDE apps and how KDE audio works please help here.

---

### Post by Unanimated on 2009-04-14
Well, in Windows, the only difference would be that I couldn't hear the mic input coming from the speakers, but I assume that's because of a difference in the drivers. I was using the proprietary Creative Labs drivers in Windows. Also, I've tried using Audacity and Traverso in Kubuntu, and neither can open the device to record. Things went fine recording in Ubuntu with Audacity. I could even record voice clips in aMSN, which I don't use anymore.

---

### Post by nwadams on 2009-04-14
This is beyond my knowledge now. I'm sorry but i don't know enough about kubuntu to understand why it would work in ubuntu and not in kubuntu.

---

### Post by markbuntu on 2009-04-15
Hmm, I don't know how well audacity will play with Phonon which is the sound server in KDE4. I don't know if Phonon even supports OSS.

But, you can add pulseaudio, audacity works with pulseaudio in Intrepid

Read these

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

If you try this let us know how you make out.

---

