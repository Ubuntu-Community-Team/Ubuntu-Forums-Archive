---
title: "Audio Voice Changer/Transformer"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by flyingpig on 2009-08-25
Hello,

Looking for software that is a voice changer/transformer that can alter the human voice. Looking for something that can do  voice "thickening", allowing users to convincingly change their vocal gender. Hopefully, it would afford separate control of pitch and formant, so the user's voice can be altered without the "chipmunk" effect.

**NOTE**: This is for** LIVE VOICE / VOIP calls online.**  
Thank you.

---

### Post by hansdown on 2009-08-25
Hi flyingpig.

Try audacity. It's in the repos.

---

### Post by flyingpig on 2009-08-25
hansdown,
it's for **live voice/voip **calls. so can't edit it.

---

### Post by hansdown on 2009-08-25
> **flyingpig said:**
> hansdown,
it's for **live voice/voip **calls. so can't edit it.

Oh. I'll keep looking.

---

### Post by flyingpig on 2009-08-25
thank you!

---

### Post by hansdown on 2009-08-25
There are some for windows.

[http://files1000.com/Shareware/communications/chat_instant_messaging/download_AV_Voice_Changer_Software_Diamond_84658.html](http://files1000.com/Shareware/communications/chat_instant_messaging/download_AV_Voice_Changer_Software_Diamond_84658.html)

[http://www.wareprise.com/2009/02/01/how-to-disguise-your-voice-and-change-the-way-it-sounds/](http://www.wareprise.com/2009/02/01/how-to-disguise-your-voice-and-change-the-way-it-sounds/)

---

### Post by flyingpig on 2009-08-25
thanks. i'm looking for something that works in ubuntu linux, though. and something free.

---

### Post by HermanAB on 2009-08-25
Howdy,

Sound Exchange (sox) can do anything:
$ man sox

You can pipe your audio through sox on the fly.

---

### Post by flyingpig on 2009-08-25
I did  "man sox". It appears it can do recordings, but can sox be used for live phone calls?

---

### Post by tgalati4 on 2009-08-25
You would do something like:

sox /dev/audio /dev/mixer pitch -200

Then run your VOIP application.

This will use the /dev/audio input (presumably the microphone) and lower the pitch by 2 semitones (1 key downward) without changing tempo appreciably and output in real time to /dev/mixer.

Where things get tricky is that you now have to set your VOIP program to use the /dev/mixer (not the microphone) as the input and you will have to get creative as to how to get output (though the headphones perhaps).

You will probably have to kill pulseaudio since you are using the sound hardware directly.

I'm not familiar enough with pulseaudio to create the appropriate source and sink to use with sox.  It's probably doable, it will just take some experimenting.

I don't know of any linux off-the-shelf package that will do that.  Most VOIP software is written with high-level frameworks.  It might be easier to program a pitchbend plug-in within the VOIP program itself.  Send an email to the developers.

---

### Post by sheridanm962 on 2009-12-31
try this [http://lobstertech.com/media/file/voicechanger/voicechanger-0.7.tar.gz](http://lobstertech.com/media/file/voicechanger/voicechanger-0.7.tar.gz) it's a voice changer ENJOY XD :guitar: :guitar::popcorn::lolflag:

---

