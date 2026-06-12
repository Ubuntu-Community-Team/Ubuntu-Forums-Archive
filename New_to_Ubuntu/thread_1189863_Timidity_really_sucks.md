---
title: "Timidity really sucks?"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-17
I'm using Timidity to play midis and it sounds nothing like on Windows.
Some of the instruments are missing, the drums sound so terrible, the bass drum is so flat it's just awful.
I'm not sure if there are some additional packs or settings, or if there's something better than this?

---

### Post by mcduck on 2009-06-17
> **Gp. said:**
> I'm using Timidity to play midis and it sounds nothing like on Windows.
Some of the instruments are missing, the drums sound so terrible, the bass drum is so flat it's just awful.
I'm not sure if there are some additional packs or settings, or if there's something better than this?

That is the nature of MIDI, as it doesn't store sound, only instructions how to play different instruments (without even defining the actual instrument, so track intended for guitar may be played back as drums on other setup.).

In your case finding a better sound font should give better result.

You may also want to try Fluidsynth/Qsynth but in the end it's still up to finding a sound font that fits well for your MIDI file, or using a proper software studio where you can assign different MIDI tracks to different instruments.

---

### Post by Bölvaður on 2009-06-17
Look on the internet for:

8MBGMSFX.SF2
gm.dls


The first one is from ALSA, the second one is part of Windows, and they both sound highly similar if not identicle. I am not familiar with the program you are using but both tuxguitar and lmms can be made to use these sound fonts.
When you make them to be linked to your program instead of your current one, then you'll experience the exact same midi sounds as you are used to.
There are other sounds you can get, but I would assume you are most acceptible towards these two.

---

### Post by snl2587 on 2009-06-17
A little more detailed information:

If you want to use the alternate soundfonts (that's what they're called; you can also search for more of them), you'll need two things: the SF2 file and the "map". It takes some tweaking (and I'm sure guides are online), but the improvement in sound quality is worth it. Also, when I've done this the soundfont has gone in /usr/share/sounds/sf2 ... that path isn't usually listed anywhere.

---

### Post by Gp. on 2009-06-20
I just got 8MBGMSFX.SF2
and don't know what to do now?

---

### Post by PUZZLEchain.NET on 2009-11-05
Also just downloaded it... how can I "use it" for Tuxguitar?

---

### Post by PUZZLEchain.NET on 2009-11-06
Any help? :(

---

### Post by PUZZLEchain.NET on 2009-11-06
I don't even know where I can find guides to implement that 8MBGMSFX.SF2....

---

### Post by PUZZLEchain.NET on 2009-11-09
Bananas are curved yellow fruits.

---

### Post by Dennis N on 2009-11-09
I did the following with timidity to get better sound:

Install these sound fonts from the repos:

1) fluid-soundfont-gm
2) fluid-soundfont-gs

Then, open a command prompt, and type: 

```
gksudo gedit /etc/timidity/timidity.cfg
```

1) The last line in the file says: 

```
source /etc/timidity/freepats.cfg
```

Put a # mark at the beginning of that line to comment it out.

2) On the next line, type: 

```
soundfont /usr/share/sounds/sf2/FluidR3_GM.sf2
```

3) Save the file.

4) Restart timidity with 

```
sudo /etc/init.d/timidity restart
```

This should improve the default midi sound.

---

