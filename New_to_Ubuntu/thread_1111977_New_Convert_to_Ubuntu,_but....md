---
title: "New Convert to Ubuntu, but..."
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Zenmij on 2009-03-31
I recently changed my entire OS to Ubuntu form Windows and am very happy apart from 2 issues:

1, whenever I try to watch a video (on youtube for example) firefox crashes (3.0.8 from the repo's). This happens mainly when I click to watch a new video.

2, I frequently lose sound. Especially if I have switched from watching a video on youtube to playing a game or vice versa, I have to re-boot to get sound back.

I wondered if someone else might have stumbled upon these issues already.

Thanks.

---

### Post by carml on 2009-03-31
Did you install e.g. Adobe Flash player? Maybe Firefox is missing any plugins,for audio I don't have ideas at the moment.

---

### Post by HermanAB on 2009-03-31
Yup, the Adobe Flash plugin for Firefox is bad news.  Nothing much you can do about it, except upgrade when possible.

---

### Post by carml on 2009-03-31
If our suppositions are right,you don't need to restart your PC,just press ctrl+alt+backspace to restart the X graphic system.

---

### Post by pbpersson on 2009-03-31
I have a problem with my sound going dead all the time in Intrepid Ibex.  It is a known issue with some audio chips.

I did not bother to "fix" it on my machine.  I went through a long tutorial on how to verify that everything is configured properly with Pulseaudio but that did not fix it.

The sound will work fine for two days and will then be gone.

I put two icons down in the launch area - one to test the sound, the other to fix it when it breaks every two days.  I don't have time to.....there is a thread here somewhere about rebuilding your entire ALSA setup with new drivers or something but I think I will wait for Jaunty Jackalope to hop in and save the day.  :)

---

### Post by night_fox on 2009-04-02
I just looked throught my firefox plugins and I have "Shockwave Flash 10.0 r22" - no sign of the adobe one and my youtube works perfectly. You could try using that instead.

Pulseaudio is unnecessarily complicated but if you follow something on this page: [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio) you might be able to sort it out. It's meant to work properly in Ubuntu 9.04 Jaunty Jackalope which comes out in 21 days! No reason not to try and fix your 8.10 though.

---

### Post by mikechant on 2009-04-02
> It's meant to work properly in Ubuntu 9.04 Jaunty Jackalope which comes out in 21 days!

I hope so. I've been holding back on upgrading from 7.10 (last release before pulseaudio) since I really need my sound to work near-perfectly. I read loads of 'how-tos' for getting pulseaudio to work and although I understood the instructions, they nearly always ended with a number of comments saying 'this didn't work/made things worse/only partly fixed it'.

---

### Post by JohnLM_the_Ghost on 2009-04-02
I in fact removed Pulse at all...
Well there is this thing that ESD software (including Gnome sound events don't work), but I have my sound.
However I still doubt this would apply to you cause I hadn't my sound going silent in the first place (I had different problems).

---

### Post by night_fox on 2009-04-05
Quite frankly the sound system on ubuntu atm is a maze. You have pulseaudio with servers, sources, sinks, controls for each one of them, ALSA, OSS, controls for them, the pulseaudio manager (several config windows for it), Gnome ALSA mixer, alsamixergui, the System->Preferences->Sound, the gnome volume applet, laptop sound buttons etc....

---

### Post by JohnLM_the_Ghost on 2009-04-05
> **night_fox said:**
> Quite frankly the sound system on ubuntu atm is a maze. You have pulseaudio with servers, sources, sinks, controls for each one of them, ALSA, OSS, controls for them, the pulseaudio manager (several config windows for it), Gnome ALSA mixer, alsamixergui, the System->Preferences->Sound, the gnome volume applet, laptop sound buttons etc....
Yeah I fact it is one of the main reasons why I consider installing Gentoo.
I'm gonna build the sound system ground up my way.
Although it will still be probably Pulseaudio on ALSA.

@everyone
Sorry for slight off-topic.
Just to be clear I am NOT saying Gentoo is a solution for you, it will most likely require more work to be set up... way more.

---

### Post by markbuntu on 2009-04-05
You can setup pulseaudio to work properly in 10 minutes or less from a clean install in Hardy, Intrepid or Jaunty.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you are using the new KDE4 it may take 12 minutes

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

### Post by WinterMadness on 2009-04-05
just a quick tip: I wouldnt recommend using firefox in ubuntu. its slow and buggy.

Use Epiphany (which is based on ff, but is better) or Opera

---

