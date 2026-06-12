---
title: "No Audio Output on Ubuntu 9.10 Acer Aspire 9805"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by A Student Philosopher on 2010-02-12
I'm using Karmic on an Acer Aspire 9805.

My problem is no matter what options I mess with weather Youtube video, Rythembox or vlc player I can't get a sound out of this laptop. Not even that nifty wind and drums startup noise.

I've messed with the sound preferences and looked around on this forum and the web to so far, no avail.

Can anyone point me towards some drivers or tell me if I'm missing something obvious?

---

### Post by mwcrowley on 2010-02-12
Has it worked before with other ubuntu releases? or in windows?  
I did a search and didn't find anything under acer.  Make sure pulse audio is installed.  As a laptop it has an integrated sound card.  I would do a search for issues with that integrated sound card.

---

### Post by A Student Philosopher on 2010-02-13
It's worked fine on Windows Xp and Vista.

I've installed pulse audio now with no change, messed around with the configuration but nothing.

My sound card: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

In searching I found [one similar but unsolved case]("http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller").

Also I've noticed a peculiar buzzing sound coming from the speakers of this laptop. It goes silent when I play anything that is supposed to make noise. This makes me think that it sees the card but is having driver issues.

---

