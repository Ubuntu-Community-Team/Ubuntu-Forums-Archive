---
title: "cant play any media files"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by car49 on 2009-04-18
cant play any media files,
it comes up saying
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument


im new to this software, can anyone help?

---

### Post by Michael.Godawski on 2009-04-18
hi,

when you go to System > Preferences > Sound what are the options set there? Can you test successfully? 

If you change to ALSA does it go better?

---

### Post by stoogiebuncho on 2009-04-18
Occasionally when you have different programs trying to use the sound card at the same time it can cause conflicts.  Try closing all programs that are using sound, and then open just the one you want.

It's annoying, but sometimes it works.

---

