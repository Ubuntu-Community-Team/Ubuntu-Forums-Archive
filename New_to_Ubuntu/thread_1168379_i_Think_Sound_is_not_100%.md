---
title: "i Think Sound is not 100%"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-24
Hi There.

I have installed uBuntu 9.04, sound was on out of the box but i think its not 100% because when i play the same songs in iTunes or Media Player in Windows , its sound is far loud and better than when i play the same song in RhythmBox or any other Audio Player in uBuntu.

Any Solution to this?? Same is happening with my Video File's sound.

---

### Post by mevets on 2009-05-24
try running 'alsamixer' from the commandline and bump up the master volume

---

### Post by Didius Falco on 2009-05-24
> **raziiq said:**
> Hi There.

I have installed uBuntu 9.04, sound was on out of the box but i think its not 100% because when i play the same songs in iTunes or Media Player in Windows , its sound is far loud and better than when i play the same song in RhythmBox or any other Audio Player in uBuntu.

Any Solution to this?? Same is happening with my Video File's sound.

Hi,


Have you opened the volume control on the panel and turned it up? Right-click it and go to **Open Volume Control** and set up all the volume controls that apply and adjust them. That will probably take care of it right there - mine started out at 80%, until I turned it up.

If that doesn't do the trick, make sure the volume is turned up in the applications you are using. (Just trying to cover all the bases...)

One last step, if the above doesn't do it.  Open a Terminal shell (**Applications/Accessories/Terminal**) and type ```
alsamixer
``` and make sure the volume is set properly there as well. You navigate that by using the left+right arrow keys to move from one control to the next and the up+down keys to set the volume level. The "M" key mutes/unmutes specific controls.

I hope this helps...

Regards,

Didius

---

### Post by nandemonai on 2009-05-24
Personally, I've noticed this since using Linux period. Sound is never as loud on Linux for whatever reason. I often get greeted with a blaring loud Windows login sound when I want to get some gaming time in because I've forgotten to turn down my home theater after being in Ubuntu. 
Generally it's worse with internal sound than a card I've found.

I have my doubts as to whether the quality is up there too. All comes down to the difference in drivers I'm guessing.

---

### Post by fillintheblanks on 2009-05-24
Try setting analog mix, wave, front, master and various other channels to maximum

---

### Post by ubername on 2009-05-24
> **nandemonai said:**
> Personally, I've noticed this since using Linux period. Sound is never as loud on Linux for whatever reason. I often get greeted with a blaring loud Windows login sound when I want to get some gaming time in because I've forgotten to turn down my home theater after being in Ubuntu. 
Generally it's worse with internal sound than a card I've found.

I have my doubts as to whether the quality is up there too. All comes down to the difference in drivers I'm guessing.

Very much the same here, on two different Dell systems, both with internal cards.

---

### Post by CatKiller on 2009-05-24
> **nandemonai said:**
> I have my doubts as to whether the quality is up there too.

It's pretty well established that, due to a couple of psychoacoustic effects, listeners will feel that louder music sounds better than quieter music, even if the actual music is exactly the same. I don't think that you can assume that the quality isn't the same when you've already established that the volume is different.

---

### Post by nandemonai on 2009-05-24
> **CatKiller said:**
> It's pretty well established that, due to a couple of psychoacoustic effects, listeners will feel that louder music sounds better than quieter music, even if the actual music is exactly the same. I don't think that you can assume that the quality isn't the same when you've already established that the volume is different.

True. But I do actually adjust the volumes so they are roughly the same via an amplifier, depending whether I'm in Windows or Ubuntu.

I do notice however that the clarity just seems better under Windows for my particular sound chip on this board.

```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
```

*shrugs*

This isn't exactly a music production machine, as you can tell from the sound chip I'm using so it's no biggie for me. Just observations.

---

### Post by CatKiller on 2009-05-24
> **nandemonai said:**
> True. But I do actually adjust the volumes so they are roughly the same via an amplifier, depending whether I'm in Windows or Ubuntu.

I do notice however that the clarity just seems better under Windows for my particular sound chip on this board.

Don't get me wrong, it could well be that it sounds different. As you say, the driver is different between the two and there could be all sorts of EQ, reverb or other jiggery-pokery going on in the Windows driver to change the sound. It's just that without some serious calibration and an immediate A/B test, you can't tell for sure.

---

### Post by raziiq on 2009-05-24
thanks for the help guys, i ll check these recommendations and post my feedback

---

### Post by kansasnoob on 2009-05-25
I always install gnome-alsamixer either from Synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video:

[ATTACH]115043[/ATTACH]

Lots of toggles and buttons to play with!

---

### Post by Bruce S on 2009-05-25
[QUOTE=Didius Falco;7336396]Hi,


Have you opened the volume control on the panel and turned it up? Right-click it and go to **Open Volume Control** and set up all the volume controls that apply and adjust them. That will probably take care of it right there - mine started out at 80%, until I turned it up.

Thanks Didius Falco,

Checked on my Volume Control, found my volume was set very low on my centre speaker.

Volume now set to high , and the sound works better than it has for months.
All is now well with Ubuntu.

):P

---

### Post by raziiq on 2009-05-25
its all set well for me, but still the sound is not desirable. Also i noticed that youtube's video sounds are really pesky, they are really low.

I ll download n install the recommended alsamixer and will post my feedback

---

### Post by raziiq on 2009-05-25
> **kansasnoob said:**
> I always install gnome-alsamixer either from Synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video:

[ATTACH]115043[/ATTACH]

Lots of toggles and buttons to play with!

i have installed gnome-alsamixer but it is a blank window. When i click Edit>Configure sound card; the program quits.

somebody help??

---

### Post by raziiq on 2009-06-03
alright i have got that alsa-mixer to work but still the sound is really low, i have all the controls set to 100% but still the sound is annoying

---

