---
title: "silence in totem but sound in VLC?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2009-06-28
i'm having all sorts of issues with my sound lately, i've followed [this guide ]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html") and am now getting sound in VLC, but Totem (with Gstreamer) is still silent.

i'm all out of ideas, what could cause this? I would think they would both use the sound that ubuntu is configured for, but then either both or neither would have sound, what's VLC doing right that totem isnt?

---

### Post by PureLoneWolf on 2009-06-28
If I recall from a long time ago, VLC uses it's own internal codecs and not the system ones.

Try re-installing Gstreamer and make sure you have the ubuntu-restricted-extras package installed aswell - see if that helps

---

### Post by ~sHyLoCk~ on 2009-06-28
Check if you have the essential gstreamer codecs installed from synaptic.

---

### Post by Sonic Reducer on 2009-06-29
ok, i removed totem-gstreamer and installed totem-xine

Sound works on:
Audacious
Amarok 2
VLC
Rhythmbox
mousing over an audio file in nautilus

sound DOES NOT work on:
youtube
Totem (w/xine)

i'm going to purge everything totem and flash, then reinstall both. i'll report back with the outcome

.:EDIT:. yeah, no change. this is super lame, why does every release of ubuntu have something fundamental messed up? i wish the devs would stop trying to cram in new features and eye candy and focus on getting things like sound working

---

