---
title: "No Sound in Xubuntu"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by GaryTheCat on 2011-06-01
Hi

I've just installed Xubuntu (10.04 &  restricted extras) on an old desktop for my son.

I can't get any sound out of it - any ideas?

Many thanks

---

### Post by frankbooth on 2011-06-01
You're not giving us enough to work with I'm afraid.

What kind of soundcard is in use?

Open a terminal (on the computer with Xubuntu) and write:
```

alsamixer

```
see if you've got anything muted by any chance.

---

### Post by I2k4 on 2011-06-01
There are many more informed users than me, but having experimented with several Desktop Ubuntu (10.04, 10.10, 11.04) and finally Lubuntu (10.10) versions that work fine on my laptop and netbook, I found Xubuntu had several problems that I just didn't bother myself trying to figure out.

It's up to you if you have some special reason to loooove Xubuntu, but for my purposes, if the OS version doesn't work, it's gone.  For an old PC, I really like Lubuntu 10.10 as being undemanding on resources and just plain working.

---

### Post by 4Orbs on 2011-06-01
Since it's an old computer it might be using OSS sound. So when you set your preferences in the sound settings, for the controls select OSS volume and MASTER volume. On my old p4 computer it's necessary to keep the OSS down below 75% to avoid distortion. The master can then be maxxed out.

---

### Post by Toz on 2011-06-01
> **I2k4 said:**
> There are many more informed users than me.....I'm not really sure how this reply helps the OP solve his sound problems.> **I2k4 said:**
> There are many more informed users than me, but having experimented with several Desktop Ubuntu (10.04, 10.10, 11.04) and finally Lubuntu (10.10) versions that work fine on my laptop and netbook, I found Xubuntu had several problems that I just didn't bother myself trying to figure out.My experience, on the other hand, is the opposite. I have 5 installs of Xubuntu on a variety of systems and they work flawlessly for me, whereas I had minor configuration issues with the other *buntu versions. All of which were solved when I put in the effort to look at them. This really boils down to preference and willingness to find a solution to the issues.

> It's up to you if you have some special reason to loooove Xubuntu, but for my purposes, if the OS version doesn't work, it's gone.  For an old PC, I really like Lubuntu 10.10 as being undemanding on resources and just plain working.The problem here is that all of the *buntus shares the same code base - the difference being the desktop environment and some DE-specific configuration changes. In all likelihood, a sound problem in Xubuntu will still exist in ubuntu, lubuntu, etc.

Everyone is entitled to their opinions, but I think the focus should be on providing GaryTheCat some tangible suggestions/answers to his sound problems.

@GaryTheCat, if you can provide us with some more information about your system, we can have a closer look at it. See this link: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") for a step by step guide to sound troubleshooting that can assist.

---

### Post by spcwingo on 2011-06-01
What is the output of this command when ran from a terminal:

```
aplay -l && lspci | grep Audio
```

---

