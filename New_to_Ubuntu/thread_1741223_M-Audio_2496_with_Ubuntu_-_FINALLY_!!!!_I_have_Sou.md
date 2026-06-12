---
title: "M-Audio 2496 with Ubuntu - FINALLY !!!! I have Sound !!!"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by cynkronyze on 2011-04-27
Hi Folks,

Not being able to wait for advice, i reinstalled Ubuntu 10.10, then i searched the forums and found this link : -

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I followed every step as is, till step 4

Ran a music application in the background

Then i ran the command 

```
 alsamixer
```

Press F6 to choose the default Sound Card ( In My Case M-Audio 2496)

when the mixer page comes up, i turned up the levels on DAC & DAC1, 

Then i set the H/W & H/W 1 both to PCM OUT setting. (I guess you can tweak this to find something.)

And just then, these words came blaring through my Wharfedales...............

Do your demons - do they ever let you go
When you've tried - do they hide -deep inside
Is it someone that you know
You're a picture - just an image caught in time
We're a lie - you and I
We're words without a rhyme..............

DIO (R.I.P)
Rainbow In the Dark

- Cynkronyze

---

### Post by cynkronyze on 2011-04-27
P.S.....I have lost the ability to control volume through the volume icon on the task bar.......

---

### Post by stmiller on 2011-04-27
Yeah the sound applet doesn't work with this card. There is a cool interface for the controls though.

```
sudo apt-get install alsa-tools-gui
```

Then run:

```
envy24control
```

:)

---

### Post by Rogelio Atance on 2012-06-02
Hi
I've installed the audiophile 2496 on Ubuntu 12.04 LTS following the steps of 
 
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

It works, I have sound from the card, but I have problems with the entrance of sound, I don't know yet why. The window of the sound properties seems to have some problems when I try to choose one of the entrance options. It cracks all the times I chosee another option.
Any Idea why this?
Thanks,

---

