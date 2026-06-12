---
title: "Audio is not working - 9.10 Karmic"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by miyagison on 2010-03-25
1.
I have a Gateway W340UA that has 9.10 Karmic installed on it. The audio was previously working ... working beautifully at that. Now, after the laptop was sitting on my desk acting as a web server dev environment for the past month the audio does not work. Where do I start in troubleshooting the problem? Btw, the strange part is that the microphone input still works! Just the speakers and the audio out port do not work!

2.
Didn't help. :/

Kernel is ok: 2.6.31-20-generic

Drivers ok:
[13.993712] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 19 (level, high) -> IRQ 19
[   13.993747] HDA Intel 0000:00:10.1: setting latency timer to 64
[   14.656160] input: HDA NVidia Mic at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input8

Users ok:
/dev/snd/controlC0:  -     1988 F.... pulseaudio
/dev/snd/pcmC0D0p:   -     1988 F...m pulseaudio

ALSA Mixer: Volume Maxed out

And the rest do not pertain to my sound card. 
Sound Card Chip: SigmaTel STAC9200

Another note, my speakers usually popped before the audio started .. now still nothing.

3.
> **tsk1979 said:**
> I had this same problem on kubuntu with my sigmatel card which comes in my Inspiron E1505.
I opened sound properties in system manager thingy, and there I saw three sources
1. Sigmatel blah blah digital
2. sigmatel blah blah analog
3. Pulseaudio

It allowed me to select which device should be used first.
It was set to digital, and it did not work.,
On analog and pulseaudio it worked fine.

I tried to get mp3 playing in amarok, and failed even after installing alternate codecs and stuff.
Then I shifted to songbird. Since I am used to songbird(used it on windows), I am happy now.

In my audio properties all i get is : Internal Audio - Analog Stereo Stereo.. Hmm. Different kernel didn't seem to help either. Looks like wipe and reload to see if that fixes it ... btw, the audio was previously working; however, the last time I was aware of the audio still working was about 2-3 weeks ago...

4.
> **tsk1979 said:**
> No need to do a complete wipeout.
If you know how to upgrade kernel, you could try that. Select the modules corresponding to your audio device.

alternatively do this
Add this line
options snd-hda-intel model=gateway
To
/etc/modprobe.d/alsa-base

This link will help
Forget the text, its in german, just look at the table
[http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA](http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA)

I will try that ... first, if it continues to be stubborn then I will wipe and reload. I know that 99% of all Linux issues can be solved without reformatting; however ... I am considering building my own kernel against the machine instead of using the generic stock kernel.

Cheers! :popcorn:

5.
Whatever caused the issues with my laptop have also caused an unstable bios as well. It seems that maybe the bios is bad or the motherboard is bad. I will try and see if I can flash the bios to see if that solves any issues. If not then my laptop has officially fried itself.

6.
:!: Problem diagnosed as the main-board is slowly dying and is unrelated to Ubuntu. WiFi Card Caused boot-locks... removed to solve... worked. Nvidia drivers failed to initialize after a recent reboot and after much frustration I have concluded that it's most likely the pci-bus going ... or something like that.

---

### Post by s.fox on 2010-03-25
Hello,

I would try following the steps outlined in [this]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") quick guide.  If you continue to have problems please post back. :)

-Silver Fox

---

### Post by miyagison on 2010-03-25
.

---

### Post by miyagison on 2010-03-25
.

---

### Post by tsk1979 on 2010-03-25
I had this same problem on kubuntu with my sigmatel card which comes in my Inspiron E1505.
I opened sound properties in system manager thingy, and there I saw three sources
1. Sigmatel blah blah digital
2. sigmatel blah blah analog
3. Pulseaudio

It allowed me to select which device should be used first.
It was set to digital, and it did not work.,
On analog and pulseaudio it worked fine.

I tried to get mp3 playing in amarok, and failed even after installing alternate codecs and stuff.
Then I shifted to songbird. Since I am used to songbird(used it on windows), I am happy now.

---

### Post by miyagison on 2010-03-25
.

---

### Post by tsk1979 on 2010-03-25
> **miyagison said:**
> In my audio properties all i get is : Internal Audio - Analog Stereo Stereo.. Hmm. Different kernel didn't seem to help either. Looks like wipe and reload to see if that fixes it ... btw, the audio was previously working; however, the last time I was aware of the audio still working was about 2-3 weeks ago...
No need to do a complete wipeout.
If you know how to upgrade kernel, you could try that. Select the modules corresponding to your audio device.

alternatively do this
Add this line
options snd-hda-intel model=gateway
To
/etc/modprobe.d/alsa-base

This link will help
Forget the text, its in german, just look at the table
[http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA](http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA)

---

### Post by miyagison on 2010-03-25
.

---

### Post by miyagison on 2010-04-16
.

---

### Post by miyagison on 2010-05-15
.

---

