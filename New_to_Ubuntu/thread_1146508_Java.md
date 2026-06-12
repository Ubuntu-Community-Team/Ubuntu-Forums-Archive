---
title: "Java"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-05-02
In firefox at Youtube site the message says:

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player

How do I turn Java on? I prefer uisng Java applets to installing Flash, but will do so if java is not an option.

Thanks for help guys. :)

---

### Post by taurus on 2009-05-02
Have you installed Sun java?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.  And use the <- to highlight the Yes at the next page.

For flash, you need the flashplugin-nonfree.

---

### Post by Hospadar on 2009-05-02
Are you sure you have flash player?

search for flashplugin in synaptic, or go to a site that doesn't check for flash and follow firefox's prompt (I usually use xgen studios for this or maybe some other online flash game websites)

---

### Post by doas777 on 2009-05-02
ok, number 1, javascript != java. you do not need java to have javascript. it's part of your browser. you do need flash to show videos though, so lets install that:
```
sudo apt-get install ubuntu-restricted-extras 
```that will install a large number of handy packages that you take for granted on windows, like sun's java, adobe's flash, some vlc codecs, etc. you may also want to look at the medibuntu repositories for getting codecs, and dvd playback. 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) please be aware these packages may have encumbered licensing.

do you use noscripts in firefox? you need to allow the site in question to run javascript before flash will work correctly.

HTH

---

### Post by mayagrafix on 2009-05-02
Thanks doas and Hospadar, the CLI worked perfectly. I now can see the videos on you tube :)

---

### Post by MontelEdwards on 2009-05-02
> **doas777 said:**
> ok, number 1, javascript != java. you do not need java to have javascript. it's part of your browser. you do need flash to show videos though, so lets install that:
```
sudo apt-get install ubuntu-restricted-extras 
```that will install a large number of handy packages that you take for granted on windows, like sun's java, adobe's flash, some vlc codecs, etc. you may also want to look at the medibuntu repositories for getting codecs, and dvd playback. 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) please be aware these packages may have encumbered licensing.

do you use noscripts in firefox? you need to allow the site in question to run javascript before flash will work correctly.

HTH
Yeah i was looking at the second response and i was like 
"why dont you just have him install the extras"

---

