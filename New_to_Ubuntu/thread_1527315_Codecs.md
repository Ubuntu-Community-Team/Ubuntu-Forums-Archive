---
title: "Codecs"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by MasterMind Karthik on 2010-07-09
Well guys,

Just asking... Does ubuntu have mp3, avi, mp4, flv and other codecs inbuilt? I mean, after installing Ubuntu 10.04, will I be able to play these formats without having to download and installing additional codec?

---

### Post by VeeDubb on 2010-07-09
I'm 99% sure the codecs you listed are all installed by default.

However, I do recommend getting the computer online at least once anyway.  There are plenty of other things like closed-source video drivers, flashplayer and acrobat reader which are not, and cannot be installed by default.

---

### Post by Darkness Des on 2010-07-09
That 1% chance comes back to bite me in my.... posterior.... every time, as it just did to you. You need 1 tiny little package called "ubuntu-restricted-extras". It's not preshipped with this because those formats can be illegal in some countries and this is an OS meant for the whole of planet earth.

---

### Post by audiomick on 2010-07-09
Hallo.
Des is quite correct: you need ubuntu-restricted-extras. This is available through the software centre or synaptic package manager.

There is also this:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Paqman on 2010-07-09
> **MasterMind Karthik said:**
> 
Just asking... Does ubuntu have mp3, avi, mp4, flv and other codecs inbuilt? 

Nope, but the first time you try to open one of those files it will prompt you to download what it needs. Or you can skip the codec issue altogether by installing ubuntu-restricted-extras as Darkness Des suggests.

---

### Post by VeeDubb on 2010-07-09
> **Darkness Des said:**
> You need 1 tiny little package called "ubuntu-restricted-extras".


Ah, good call.

It's been so long since I did a clean install on a system that wasn't hooked up to the net that I forgot about that.

On the upside, you can install that, and all of the bad/ugly gstreamer pluggins, and have virtually every codec available.

---

