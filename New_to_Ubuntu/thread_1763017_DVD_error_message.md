---
title: "DVD error message"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by ndex477 on 2011-05-19
Posted a thread  earlier re: Trying to play a dvd and am still not getting anywhere with successfully playing one of my DVDs.

The error message that I get when I insert a DVD is: Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed. What is a DVD decryption library and how do I install one?

Thanks

---

### Post by kiwiluver75 on 2011-05-19
1.First, if you do not have the medibuntu repository, install it by typing this in the terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
If you already have medibuntu skip to step 2.

2. Get dvd support(only after getting medibuntu) by typing this in the terminal
```
sudo apt-get install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh
```

Hopefully this helps.

---

### Post by ndex477 on 2011-05-19
Does this allow you to view DVDs? because i've typed all kinds of stuff into the terminal and since i'm new to Linux, I don't know what any of this stuff i'm typing is.  I'm trying to view my DVDs using Movie Player. Will these commands help me accomplish that?

I was informed to get extras using: sudo apt-get install ubuntu-restricted-extras.

---

### Post by wildmanne39 on 2011-05-19
> **ndex477 said:**
> Does this allow you to view DVDs? because i've typed all kinds of stuff into the terminal and since i'm new to Linux, I don't know what any of this stuff i'm typing is.  I'm trying to view my DVDs using Movie Player. Will these commands help me accomplish that?

I was informed to get extras using: sudo apt-get install ubuntu-restricted-extras.
HI, go here and follow the guide carefully and you will have dvd playbaqck,mp3,flash video playback, be able to copy cd and dvd, make sure you read the whole page carefully and use the version that is for the version of ubuntu you are using.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

