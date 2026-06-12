---
title: "My sound card not working."
date: 2010-11-05
forum: New to Ubuntu
---

### Post by SungSean on 2010-11-05
I am a Xubuntu user on Pentium 3 Coppermine 866 Mhz, 256 Mb of RAM.
iI've installed my old Sound Blaster Live 5.1 sound card PCI. but cannot make it work.
My internal speaker is working. I checked BIOS to disable this motherboard sound card but there was no option for it. Help would be appreciated.

---

### Post by mastablasta on 2010-11-05
what kind of sound output you have in sound preferences? is the system recognising your sound card? have you checked the alsamixer soundlevels?
 
have you read this:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by SungSean on 2010-11-06
I have Master, Headphone, PC Speaker, AC 97 in sound preferences.
After reading your link I think I have my SB Live installed (read below).
All my alsamixer sound levels are not muted.
Thank you for the link.
I have followed some instructions from the link you gave me and found these results:

This is the list that appears when I type 'sudo aplay -l':

**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live! 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Live [SB Live! 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB Live! 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is what I get when I type 'lspci -v | less':

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio C
ontroller (rev 01)
        Subsystem: IBM Device 01c6
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at f000 [size=256]
        I/O ports at f400 [size=64]
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

01:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs Device 8065
        Flags: bus master, fast Back2Back, medium devsel, latency 16, IRQ 21
        I/O ports at 78a0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1


It look like my system recognize Sound Blaster 5.1  and installed it and the module says 'snd' so it is proper driver too.

---

### Post by P4man on 2010-11-06
I dont have xubuntu, so it might be a bit different there, but if you click sound preferences > output make sure you select the card to which your speakers are attached, so the soundblaster card. Its probably just using the onboard sound as default device.

---

### Post by SungSean on 2010-11-06
I assumed 'sound preference' option as when you click the speaker icon on top right corner and opened 'Mixer' window. So I am not sure I looked at the correct one. Could you point me to where exactly I could find 'sound preference' in Xubuntu? I spent long time looking but could not find it.

---

### Post by P4man on 2010-11-06
sorry, I dont have xfce here. Im sure there is a way to select the default sound card, but if you cant find it, install

padevchooser

Then in apps > sound and video > Pulse Audio device chooser  should add an icon to your panel where you should be able to select a default sound card (sink).

But like I said, Im sure there is an easier way.

---

### Post by SungSean on 2010-11-06
I ve installed Pulse Audio Device Chooser and I see that in the Volume window, SB live card is always displayed before internal sound card. Yet when I play music files, only the internal speaker plays and not through speakers connected to SB card. I used headphone to check if any sound plays through SB but no sound.

---

### Post by SungSean on 2010-11-07
I am sure SB Live is selected in sound preference option. Still sound comes only through the internal speaker not Sound Blaster.

---

### Post by P4man on 2010-11-08
Sorry, for padevchooser to work, you need one more step. Click the padevchooser icon in the notification area, select configure, network server, check the first three options. Then click the icon again, default sink, select the SB LIve.

There really ought to be a more straightforward way of doing this, but like I said, I dont have or know XFCE.

---

### Post by SungSean on 2010-11-12
Thank you P4Man. It worked and now music is coming from the SB Live card! Than you so much!!!
One more question though. I have 5.1 speaker and it has three audio connectors - green, black and orange.
I can't find on the web as to how they should connect to my SB Live 5.1 connectors (which are black, green, red, blue and orange.) Thank you again.

---

### Post by mastablasta on 2010-11-12
green to gree, black to black and orange goes to orange...
 
probably... 
 
Usually green on soundcard is line out, black is line in and orange is microphone. but if oyu have some complex speakers you could try other jacks because you could have one for subwoofer or how they are called.

---

### Post by XubuRoxMySox on 2010-11-12
Honestly I don't know why the Xubuntu developers decided to include PulseAudio. None of the default applications depend on PulseAudio, and it's been so problematic for so many people. I was [COLOR="Red"]**royally ticked off**[/COLOR] when PulseAudio showed up in Xubuntu 10.04, and particularly so because they chose a LTS version of all things to pull that stunt in.

I had lots of trouble trying to remove PulseAudio (it has tentacles, lol - not as bad as Plymouth, but lots of 'em) and getting ALSA set up. So much so that I looked around for another Xfce distro that isn't polluted with that abominable software and would last beyond the life of Xubuntu 9.10.

Then I read that **[COLOR="Green"]Linux Mint's Xfce edition[/COLOR]** - built on Xubuntu 10.04 LTS - does *not* ship with that evil, troublesome software! It was like getting Xubuntu Lucid "done right," free of the sound issue. 

I mean after all, I'm a dancer! Dancers gotta have sound!

-Robin

---

### Post by SungSean on 2010-11-13
Can I really try different connectors on sound card with different connectors of speakers? There are 3 connectors coming from speakers and I don't want to damage my sound card or speakers. Like electric damages.

---

