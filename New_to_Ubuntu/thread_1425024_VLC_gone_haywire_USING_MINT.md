---
title: "VLC gone haywire USING MINT"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by misswham on 2010-03-08
yesterday when i tried to view a video through it, vlc comes up and closes immediately or it will open up and the box where the video would be is clear but i hear the audio. Now when I listen to music it plays fine but now the video part is acting a fool. i have gone to synaptic and did a total uninstall and then reinstall and now the same thing. I have turned OFF my compiz settings to NO EFFECTS at all and still the same thing. What does it sound like?

---

### Post by macabrem on 2010-03-08
I'm assuming this is a video you have viewed successfully in VLC before?  

Have you tried to view it in other movie players successfully?  

Have you installed any other software recently?

---

### Post by misswham on 2010-03-08
yes i have viewed other videos as well and they were successful.  i have tried other players on the same files and they work fine.  I have done the usual updates that i get in notification.  

vlc just had a better look as far as crispness of picture and it has sound effects that i can change.

---

### Post by misswham on 2010-04-04
Does anyone else have an idea on how to fix?  I just put Linux Mint on my laptop also and VLC is doing the same thing.

---

### Post by GSF1200S on 2010-04-04
Can you please run vlc from a terminal:
```
vlc
```
and post the results here?

It could be many things, but we should be able to fix it :)

---

### Post by Linuxforall on 2010-04-04
[https://launchpad.net/~onestone/+archive/vlc](https://launchpad.net/~onestone/+archive/vlc)

Add this ppa and update your vlc to the latest one.

---

### Post by GSF1200S on 2010-04-04
> **Linuxforall said:**
> [https://launchpad.net/~onestone/+archive/vlc](https://launchpad.net/~onestone/+archive/vlc)

Add this ppa and update your vlc to the latest one.

Haha, I was going to go there next if it wasnt simple ;)

---

### Post by misswham on 2010-04-04
aretha@aretha-desktop ~ $ vlc
VLC media player 1.0.2 Goldeneye
[0x9e06140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
/home/aretha/.themes/Plymouth Hemi 'Cuda Green/gtk-2.0/gtkrc:556: error: invalid string constant "text-is-fg-color-workaround-d", expected valid string constant
[0xa1d4080] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  102
  Current serial number in output stream:  103


this is what i got when i typed in vlc

---

### Post by Linuxforall on 2010-04-04
> **GSF1200S said:**
> Haha, I was going to go there next if it wasnt simple ;)


In terminal:

sudo apt-get --purge remove vlc

sudo apt-get autoremove

sudo add-apt-repository ppa:onestone/vlc 

sudo apt-get update

sudo apt-get install vlc

---

### Post by mc4man on 2010-04-04
> this is what i got when i typed in vlc 
A quick question that would affect what you may do - Do you have cairo-dock installed and running?

**If not** then *to test* a different video output start vlc from the terminal as such and try to play
```
vlc --vout x11
```
or
vlc --vout x11 /path/to/file

If you have cairo-dock and wish to keep then you'd probably want vlc 1.0.5 or you could run vlc without the embedded video in the interface

*To test* that start vlc with 
```
vlc --no-embedded-video
```

A ppa with vlc 1.0.5 and a bit more - 
[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

Edit: due to the large number of packages on the above linked ppa - while I don't use it I have tested some and they are fine.
I would suggest if using it, -   enable - get the app(s) you wish and then disable, - I wouldn't run the update manager with it enabled or you may update something you didn't intend or want to..

---

### Post by Linuxforall on 2010-04-05
> **mc4man said:**
> A quick question that would affect what you may do - Do you have cairo-dock installed and running?

**If not** then *to test* a different video output start vlc from the terminal as such and try to play
```
vlc --vout x11
```
or
vlc --vout x11 /path/to/file

If you have cairo-dock and wish to keep then you'd probably want vlc 1.0.5 or you could run vlc without the embedded video in the interface

*To test* that start vlc with 
```
vlc --no-embedded-video
```

A ppa with vlc 1.0.5 and a bit more - 
[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

Edit: due to the large number of packages on the above linked ppa - while I don't use it I have tested some and they are fine.
I would suggest if using it, -   enable - get the app(s) you wish and then disable, - I wouldn't run the update manager with it enabled or you may update something you didn't intend or want to..


Great ppa but too many extras whereas onestone's is just VLC which is better, unfortunately he hasn't upgraded his to 1.05

---

