---
title: "How to find out the correct sound model for snd-hda-intel?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Lysi on 2009-01-17
Hallo everyone,

this is a rather lengthy post... sorry for that.

Maybe this is not so much of a beginner question but I feel like one in that particular problem. If it is inappropriate here, feel free to move it to multimedia.
My system is a dapper upgrade to hardy where I switched now from alsa to pulseaudio daemon. The idea behind pulseaudio is really nice and I hope that this will be the final conceptual design for all sound in linux.

I have read tons of information about the configuration and interaction of the new sound demon and the user interface. If someone else is looking for information take theses links e.g.

These two are actually the best  ones I have found and I highly recommend them to everyone looking for a way out of the confusing interactions of alsa, oss, esd, jack, pulseaudio and whatever you can come up with.
[b]
[[SOLVED] Multiple Sound Solution (ALSA w Pulseaudio)](http://ubuntuforums.org/showthread.php?t=843012)
[How it works, SOUND](http://ubuntuforums.org/showthread.php?p=5931543)[/b]
and more my problem related:

[Realtek ALC888 Audio Install](http://ubuntuforums.org/showthread.php?t=674437)
[HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support](http://ubuntuforums.org/showthread.php?t=789578)
[The Perfect Setup](http://www.pulseaudio.org/wiki/PerfectSetup)

so if I understand the system correctly the underlaying driver of pulseaudio is from alsa. Therefore the model in /etc/modprobe.d/alsa-base for sound-hda-intel should be the one of the onboard sound chip on my MSI P35.
I checked for the correct card and audio chip set.
```
 cat /proc/asound/card0/codec#* | grep Codec*
Codec: Realtek ALC888

```
```
lspci -vvv
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 735a
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

Now if one checks the configuration for hda-intel and ALC888 in 
```
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

        ALC883/888
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          3stack-6ch    3-jack 6-channel
          3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
          6stack-dig-demo  6-jack digital for Intel demo board
          acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
          acer-aspire   Acer Aspire 9810
          medion        Medion Laptops
          medion-md2    Medion MD2
          targa-dig     Targa/MSI
          targa-2ch-dig Targs/MSI with 2-channel
          laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
          lenovo-101e   Lenovo 101E
          lenovo-nb0763 Lenovo NB0763
          lenovo-ms7195-dig Lenovo MS7195
          haier-w66     Haier W66
          6stack-hp     HP machines with 6stack (Nettle boards)
          3stack-hp     HP machines with 3stack (Lucknow, Samba boards)
          6stack-dell   Dell machines with 6stack (Inspiron 530)
          mitac         Mitac 8252D
          auto          auto-config reading BIOS (default)

```

And here I am and I am confused:confused:. How do you choose now the correct model? Do you just do try and error until all sound problems disappear or what to do here?
I tested currently with 
```
targa-dig     Targa/MSI
targa-2ch-dig Targs/MSI with 2-channel
auto

```
The problem for me is actually that I am relatively clueless what the number of jacks and channels, spdifs or whatever is the correct one for me, since I am no sound card expert. However there is light at the end of the tunnel at least :):) I somehow grasp some essentials already.
Is there a way like lspci -vvv which checks this onboard or do I need to check manuals etc. ? 

So why I am testing all the different models? 
Because in my current system I got stutter output with tvtime or teamspeak has no mic or stuttered blurred mic with ```
padsp teamspeak
```... And I hope that the correct sound chip model would solve these problems.
I played around with the number of channels in /etc/pulse/daemon.conf and then sound disappears in tvtime.

System/Preferences/Sound is set all to pulseaudio and default mixer tracks:
Playback Alsa PCM on front:0 (ALC883 Analog) via DMA (PulseAudioMixer) 
Gnome volume applet is set to the same playback device and all controls are switch on or at 100%.

currently in /etc/modprobe.d/alsa-base ```
options snd-hda-intel model=targa-2ch-dig
```

and the test sound now stutters as well .. :confused::confused:
what also confuses me is the fact that tvtime never shows up in pavucontrol, also with padsp it is not there... :confused::confused: Is it using oss / esd or alsa? I have no idea, but it doesn't seem to block the device.

While we are at it, one last question. I realized that the gnome volume applet has still influence on the whole sound system if one changes the device there to alsa mixer etc. Why? Shouldn't have the pulseaudio daemon control about this?

Thanks for your replies and keep it up. Ubuntu has by far the best linux community I have met:popcorn:,
Lysi

p.s.
English isn't my native language but I hope I made my problem clear.

---

### Post by -gator- on 2009-01-20
Hey 

Just try some models untill your sound works correctly. On my laptop none of the models worked as it should, i tried medion, base, acer,... 
I found on internet to try: options snd-hda-intel model=3stack-6ch and this works perfect.

Sorry if there are faults in my english ;)

GrtzZ

Stefan

---

