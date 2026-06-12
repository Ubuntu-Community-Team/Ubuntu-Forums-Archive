---
title: "Ubuntu, as you know, is not as loud as Windows. Is there a util to boost volume?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Ubunser on 2010-05-12
Need a util like volume control but twice as powerful!!!

---

### Post by ENigma885 on 2010-05-12
You've got to check [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1308838")!

But if you need a quick answer, it's an equalizer for PulseAudio. (PulseAudio is the soundserver in Ubuntu since 8.04)
You can download the package from [[COLOR="Blue"]HERE[/COLOR]]("https://launchpad.net/~psyke83/+archive/ppa/+files/pulseaudio-equalizer_2.7_all.deb"). 
And if you prefer receiving further updates for this equalizer, you can add Psyke83's ppa (the equalizer maintainer). Simply, 
[LIST=1]
[*]open a terminal window (*Applications>Accessories>Terminal*)
[*]paste 
```
sudo software-properties-gtk --enable-ppa=psyke83/ppa
```
[*]enter ur password when prompted (You won't see anything being written)
[*]press *Enter*
[/LIST]

---

### Post by kostkon on 2010-05-12
> **Ubunser said:**
> Need a util like volume control but twice as powerful!!!
First of all, install *gnome-alsamixer*. This utility will give you access to your hardware volume levels.

Also, you could install the *PulseAudio Device Chooser* utility and use the pulseaudio volume control.

---

### Post by ubunterooster on 2010-05-12
Go to system>preferences>sound.
There the volume has a 100% level but can go to 150% near the top of the window

---

### Post by uRock on 2010-05-12
> **Ubunser said:**
> Need a util like volume control but twice as powerful!!!
Really? ubuntu blasts when the master volume is turned up.

---

### Post by banerjeerupak on 2010-05-12
What do you mean by Ubuntu not being as loud as Windows. With my system, i have found that Ubuntu brings out higher decibels. The last time i checked was with 8.10. So can't comment on the newer versions.

---

### Post by ubunterooster on 2010-05-12
> **banerjeerupak said:**
> What do you mean by Ubuntu not being as loud as Windows. With my system, i have found that Ubuntu brings out higher decibels. The last time i checked was with 8.10. So can't comment on the newer versions.
It is not as loud (by default) on all of the 3 laptops I have used

---

### Post by Ubunser on 2010-05-13
> **ENigma885 said:**
> 
You can download the package from [[COLOR="Blue"]HERE[/COLOR]]("https://launchpad.net/~psyke83/+archive/ppa/+files/pulseaudio-equalizer_2.7_all.deb"). 


I got a problem, look please...

---

### Post by Ubunser on 2010-05-13
And also some other errors like the following.

---

### Post by 3rdalbum on 2010-05-13
What version of Ubuntu are you using, and have you got the repositories enabled in Software Sources?

---

### Post by Ubunser on 2010-05-13
> **3rdalbum said:**
> What version of Ubuntu are you using, and have you got the repositories enabled in Software Sources?

I am using 9.04 and here's a screenshot of what you asked.

---

### Post by ENigma885 on 2010-05-13
Unfortunately, there's no source for 9.04. The available sources in [[COLOR="Blue"]the PPA page[/COLOR]]("https://launchpad.net/~psyke83/+archive/ppa/?field.series_filter=lucid") are for 10.04, 9.10, 8.04, and 8.10. And personally, I don't recommend adding a PPA for a different Ubuntu version than urs.

However, u still have an upgrade option to Lucid or Karmic.

---

