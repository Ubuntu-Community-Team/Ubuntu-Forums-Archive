---
title: "How to use the audio disk burner"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Irish1 on 2009-05-16
I'm trying to use the Brasero disk burner to make an audio CD but it doesn't seem to want to burn.  I can copy a DVD, make a data CD, but when I get to the burn stage for an audio CD nothing happens after I get the message 'Normalizing Tracks', there's just an orange bar move back and forth on the screen.  Any thoughts?  Is it the settings?

---

### Post by logos34 on 2009-05-16
what format are the tracks in?  Maybe it can't convert because the right codecs aren't installed (i.e. mp3)??

sudo apt-get install ubuntu-restricted-extras

[edit]

---

### Post by Irish1 on 2009-05-16
They are all Mp3 files, and I'm not sure if I have the right codecs.  I entered the code suppled by logos34 and got the message couldn't find ubuntu extras.  How do I get codecs for various file types?

---

### Post by logos34 on 2009-05-16
sorry, typo, I left out 't' in 'restricted'.  copy and paste again

---

### Post by Irish1 on 2009-05-16
The codecs were great, I uploaded those no problem.  I am still, however, having the same issue with Brasero - the Normalizing Tracks message continues to appear as the orange bar moves from left to right on the screen.

---

### Post by kostkon on 2009-05-16
Maybe the normalising of the tracks takes time or is not working for some reason. The thing you could do is to disable the *Normalise* plugin.

Go to *Tools &#8594; Plugins* (I think) and disable the plugin.

Hope that helps.

---

### Post by zvacet on 2009-05-17
Burn them as data and you will be fine.

---

### Post by logos34 on 2009-05-17
> **zvacet said:**
> Burn them as data and you will be fine.

as long as the O.P. has a dual CD + MP3 Player...didn't mention that, though

---

### Post by eric71 on 2009-05-20
This is a reported bug that has now been kicked upstream to the Brasero developers. All you can do for now is disable the normalizing plugin. Then audio cds will burn, just with uneven volume.

---

