---
title: "music not working after upgrade"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by rlj399 on 2009-11-30
Whenever I click a music file (which worked before i upgraded to the new ubuntu) it doesn't play or it'll play for about half a second and then stop. Other sources of sound work just fine like videos from youtube (although now after the upgrade i can't pause or control the video in any way). Is there some quick way to fix everything i had working before the upgrade??

---

### Post by BOZG on 2009-12-02
> **rlj399 said:**
> Whenever I click a music file (which worked before i upgraded to the new ubuntu) it doesn't play or it'll play for about half a second and then stop. Other sources of sound work just fine like videos from youtube (although now after the upgrade i can't pause or control the video in any way). Is there some quick way to fix everything i had working before the upgrade??

Have you installed the multimedia codecs?

Try [ul=Medibuntu]http://medibuntu.org[/url]

---

### Post by rlj399 on 2009-12-03
yes sir, it has been installed since before the upgrade and i just checked right now and it said it was already installed :-(

---

### Post by BOZG on 2009-12-11
> **rlj399 said:**
> yes sir, it has been installed since before the upgrade and i just checked right now and it said it was already installed :-(

Have you sorted this out yet?

Did you make sure that the correct repositories for Karmic are installed?  If you upgraded, the old repositories might still be installed which could be a problem.

---

### Post by RedSingularity on 2009-12-13
What program are you using to play music?

---

### Post by rlj399 on 2009-12-15
no, i have not resolved my problem yet :-(
How do i know if the right repository is installed?
I've tried like 4 music players so i highly doubt the player is the problem.
Also I dual boot windows 7 so maybe that's causing a problem?

---

### Post by northern lights on 2009-12-15
> **rlj399 said:**
> How do i know if the right repository is installed?Repositories are never "installed". Repos also are nowhere near related to your audio problem. For the sake of complete information:
You'll find a list of the currently enabled repos under */etc/apt/sources.list* or via 'System > Administration > Software Sources'.

As an aside @BOZG: Guessing or made-up "solutions" are never helpful to the OP.

> **rlj399 said:**
> I've tried like 4 music players so i highly doubt the player is the problem.mkey. Then it isn't.

> **rlj399 said:**
> Also I dual boot windows 7 so maybe that's causing a problem?Nopes. If you've booted Ubuntu, it's irrelevant whether any other OS(s) is/are installed on the system.

Can you please post the outputs of ```
aplay -l
```and```
aptitude search phonon
```Also, what files are you trying to play? mp3 only? Does the same happen with flacs or wmas?

---

### Post by BOZG on 2009-12-16
> **northern lights said:**
> As an aside @BOZG: Guessing or made-up "solutions" are never helpful to the OP.

I didn't see anyone else helping.  Obviously it's better to just ignore the issue than try and help at all.

Having had issues with sound in the past which were resolved after changing the repositories, it's hardly a guessing or made up "solution".

---

### Post by rlj399 on 2009-12-19
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



p   libphonon-dev                   - development files for Phonon multimedia fr
p   libphonon4                      - Phonon multimedia framework for Qt 4, dumm
i A libqt4-phonon                   - Phonon multimedia framework for Qt 4      
p   libqt4-phonon-dev               - development files for the Phonon multimedi
p   libqtscript4-phonon             - Qt Script bindings for the Qt 4 Phonon lib
i A phonon                          - metapackage for Phonon multimedia framewor
v   phonon-backend                  -                                           
p   phonon-backend-gstreamer        - Phonon GStreamer 0.10.x backend           
p   phonon-backend-null             - Phonon null backend (no real backend)     
i A phonon-backend-xine             - Phonon Xine 1.1.x backend                 
p   phonon-dbg                      - Phonon debugging symbols                  
p   python-qt4-phonon               - Python bindings for Phonon                
p   python-qt4-phonon-dbg           - Python bindings for Phonon (debug extensio
v   python2.5-qt4-phonon            -                                           
v   python2.5-qt4-phonon-dbg        -                                           
v   python2.6-qt4-phonon            -                                           
v   python2.6-qt4-phonon-dbg        -

---

