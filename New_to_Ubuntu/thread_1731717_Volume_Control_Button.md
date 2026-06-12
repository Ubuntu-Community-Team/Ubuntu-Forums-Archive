---
title: "Volume Control Button"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by mousestalker on 2011-04-17
How do I put a volume control button in my top panel for quick 'n easy adjustment of overall system sound volumes?

---

### Post by racie on 2011-04-17
Hmm... I think it should already be there, but...

Right click the panel, click "add to panel" or something like that, browse for the volume control applet, and you're done.

---

### Post by Frogs Hair on 2011-04-17
Drag the sound icon from preferences to the panel. or install the Alsa Mixer GUI from the software center and do as above. The Gnome Alsa Mixer will appear under sound & video.You can access the Alsa Mixer from the terminal without installing the GUI. 

```
alsamixer
```

---

### Post by Frogs Hair on 2011-04-17
As racie wrote you can access sound preferences from the speaker indicator on the panel . If it is missing , right click panel select add to panel and add the indicator applet.

---

### Post by mousestalker on 2011-04-17
@racie, that worked. Thank you!

---

### Post by dwhite on 2011-04-17
and don't forget usually one or more of your function keys are mapped to system volume, so you can just use your keyboard to change the volume, for me it is the combination;

Fn+F6 (that is the function key pushed at the same time as the F6 key) to raise the vol. and
Fn+F5 to lower the volume

---

