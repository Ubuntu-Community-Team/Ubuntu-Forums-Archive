---
title: "XVidCap No Audio Codec"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by DavidG24 on 2011-03-20
hi guys,

I just installed XVidCap on my system (Ubuntu 10.10 x64) and have found that whilst the video records perfectly there is no audio. I have a Logicam Webcam (with a built in mic) and have setup the sound preferences so that it uses it as the mic input (this all works in gtk-recorder). Anyways once a video is recorded in the output dialog window that comes up it says that there is no audio codec. I went to the preferences in XVid and under the 'Multi-Frame' tab the Audio settings list the the Enable Audio checkbox is ticked and the Input Device is in /dev/dsp, further the audio codec auto checkbox is ticked.

So, I thought I would see what was in /dev/dsp, and I found that this directory doesn't exist?

Any suggestions?

Cheers,

David

---

### Post by Daveth on 2011-03-20
that dev/dsp thing is Oss related, apparently, and the net has solutions derived from using Oss-emulation in ALSA, or doing dark arts with Jack - hardly easy by the sound of it.
This post
[HTML]http://sourceforge.net/apps/mediawiki/xvidcap/index.php?title=Faq#Recording_sound_does_not_work_.28or_it_only_works_for_the_microphone.2C_not_application_output.29[/HTML]
suggests that tinkering with the ALSA sound mixer can get it to work, and does offer up to some things to play with.
I must say that my use of XVidCap has always been with silent offerings!
Let everyone know if you crack this.

---

