---
title: "No digital surround"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Greblok on 2010-05-13
Hi people.

After  some testing and error, I found that Ubuntu is unable to give me  surround sound with SPDIF. I have an internal SPDIF cable from your sound  card (internal) to a GeForce 9500 GT with HDMI out.

In sound options of Ubuntu 10.04 I have the option of selecting various analog surround setup (which after  all is quite useless for me), and Digital Stereo (IEC958), no digital  surround sound.

This has worked smoothly in Windows, but it seems  that Ubuntu does not realize that the digital out is to send surround  sound, not stereo.

Tested with a 5.1 AC3  file.
The result is that the left and right front delivers sound  correct, the same with the center. However, when testing the rear speakers the sound is reproduced in the front left and right speaker.
Why?

Is it also possible to set  up both analog output (internally, to stereo desktop speakers) and  digital at the same time, so I do not have switch between them every time?

Analog stereo  works fine btw.
With analog stereo selected I  actually get stereo sound from my surround system as well as the desktop speakers, but I do not  quite understand why.

> ~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output


---

### Post by 2hot6ft2 on 2010-05-13
You might try these.

PulseAudio Fixes & System-Wide Equalizer Support
[http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=22](http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=22)

Make sound quality better in 2.5 Karmic
[http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=222](http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=222)
:guitar:

---

### Post by Greblok on 2010-05-16
Thank you, seems like I got a ltle bit further.
Still having trouble understanding it, but at least I have a place to start. :)

Edit:
2hot6ft2[COLOR=Black]'s tip solved it. Surround is now awailable. 
Marking the thread as solved.[/COLOR]

---

### Post by fluttman on 2010-07-25
I have the same problem with digital outputs.
Running 10.04 fully updated, as well as the latest version of Pulse and the equalizer.
I've tried with 3 different sound cards and it is always the same, surround sound is ONLY available on analog outputs....:( 

Any other ideas?

Thanks,

Fabian

---

