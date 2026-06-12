---
title: "Internal microphone not working, Thinkpad R61i"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by laffinet on 2009-11-08
Hi !

I'm recently did a fresh install of 9.10 Karmic in the hope that I finally get my internal microphone to work on my Lenovo Thinkpad R61i.
No luck. Everything else is fine, I can plug in an external mic and that works just fine, but I can't get the internal one to work.

lspci:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

Screenshot of alsamixer attached. I searched google high and low but so far haven't had any success.

Any ideas ?

---

### Post by laffinet on 2009-11-10
Bump.

---

### Post by jimmy the saint on 2009-11-10
That red one way at the right looks a lot like my input volume.  Try hitting F4 in alsamixer.  Sometimes input selectors show up there that don't show up in the main view.  First try turning up that red one on the right though.

---

### Post by laffinet on 2009-11-10
Thanks for the suggestions.
Problem is I can't turn up the red one on the right. I can navigate to it via the cursor keys but unlike the other ones, hitting "cursor up" doesn't do anything. 
F4 doesn't reveal any other controls either :-(

---

### Post by laffinet on 2009-11-10
Just noticed, the microphone does work, just at an incredibly low level. Yelling at it produces a barely noticable recording.
No idea how to get around that...

---

### Post by laffinet on 2009-11-11
bump

---

### Post by eagle416 on 2009-11-11
I am not totally sure about this, but I had similar issues recently. I notice there are 3 int mics. Select the one on the left (that has the [00] in green at the bottom) and hit spacebar. The red "CAPTUR" should jump to it, and it might assign capture properties to that control.

---

### Post by laffinet on 2009-11-12
> **eagle416 said:**
> I am not totally sure about this, but I had similar issues recently. I notice there are 3 int mics. Select the one on the left (that has the [00] in green at the bottom) and hit spacebar. The red "CAPTUR" should jump to it, and it might assign capture properties to that control.

I toggled capture for all sources, doesn't make a difference.

Also remember: the microphone is working, just at a very low level, which renders it useless.

I tried an external mic, works without a problem (always has).

---

### Post by empty_spaces on 2009-11-12
Your alsa-mixer screenshot seems to be missing the "Mic Boost" option.

Do a google search for "alsamixer mic boost" , there's a bunch of threads that you might find useful.

---

### Post by laffinet on 2009-11-15
Thanks for the tip. I did a lot of googling and reading, but haven't found a way to turn on the mic boost :-(

---

### Post by laffinet on 2009-11-16
bump

---

### Post by immeëmosol on 2010-01-17
On my Lenovo R61i 7650-D7G it probably won't work,
because there seems to be no internal microphone:
[http://forums.lenovo.com/t5/R-Series-ThinkPad-Laptops/No-internal-microphone-in-R61i-7650-8DU/m-p/7340](http://forums.lenovo.com/t5/R-Series-ThinkPad-Laptops/No-internal-microphone-in-R61i-7650-8DU/m-p/7340)

And on [http://lnv.lithium.com/t5/R-Series-ThinkPad-Laptops/R61i-7650-DHU-Does-it-have-internal-mic/m-p/116752](http://lnv.lithium.com/t5/R-Series-ThinkPad-Laptops/R61i-7650-DHU-Does-it-have-internal-mic/m-p/116752) it is said:
"If there is an internal mic there should be two tiny holes on the palm rest near the blue Fn key."

Sound not working is confirmed on the folloewing page as well:
[http://www.thinkwiki.org/wiki/Category:R61i#Sound](http://www.thinkwiki.org/wiki/Category:R61i#Sound)

These posts might be related and/or helpful :
[http://ubuntuforums.org/showthread.php?t=803361](http://ubuntuforums.org/showthread.php?t=803361)
[http://wernerroth.de/index.php/2007/11/13/kubuntu-710-on-a-lenovo-r61i/#comment-947](http://wernerroth.de/index.php/2007/11/13/kubuntu-710-on-a-lenovo-r61i/#comment-947)
  -  [https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

---

### Post by lev-unr on 2010-01-17
Have a similar issue and just solved it. 

1. go to terminal turn up all the mics in alsamixer

2. Go to sound setting make sure it is on mic 2 .. It said i had two mics (even though I only have one internal mic) Make sure it is on mic 2 instead of mic 1 and it should work like a charm. 

Hope this works for you. I did this on a ideapad s-10 2

---

### Post by laffinet on 2010-01-17
> **lev-unr said:**
> Have a similar issue and just solved it. 

1. go to terminal turn up all the mics in alsamixer

2. Go to sound setting make sure it is on mic 2 .. It said i had two mics (even though I only have one internal mic) Make sure it is on mic 2 instead of mic 1 and it should work like a charm. 

Hope this works for you. I did this on a ideapad s-10 2

Thanks, I will try that and report back here.

---

### Post by Arla on 2010-01-18
Depending on what you've done already.

Have you tried installing

linux-backports-modules-alsa-karmic-generic ?

You can find it if you turn on backports, it was the only thing that seemed to fix the internal mic for my Lenovo Y450, so might fix another Lenovo machine.

---

### Post by laffinet on 2010-01-18
> **lev-unr said:**
> 
1. go to terminal turn up all the mics in alsamixer


I can't turn the volume on the 2nd microphone up. I can select it, but I can't get it to change the volume.

---

### Post by laffinet on 2010-01-18
> **Arla said:**
> Depending on what you've done already.

Have you tried installing

linux-backports-modules-alsa-karmic-generic ?

You can find it if you turn on backports, it was the only thing that seemed to fix the internal mic for my Lenovo Y450, so might fix another Lenovo machine.

Tried that, didn't change a thing.:(

---

### Post by nbubis on 2010-01-22
Having the same exact problem on a Dell inspiron 1420n running Karmic. tried the suggestions in this post and in many others, but the recording volume is still incredibly low.

Any tips?

---

### Post by nbubis on 2010-01-22
Ok, seem to have solved this.

Open alsamixer (the 0 is for the first sound card on your machine):

[FONT="Courier New"]alsamixer -Dhw:0[/FONT]

In the "Playback" view, scroll to the "Digital Input Source" (using the left/right keys) and change it from "[Analog Inputs]" to "[Digital Mic 1]" (using the up/down keys).

Try using "sound recording" or "Audacity" to record.

Hope this saves someone else's head from being banged against the wall.

---

### Post by farchumbre on 2010-02-13
I tried that, but it is still not working in my x300

---

### Post by gradinaruvasile on 2010-03-04
I had a similar problem with a r61i. The solution was to :

1. in alsamixer set the capture devices and up the volume
2. select in the sound preferences "stereo duplex" profile for the internal sound card.

---

