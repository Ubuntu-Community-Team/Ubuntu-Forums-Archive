---
title: "Sound not working?"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-01-05
OK, I have a BIG problem. I cant hear any sound!!! I go to: System/Preferences/Sound and change it every time I hit test but it dose not work!!! This is what I get for what I think is the correct driver:

[IMG]http://taylorthomas.weebly.com/uploads/5/0/3/2/503275/screenshot.png[/IMG]

Please HELP!!!:P:(

---

### Post by eagle416 on 2009-01-05
try this:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by taylor102387 on 2009-01-05
That did not work. :( Anything else?

---

### Post by orlox on 2009-01-05
This simple and short guide helped me make the audio on my laptop work.

[http://ubuntuforums.org/showthread.p...d.php?t=843012](http://ubuntuforums.org/showthread.p...d.php?t=843012)

---

### Post by 2hot6ft2 on 2009-01-05
First you need codecs to play that see the highlighted part.

Intrepid 8.10 uses PulseAudio on top of alsa so going directly to your sound card wont work.
Sound being set to 0 is a known bug in intrepid.

Try the first link for fixing pulse first since it has the fix for it being set to 0. [COLOR="Blue"][B]Also you need codecs to play most multimedia which is covered close to the bottom or use this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.[/B][/COLOR]


Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
A short version here. I suspect it will be modified.
[http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

There are more but this gives you some alternatives that are being used.
--------------
no sound
Do you have all the needed codecs to be able to play sound?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
if so and you still have no sound try these maybe one will help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by abn91c on 2009-01-05
what do you get with aplay -l

---

### Post by taylor102387 on 2009-01-06
device_list:215: no soundcards found...

---

