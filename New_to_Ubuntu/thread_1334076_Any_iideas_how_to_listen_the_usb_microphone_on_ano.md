---
title: "Any iideas how to listen the usb microphone on another pc in another room?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-11-22
Hello,

I connect with the console to SSH to another PC in another room, and would like to listen to the ALSA USB microphone connected to. 

Is that possible with Linux?

---

### Post by anders_c_ on 2009-11-22
If you figure out which device it is under /dev/ you might be able to play it through mplayer. Atleast thats how you view a connected webcam: "mplayer /dev/video0" you might need to add some things about which codec to use and stuff like that, it's probably different on different microphones.

---

### Post by frenchn00b on 2009-11-22
> **anders_c_ said:**
> If you figure out which device it is under /dev/ you might be able to play it through mplayer. Atleast thats how you view a connected webcam: "mplayer /dev/video0" you might need to add some things about which codec to use and stuff like that, it's probably different on different microphones.
 
my machine is composed like this:

lsmod | grep snd
```
snd_hda_intel         325688  0
snd_usb_audio          70272  0
snd_seq_dummy           2660  0
snd_pcm_oss            32800  0
snd_mixer_oss          12320  1 snd_pcm_oss
snd_pcm                62660  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss

```

/etc/modprobe.d/sound.conf has the following contents:

```
## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-usb-audio

## module options should go here
options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1
```

the famous microphone to be listened to is: 
alias [B]snd-card-1 snd-usb-audio
[/B]

---

### Post by frenchn00b on 2009-11-22
I did on my machine wiht USB mic
```
ohphone  --sound-in /dev/dsp1 -l
```

```

Command ? Incoming call from "skype [::ffff:192.168.1.3]" at Sun, 22 Nov 2009 17:31:59 +0100, answer call (Y/n)? y
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default - Check permissions or full duplex capability.
Could not open sound device Default -
```

and ohter:

ohphone 10.1.1.134

I replied the call but the USB isnt working :(

---

