---
title: "video format 0x7 problems"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by jimwill on 2011-06-12
On some video's (avi's for one) I cannot get kaffeine to play them. It just says 'codec already installed' and stops. 
With mplayer I get 'Cannot find codec matching selected -vo and video format 0x7" then proceeds to play the audio with a black video. 
However in winxp running mplayer the video plays with no problem!??

Other video's from the same source and same type, play on kaffeine just fine!

What am I missing?
Running kubuntu 8.04.4. with all updates I know about installed.

---

### Post by VOT Productions on 2011-06-12
First of all, you should upgrade to 10.10 or 11.04. There were so many advances in the next few versions.
As for the problem, you probably have either a faulty copy or you have to install restricted extras using the terminal: **sudo apt-get install kubuntu-restricted-extras.**

---

### Post by jimwill on 2011-06-12
> **VOT Productions said:**
> First of all, you should upgrade to 10.10 or 11.04. There were so many advances in the next few versions.
As for the problem, you probably have either a faulty copy or you have to install restricted extras using the terminal: **sudo apt-get install kubuntu-restricted-extras.**

I don't like the KDE 4.0+ desktops, I prefer the KDE 3.5. I have installed trinity on my laptop and it seems to work ok (haven't tried the video's on it yet). (may get brave and install trinity on my desktop computer!)

I will try the restricted extras - - -thanks!

---

### Post by VOT Productions on 2011-06-12
I think you can downgrade to KDE 3.5 if you use the right tools.

---

### Post by jimwill on 2011-06-12
Ok, I did the **sudo apt-get install kubuntu-restricted-extras** but still have the same errors.:(

I have in the past installed some of the codec packages from the repository. Can anyone recommend what I may have missed?

running kaffeine from terminal I get:
> kaffeine: ERROR: KXineWidget: No codecs to handle media
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)


"not stable yet"???

---

### Post by jimwill on 2011-06-16
Ok, not a fix, but a work-around. I installed format factory ( [http://format-factory.en.softonic.com/](http://format-factory.en.softonic.com/) ) under wine and convert the non-playable avi's to mp4's, which play fine in kaffeine. 
I will go ahead and mark this as solved (altho it isn't) in the hopes that anyone else having this problem can use the work-around until a real fix comes along.

---

