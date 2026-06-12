---
title: "My sound does not work!!!!!!!!!!!!!!!!!"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Art3mis on 2009-03-18
Sound does not work-----can anyone pls help

---

### Post by Therion on 2009-03-18
[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+comprehensive+troubleshoot](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+comprehensive+troubleshoot)

---

### Post by kansasnoob on 2009-03-18
Start by installing gnome-alsamixer either from synaptic or go to terminal and run:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Pay special attention to the first three toggles and the last four (VIA) toggles. Consider whether or not "external amp" applies!

It's also possible your sound card is not recognized so go to terminal and post the output of:

```
aplay -l
```

Also tell us what version of Ubuntu you're using!

---

### Post by kansasnoob on 2009-03-18
> **Therion said:**
> [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+comprehensive+troubleshoot](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+comprehensive+troubleshoot)

That is very, very outdated!

---

### Post by UnknownFear on 2009-03-18
I also need help on this. I am using Ubuntu 8.10

> **kansasnoob said:**
> 

I set the first 5 (Master, Master M, Master S, PCM and Surround) to MAX, and un-muted, and I also set the last 4 (IEC958 P, PC Speak, Aux and Capture) to max and un-muted.

[QUOTE]It's also possible your sound card is not recognized so go to terminal and post the output of:

```
aplay -l
```

Also tell us what version of Ubuntu you're using!

```
unknownfear@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [SB Live 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Live [SB Live 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Live [SB Live 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

That is what the output is for "aplay -l". I can't get any sound working at all! Please help.

---

### Post by The-IRS on 2009-03-18
have you installed the JACK controller?
Applications>system>add/remove

search JACK

---

### Post by kansasnoob on 2009-03-18
It looks like you have a sound blaster card so install Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Remember the gpg key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Then install from terminal:

```
sudo apt-get install alsa-firmware alsa-firmware-loaders
```

Then restart and see if it auto detects the card - and follow the previous instructions.

---

### Post by Therion on 2009-03-19
> **kansasnoob said:**
> That is very, very outdated!
Solved a problem for me last week when a friend had sound issues.

---

### Post by UnknownFear on 2009-03-19
I installed Medibuntu and followed all instructions. I than restarted the computer and, upon getting to the login screen, I heard the login noise so I thought it was working. I than logged in and went to the Sound options, but when I tested the sound, it didn't make any noise. All the Playbacks are set to Autodetect, the Sound Capture is set to ALSA - Advanced Linux Sound Architecture and the Device is set to Capture: ALSA PCM on front:2 (Intel ICH5) via DMA (PulseAudio Mixer). These were set be deault, I did not change anything. Any more help?

---

### Post by Therion on 2009-03-19
> **UnknownFear said:**
>  Any more help?
Two things...

1.  From your aplay -l output I see that you have onboard audio (via the integrated Intel audio chipset) AND the Creative Soundblaster sound card.  When you installed the Soundblaster, did you DIS-able the onboard audio?  If not, you need to enter you BIOS and disable the onboard audio chipset.

2.  Right-click on your Volume Control icon and go to Properties.  Do you have a "Switches" tab?  
If so, open it and see if you see a check-box labeled: **Audigy Analog/Digital Output Jack**.  If you do... UN-check that box.

---

### Post by Eisenwinter on 2009-03-19
Post the output for the command **asoundconf list**

If that command doesn't work (which means you don't have ALSA installed at all), post the output of the command **lspci**, and I'll try to help you install ALSA for your card.

---

### Post by UnknownFear on 2009-03-19
***asoundconf list***
```
Names of available sound cards:
Live
U0x46d0x8ce
ICH5
```

***lspci***
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)
```

---

### Post by Therion on 2009-03-19
> **UnknownFear said:**
> 

***asoundconf list***
```
Names of available sound cards:
Live
U0x46d0x8ce
ICH5 **[color="red"]<--- Onboard Audio Chipset[/color]**
```

You need to disable your onboard audio chipset as I mentioned earlier.

---

### Post by UnknownFear on 2009-03-19
How exactly do I disable this onboard memory chipset?

{EDIT} OK, I unchecked ***SB Live Analog/Digital Output Jack*** and I set everything to MAX, this is for SB Live 5.1 [SB0220] (Alsa mixer). I than restarted my computer, yet I don't have any sound. Everything is set to ALSA, and the Device is set to SB Live 5.1 [SB0220] in the Sound settings.

{EDIT 2} Sorry, I didn't disable the onboard chip as I do not know how. I check the BIOS, but I don't see anything about disabling onboard chipset.

---

### Post by UnknownFear on 2009-03-19
I GOT IT! I found the chipset in the BIOS. It was only labled as "Audio" so I disabled it and I now have sound! WOO!! Thanks Therion!!!

---

### Post by Therion on 2009-03-19
> **UnknownFear said:**
> I GOT IT! I found the chipset in the BIOS. It was only labled as "Audio" so I disabled it and I now have sound! WOO!! Thanks Therion!!!
No problem.  Glad it worked out for you.

---

