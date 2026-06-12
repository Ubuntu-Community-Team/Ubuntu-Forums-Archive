---
title: "Lost Sound in Lucid"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by jnmjr on 2010-05-13
Hey all, just lost sound in Lucid completely, started up the PC and nothing, I haven't done any up-grades or changed anything, can't figure it out, btw...sound works fine in WinXP....Any ideas?

---

### Post by -humanaut- on 2010-05-13
Go to the volume icon and click sound preference's and make sure the correct hardware is selected.

---

### Post by jnmjr on 2010-05-13
> **-humanaut- said:**
> Go to the volume icon and click sound preference's and make sure the correct hardware is selected.

Like I stated before, nothing has been changed, thre's just no sound!!!! :confused:

---

### Post by -humanaut- on 2010-05-13
I'd still recommend checking it could be as simple as clicking the right hardware such as ALSA.

---

### Post by jnmjr on 2010-05-13
> **-humanaut- said:**
> I'd still recommend checking it could be as simple as clicking the right hardware such as ALSA.

See ATT.
[ATTACH]156842[/ATTACH]

I haven't changed it???

---

### Post by jnmjr on 2010-05-14
I'm bumping this up, need help, don't know how to get this working:confused:

---

### Post by Sealbhach on 2010-05-14
Remove Pulse Audio in Synaptic and see if it fixes it - it usually does.

.

---

### Post by jnmjr on 2010-05-14
> **Sealbhach said:**
> Remove Pulse Audio in Synaptic and see if it fixes it - it usually does.

.

I removed it but it also removed the sound button from the panel, if I click sounds from preferences it says "waiting for sound system to respond", still don't know what's wrong????

---

### Post by Sealbhach on 2010-05-14
> **jnmjr said:**
> I removed it but it also removed the sound button from the panel, if I click sounds from preferences it says "waiting for sound system to respond", still don't know what's wrong????

OK, better put it back then if it didn't produce any sound.

Another thing to try is install aumix, and play around with the volume settings on that, to make sure everything is turned up.

Also, run

```
lshw -C sound

```

to find out what your sound card is, and google to see if any other users are experiencing problems with that sound card, it may be an update has got a bug in it.

.

---

### Post by jnmjr on 2010-05-14
> **Sealbhach said:**
> OK, better put it back then if it didn't produce any sound.

Another thing to try is install aumix, and play around with the volume settings on that, to make sure everything is turned up.

Also, run

```
lshw -C sound

```

to find out what your sound card is, and google to see if any other users are experiencing problems with that sound card, it may be an update has got a bug in it.

.

Ok, googled sound card no issues that I could dig up, all sound settings are on no issue there, the only thing is that when I reinstalled Pulse the volume panel button is not there and I don't know how to put it back???

---

### Post by Sealbhach on 2010-05-14
> **jnmjr said:**
> Ok, googled sound card no issues that I could dig up, all sound settings are on no issue there, the only thing is that when I reinstalled Pulse the volume panel button is not there and I don't know how to put it back???

Add the Indicator Applet to the panel, it should bring it back.

.

---

### Post by jnmjr on 2010-05-14
> **Sealbhach said:**
> Add the Indicator Applet to the panel, it should bring it back.

.

That was the first thing I tried and only the mail button shows up which I hadn't lost any ways....

---

### Post by jnmjr on 2010-05-14
I got it back by installing the sound indicator package from Synaptic.....I mean the button not the sound????

---

### Post by Black Hawk on 2010-05-14
Have you tried running speaker-test in the terminal? ctrl + c to exit speaker-test. 
Have you tried running sudo alsa force-reload ?

---

### Post by jnmjr on 2010-05-14
> **Black Hawk said:**
> Have you tried running speaker-test in the terminal? ctrl + c to exit speaker-test. 
Have you tried running sudo alsa force-reload ?

Did as you suggested, no sound??? I'm completely miffed by this???? It seems all should be working!!!!!!!!!!!!Sound card is recognized, drivers, Alsa, Pulse, it's all there and should be working :confused:

---

### Post by Black Hawk on 2010-05-14
post the output of

```
 cat /proc/asound/cards 
```

---

### Post by Sealbhach on 2010-05-14
Can you boot into an earlier kernel at the Grub menu?

.

---

### Post by jnmjr on 2010-05-14
> **Black Hawk said:**
> post the output of

```
 cat /proc/asound/cards 
```

 jose@My-Desktop:~$  cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE OEM [SB0570a] at 0xe800 irq 16

---

### Post by jnmjr on 2010-05-14
> **Sealbhach said:**
> Can you boot into an earlier kernel at the Grub menu?

.

Yes but makes no difference....

---

### Post by jnmjr on 2010-05-15
Finally a solution to this problem.....

"I figured out why I lost my sound. 

Apparently, there's an issue (very likely a bug) that caused my Audigy card to be switched from analog to IEC958 digital output at the level of Alsa. Changing the PulseAudio settings, therefore, had no effect. 

The solution was to install the GNOME ALSA Mixer from the software center and select analog source instead of IEC958."

This is a quote I read in the forum, will edit and  post name when I find the post again.

This solution had been there for me all along since the time I installed AlsaMixer but I totally overlooked it. Se la Vie.... Thank you all for your posts and help it is greatly appreciated :guitar:

See thread **"lucid lynx - no sound"**posted by eMJAYY

---

