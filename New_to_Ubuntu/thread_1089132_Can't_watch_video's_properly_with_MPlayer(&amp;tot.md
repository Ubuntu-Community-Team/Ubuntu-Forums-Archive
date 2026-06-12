---
title: "Can't watch video's properly with MPlayer(&amp;totem2!)"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-06
Attempting to watch videos what I get is a continuous flashing light, very disturbing. I had that problem with totem, so I tried MPlayer. I made sure I installed all codecs but nothing, the problem's still there.
Any clue guys?
thx in adv!:)

---

### Post by chrisod on 2009-03-06
Have you tried VLC? I've had better luck with it than with any other video player.

---

### Post by Bölvaður on 2009-03-06
I second the vlc.
but you will also remember that there are some very bad codecs out there.

---

### Post by webwiller on 2009-03-06
I'll try...but I dont think it's a matter of player..but more of hardware, drivers, codecs...something like that! They were fine on WindowsMediaPlayer which I think it's worst...& than the same problem, different videos, different players, but same flashing light...mah...

---

### Post by kansasnoob on 2009-03-06
Have you installed the Medibuntu stuff:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I no longer bother installing the whole thing I just go for the dvd and codec support, but it's perfectly safe to install the Medibuntu repo!

---

### Post by spcwingo on 2009-03-06
I had this problem too until I changed my video card.  Yours wouldn't happen to be a S3 Unichrome based card, would it?  To find out:

```
lspci
```

---

### Post by webwiller on 2009-03-07
lspci gives this result re: graphic card:

01:00.0 VGA compatible controller: ATI Technologies Inc Device 95c2

Tried VLC, exactly the same fault: the screen flashes. But it's not just the video or movie which flashes, cause if I open a menu, I cant even read it cause it flashes too. Therefore I deduct that it is the whole screen which flashes, not just the video playing.

Tried medibuntu.

Any more suggestions will be appreciated..:)

---

### Post by spcwingo on 2009-03-07
Are you running the restricted video driver?

---

### Post by webwiller on 2009-03-07
What you mean by restricted video driver? How do I check that?

---

### Post by Yashiro on 2009-03-07
Try playing a movie with desktop effects disabled.(None)

Go into System (menu at the top of the screen), Preferences, Apperance, Visual Effects.

---

### Post by zika on 2009-03-07
> **webwiller said:**
> Attempting to watch videos what I get is a continuous flashing light, very disturbing. I had that problem with totem, so I tried MPlayer. I made sure I installed all codecs but nothing, the problem's still there.
Any clue guys?
thx in adv!:)
try System->Preferences>Multimedia_Systems_Selector->Video->X11(no XV)

---

### Post by webwiller on 2009-03-07
Bingo!
It works just fine if I put visual effects off. But how come...is it a bug? Any how to fix this properly?
Thx anyway!! Much appreciated!;)

---

### Post by zika on 2009-03-08
> **webwiller said:**
> Bingo!
It works just fine if I put visual effects off. But how come...is it a bug? Any how to fix this properly?
Thx anyway!! Much appreciated!;)
I gave You a fix ... ;)

---

### Post by Yashiro on 2009-03-08
There is a bug that means OpenGL effects (Desktop Effects) cannot sync the display at the same time as the xV video display.
This means they're essentially fighting for control.

My fix disables OpenGL Desktop effects. If your driver supports it, you will then get fully hardware accelerated movies.

Zika's fix allows you to leave composite effects turned on but your movies do not make use of hardware specific acceleration.
This means movies require more CPU power and scale badly when resized.

Your system is fine. It's a problem that affects everyones system to some degree. Yes, it's pretty poor.

---

### Post by zika on 2009-03-08
> **Yashiro said:**
> There is a bug that means OpenGL effects (Desktop Effects) cannot sync the display at the same time as the xV video display.
This means they're essentially figting for control.

My fix disables OpenGL Desktop effects. If your driver supports it, you will then get fully hardware accelerated movies.

Zika's fix allows you to leave composite effects turned on but your movies do not make use of hardware specific acceleration.
This means movies require more CPU power and scale badly when resized.

Your system is fine. It's a problem that affects everyones system to some degree. Yes, it's pretty poor.
on the spot! thanks!

---

### Post by webwiller on 2009-03-08
I dont have this menu:

try System->Preferences>Multimedia_Systems_Selector->Video->X11(no XV)

mhm....:O

---

### Post by zika on 2009-03-08
> **webwiller said:**
> I dont have this menu:

try System->Preferences>Multimedia_Systems_Selector->Video->X11(no XV)

mhm....:O
Al-F2->gstreamer-properties->Video->X11(no XV)

to enable it in a menu:System->Preferences->Main_Menu->Preferences->check:Multimedia_Systems_Selector

---

### Post by otakuj462 on 2009-04-15
Same issue here exactly, same video card, on an HP 6531s, same fix solved it. Someone should submit a bug report to launchpad.

---

