---
title: "Sound Coming From Actual Computer"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by SoulMazer on 2009-02-24
Well, I'd assume by the name of this forum that this is the place to ask this question. So, I have a problem where all sounds are played through both my speakers AND my actual computer. I would like to have sound only play through my speakers, as my computer has a rather cheap and low-range mini-speaker. I have tried going into Sound Preferences, however I have had no luck changing this no matter which device I select for sounds. In case it matters, I have "Infinity" brand speakers, however since the speakers DO actually work, I don't think I need a driver.

Any help is greatly appreciated. Thanks.

---

### Post by llamabr on 2009-02-24
In ubuntu, it's rarely a driver problem, contra windows.

Try alsamixer, and messing with the settings.  I know that the internal speaker is represented in there (but since i'm on a laptop, I can't test it).

Probably easy to adjust the settings with a song playing, so you can find the right one.

---

### Post by lindsay7 on 2009-02-24
Normally when you plug into the speaker jack on the computer the sound will only be played thru the external speakers.  Are you speakers for a computer with a built in amplifier? Also check to see if the minijack is pushed in all the way. If not you may be getting sound (low volume) thru both the internal and external speakers.

---

### Post by SoulMazer on 2009-02-24
The only 4 things that seem to affect anything at all are Master, PCM, Front, and Front Mi. I am guessing Front and Front Mi are not related to the speakers...so that leaves Master and PCM. When adjusting them, they both just seem to act as volume controls.

Any other ideas? Would messing around in my BIOS and possibly disabling the internal speaker work?

Thanks again.

---

### Post by jimmy the saint on 2009-02-24
check here.

[https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/12261](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/12261)

or here

[http://ubuntuforums.org/showthread.php?t=900898](http://ubuntuforums.org/showthread.php?t=900898)

Two likely solutions to your issue.

---

### Post by llamabr on 2009-02-24
```
Any other ideas? Would messing around in my BIOS and possibly disabling the internal speaker work?
```

You can disable the internal speakers?  I'd say that would work.

---

### Post by SoulMazer on 2009-02-24
@jimmy the saint: I tried both and no luck. Same problem.

@llamabr: Well I guessed wrong. Apparently you can't control an internal speaker via BIOS.

Well...are there any other options?

Thanks.

---

### Post by llamabr on 2009-02-24
This wouldn't be in bios.

Depending on how long you struggle with this, and how attached you are to the internal speaker, eventually putting a screwdriver on it and cutting the internal speaker will do the trick.

Tho, I'm sure there's a software solution first.

---

### Post by SoulMazer on 2009-02-24
Small update:

I have been reading around on Google for an answer and saw a way that I could blacklist my internal speaker....however this did not work. So...does anybody have any other ideas besides...the screwdriver?

---

### Post by llamabr on 2009-02-24
Don't rule out the screwdriver.

What did you do to blacklist it?  And what didn't work?  Any errors?

This is an interesting problem, as plugging in external speakers should short circuit your internal one.  It may be a hardware problem.

---

### Post by SoulMazer on 2009-02-24
To blacklist it, I went to the main "blacklist" file in /etc/modprobe.d and added the line: "blacklist pcspkr".

Yet, this didn't work.

However, I DID find a solution. I enabled my headphone jack and plugged in my old headphones. No more internal speaker!

Yet, if you do find another solution, I would appreciate not having a pair of headphones laying in the middle of my floor!

---

