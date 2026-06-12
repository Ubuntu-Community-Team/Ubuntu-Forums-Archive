---
title: "Upgraded to Jaunty No Sound!"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-27
hi.. during my upgrade to jaunty i noticed that my sound stopped working.. after the restart it still seems to not work..

i have creative x-fi sound card, do i need to reinstall the "special" drivers that the retards at creative finally released? or is my sound card just simply not gunna work?

---

### Post by Didius Falco on 2009-04-27
This should help you out:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

Be sure and go to the post he links to - could save you some grief if the drivers don't work properly.


I hope it helps...

---

### Post by lindsay7 on 2009-04-27
I had the same problem. Make sure the volume in turned up in Ubuntu and your speakers. Go to sound in "System/ Preferences and try the test buttons for each setting.  Try auto and all the choices and see if that works. My sound was so low at first that I did not even recognize that the test was working when it was on the correct setting.

---

### Post by ayastona on 2009-04-27
i followed the advice above and my sound works but not for everything.. for instance youtube sound doesnt work.. as well as sound from other sites..

btw i have some flv files and stuff on my hard drive that i ripped from youtube and the sound and everythign works for those files.. its just online i cant hear anything

tw this link didnt work either cause i already have this thing installed: [http://blog.mintwebdesign.co.uk/ubuntu/fix-flash-sound-youtube-jaunty-jackalope-ubuntu-904/](http://blog.mintwebdesign.co.uk/ubuntu/fix-flash-sound-youtube-jaunty-jackalope-ubuntu-904/)

---

### Post by kansasnoob on 2009-04-27
Not much compiled yet for pulseaudio workarounds in Jaunty.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

I used this PPA:

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

but it was no cake walk getting things to work properly - in fact I still had some hiccups in VLC so I then had to install VLC 1.0.0 using this PPA:

[https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

All seems well so far but I don't use mplayer or any of the ipod type apps, so what's working for me may totally fry your sound!

---

### Post by ayastona on 2009-04-28
God damnit (that was in caps btw)

---

### Post by dpm_edinburgh on 2009-04-29
I have exactly the same problem: sound is fine in Banshee, but no sound at all in Youtube (on an HP dv6000 laptop).

---

### Post by UMDGaara on 2009-05-21
This may have something to do with the default PulseAudio setup in Jaunty - I've had this happen on both my desktop and laptop after fresh installs (not even upgrading).

To resolve, I installed the PulseAudio configuration tools which I've long said have no business being left out of Ubuntu ever since PulseAudio itself was included. You need the tools to configure the much-touted sound server and individual application-level volume control anyway - and now apparently to fix the default PulseAudio output device selection.

Anyway, in Synaptic install padevchooser and related dependencies. When finished, launch Applications -> Sound & Video -> PulseAudio Device Chooser. You'll get a new applet in your panel that looks like a little headphone jack.  Click that and change Default Sink from RTP Multicast Sink to whatever your sound card is.

That should be it. If you want to use the create Multicast/RTP sink and you still want local audio, you can probably also use the "Loopback audio to local speakers" check box in the Multicast/RTP tab of the PulseAudio Preferences window accessible by clicking Configure local sound server in the devchooser menu (didn't try this).

Another interesting note is that the sound server appears to be enabled by default without authentication required - anyone else see this as a security/privacy risk?

---

### Post by arito on 2009-05-28
This just happened to me too. I installed Flash plugin 10, and the problem went away (forgot to check which one I had before). Re-installation of the current Flash version might have been enough. By the way, I had to restart Firefox for this to take effect.

---

