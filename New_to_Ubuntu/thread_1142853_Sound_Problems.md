---
title: "Sound Problems"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by koldphlame on 2009-04-29
My usb driven speakers play sound but only as **_[COLOR="Red"]loud[/COLOR]_** as they can there's no control over the sound :confused: and they only work with the music on my harddrive they will not play any thing from the internet youtube, etc.

Could someone help me to fix or lead me in a direction to fix this problem:mrgreen:

---

### Post by kansasnoob on 2009-04-29
What version of Ubuntu are you using? I know your sig says Hardy but I need to know for sure.

Regardless, one thing I'd do to start with is install gnome-alsamixer either from synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Lots of toggles there.

This guide has been a lifesaver to me in the past:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

What happens when you click on the volume applet in the panel?

---

### Post by windfix on 2009-04-29
Thanks, KansasNoob.  The gnaome-alsamixer let me find my audio problem in seconds.  I had accidentallyh turned on analog loopback yesterday while trying to get my headset microhpone working, and unhappily discovered that I had no sound afterward.  Great suggestion, hopefully works for the guy/gal that started this thread too!

---

