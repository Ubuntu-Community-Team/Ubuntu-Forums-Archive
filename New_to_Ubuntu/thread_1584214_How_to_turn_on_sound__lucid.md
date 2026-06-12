---
title: "How to turn on sound?  lucid"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by balise on 2010-09-28
I installed Ubuntu lucid on my new Dell laptop after installing W7.  Dualboot is fine, but I hate always having to boot into W7 to listen to youtube / songs etc.  I have looked and followed up on *many* "no audio" posting but haven't got a peep from the box after about six months.  It is very confusing and complicated.  Is there any checklist or such anywhere?  It is maddening.  I'm not totally stupid (started on version 7 Unix lo these many years ago), but sound on Ubuntu seems designed to make you feel so.  Please help!

Ps: Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
When I "lsmod" and grep "snd" I get so many things I want to switch to something simple like Gentoo.  %^)

Thanks, -jae

---

### Post by QIII on 2010-09-28
I'm not sure if it will help, but you might try looking here if you haven't already.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

I can't recommend for or against OSS, but this is at least one option.

What is the model of your laptop?  I'll see if I can find something particular to it.

---

### Post by balise on 2010-09-29
QIII, it's late here so I'm not going to go any further, but your suggestion looks good so far, having read some resonant stuff on various sites w.r.t. OSS.  Don't want to diss Linux / Ubuntu, but.  Thank you.  I'll go farther on my own and interact with this thread also.

I'm on a Dell 1458.  Should have got larger pixels, considering my age, but what did I know?  

-jae

---

### Post by Exxplicit on 2010-09-29
You can try updating ALSA.  I installed a new mobo and this fixed my sound problems.

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

### Post by BigRedButton on 2010-09-29
you could also try just reinstalling/updating all of the audio related packages via Synaptic. pulseaudio, ALSA, possibly the relevant applet. Also look under System>Administration>Hardware Drivers to see if you need to install something

Also, about the text size for ease of reading, you can always adjust the resolution via the Monitors section under System, or take a look at Orca.

---

### Post by mastablasta on 2010-09-29
> **BigRedButton said:**
>  
Also, about the text size for ease of reading, you can always adjust the resolution via the Monitors section under System, or take a look at Orca.
 
or hold Ctrl and move the mouse wheel up and down to zoom & zoom out.
 
edit: good trouble shooting guide for sound: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 
seriously though Updated alsa goes a long way in these intel sound cards...

---

### Post by balise on 2010-09-29
Being wined and dined on my B-day today  ..  Thanks all for the tips.  Think I'll try re-installing latest Alsa, then go for pure OSS if it doesn't cure.  Some of the stuff I read about OSS sounds authentic.  .. But, tomorrow.

---

