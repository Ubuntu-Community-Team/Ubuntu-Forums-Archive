---
title: "various audio problems with 10.10"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by profeta81 on 2011-04-07
hi all

I seem to have some sort of audio issue... this may not be an issue anymore in a couple of weeks after the upgrade, I just thought I mentioned it anyway.

I installed to 10.10 Maverick Meerkat a couple of weeks ago and since then I had experience various sound issues. I don't know if they're all related. First two issues encountered are in the playback of MP3s and other audio files: often the playback stops for several seconds (10 - 20) and then either resumes or the rest of the songs (audio file) is skipped; the second possibly related problem is than when I scroll pdf documents opened in evince a background noise can be clearly heard in the background, the noise is not very intense but very distinct and it is syncronized with the pdf files scrolling. The noise can only be heard when other sounds files are played back (MP3s etc), like an interference.

second issue is with the recording and the mic: any recording I try to make is very noisy, to the point that recorded speech cannot be understod when the recording is played back. I first noticed the problem when calling using skype, and afterwards I reproduced the problem with the sound recorder.

I'm attaching a file I created with me saying the phrase "hello, my name is Lorenzo" to give an idea of the recording problem.

I will be happy to give any diagnostic information on audio card (realtek ALC861 says in the gnome alsa mixer) and other things if needed and commands output...

regards all!
Lorenzo

---

### Post by 123456789123456789123456 on 2011-04-07
I see the problem.  listened to the file.  I use 10.10 at my church with recording audio services, I have not experienced any problems with the sound at all.  the only issue we seem to have is that the mic used picks up all backgraoud sound radiation.  this does not seem to be the same for you.  therefore, the only thing I can think of is a hardware compatability issue.  can you give us a list of your sound card specs?

---

### Post by profeta81 on 2011-04-08
right, I don't quite know how to do that...

I tryed lsp | grep Audio and it gives me:
```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

```
whereas, as mentioned above, the alsa mixed shows:
```

realtek alc861

```
and, on a website with the specs of the Satellite 100-206, I found the following:
> 
Audio:
 - Speakers : integrated stereo Harman Kardon® speakers
 - Producer : Toshiba Bass Enhanced Sound System con tecnologia SRS® TruSurround XT™ e SRS® WOW 


:confused: :confused:

---

### Post by grahammechanical on 2011-04-08
What kind of a microphone are you using? There is a difference between high impedance and low impedance. I do not understand it fully. I have forgotten a lot. But one type will be more likely to pick up background noise than the other type. Are you using a combined headphone and microphone set? They are designed to cut out background noise.

On my old Windows 98 machine I use to hear the mouse clicks through the external speakers that I had plugged into the sound card. I used a dial up modem and when I scrolled down the pages of the Ubuntu forum I would hear what sounded like Morse code from the speaker of the modem.

Your mouse scroll wheel might be causing the problem. How old is it? Is it wireless? Could you clean it in some way?

Regards.

---

### Post by profeta81 on 2011-04-08
> **grahammechanical said:**
> What kind of a microphone are you using? There is a difference between high impedance and low impedance. I do not understand it fully. I have forgotten a lot. But one type will be more likely to pick up background noise than the other type. Are you using a combined headphone and microphone set? They are designed to cut out background noise.

yes, combined headphone and microphone set, just the standard one you'd buy in shops for chatting and listening to music...

> On my old Windows 98 machine I use to hear the mouse clicks through the external speakers that I had plugged into the sound card. I used a dial up modem and when I scrolled down the pages of the Ubuntu forum I would hear what sounded like Morse code from the speaker of the modem. Your mouse scroll wheel might be causing the problem. How old is it? Is it wireless? Could you clean it in some way?

Sorry, maybe I wasn't clear enough, when I said "background noise" I meant something more like an interference, not so much a noise the microphone is picking up from the background such as typing on the keyboard...

cheers

---

### Post by profeta81 on 2011-04-08
sorry for double posting... I tryed the solution used in this thread "[SOLVED] Microphone not working in Skype":

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

this didn't work... also i tried the commands:
```

> arecord -l
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
> sudo lshw -C multimedia
[sudo] password for <user>:
  *-multimedia
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:46 memory:dc400000-dc403fff

```

In alsamixer and also in various websites I found that the audiocard should be Realtek HD Audio ALC861... I don't know whether this may be an issue...

I hope this is helpful...

---

### Post by profeta81 on 2011-04-11
nobody has any idea on how to fix this then?

sorry for bumping ;(

---

### Post by profeta81 on 2011-04-13
hello?

sorry again ;(

---

### Post by profeta81 on 2011-04-16
:(

---

