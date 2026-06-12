---
title: "how to I install java for Google Chrome"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by TheAJGman on 2011-03-03
hi how to I install java for Google Chrome

---

### Post by maqtanim on 2011-03-03
I don't think you need to install java for Chrome separately! I use Chromium, and whatever I can remember, I didnot install any java for the chromium separately...

---

### Post by NCLI on 2011-03-03
Just install the "Ubuntu Restricted Extras" from the Software Center. That will install Java for all supported browsers.

---

### Post by TheAJGman on 2011-03-03
How would you do that via terminal

---

### Post by wojox on 2011-03-03
```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

---

### Post by I2k4 on 2011-03-06
I was similarly looking to install Java for Chromium (Lubuntu 10.10) and eventually found the "restricted" package in the Synaptics Package Manager.  (It's called "lubuntu-restricted-extras" there.) Java is necessary for at least one internet site I use regularly, and Lubuntu/Chromium causes a rejection, so I tried it.

But halfway through the process, the installation seemed to freeze for a long time, and the "details" showed it was downloading some Microsoft TrueType fonts (?) and it wanted an agreement to respect Microsoft's terms for use.  It just sat there waiting and I couldn't figure out how to agree to it.  The details screen seems to be display only.  Would this work better or differently using the terminal?  I'd give it another shot.

---

### Post by davidmohammed on 2011-03-06
I would agree with you - use the terminal

sudo apt-get install lubuntu-restricted-extras

since it sounds like you are using lubuntu.

---

### Post by clickit on 2011-05-28
> **davidmohammed said:**
> I would agree with you - use the terminal

sudo apt-get install lubuntu-restricted-extras

since it sounds like you are using lubuntu.

I've installed ...-extras but it didn't help :(
this [site]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1") keeps reporting : Oops! You don't have the recommended Java installed.

Chromium beta 12.0.742.68 (86550) on xUbuntu 11.04

thanks

---

### Post by Paqman on 2011-05-28
It's probably complaining that you don't have the Sun Java installed. That's fine, it does the same for me, and I have the OpenJDK version of Java installed and working fine.

---

### Post by wog on 2011-05-29
Actually, the version of Sun Java is old. The latest is 1.6.25, but the repositories only seem to have 1.6.24.

---

### Post by spcwingo on 2011-05-29
> **clickit said:**
> I've installed ...-extras but it didn't help :(
this [site]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1") keeps reporting : Oops! You don't have the recommended Java installed.

Chromium beta 12.0.742.68 (86550) on xUbuntu 11.04

thanks

Try testing it [[COLOR="Red"]here[/COLOR]]("http://bubblemark.com/").

---

### Post by undrline on 2011-07-28
> **I2k4 said:**
> I was similarly looking to install Java for Chromium (Lubuntu 10.10) and eventually found the "restricted" package in the Synaptics Package Manager.  (It's called "lubuntu-restricted-extras" there.) Java is necessary for at least one internet site I use regularly, and Lubuntu/Chromium causes a rejection, so I tried it.

But halfway through the process, the installation seemed to freeze for a long time, and the "details" showed it was downloading some Microsoft TrueType fonts (?) and it wanted an agreement to respect Microsoft's terms for use.  It just sat there waiting and I couldn't figure out how to agree to it.  The details screen seems to be display only.  Would this work better or differently using the terminal?  I'd give it another shot.

It sounds like you were using Synaptic.  You should be able to hit the tab key, and the <OK> will highlight red, then you can hit Enter.

---

