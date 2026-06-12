---
title: "Login sound disappeared"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Torp3x on 2011-03-30
Title says it all, suddenly the login sound has disappeared. I still get the funky little bongo drumroll when I select a user, but after that it's silent. Up until now I've had the default login sound. Haven't changed a single setting to do with sound.

Wha....???

---

### Post by Torp3x on 2011-03-31
Anyone have any idea where to look to start fixing this? Every setting points to it theoretically playing the default login sound, but in practice it does not. 

It just happened spontaneously too.

Maverick.

---

### Post by Torp3x on 2011-04-01
Nobody has any ideas how to fix this? It behaves correctly with a different user profile.

I don't care about the login sound but if it's not working then something is broken somewhere....

---

### Post by dniMretsaM on 2011-04-01
System -> Preferences -> Startup Applications -> GNOME Login Sound.

---

### Post by Torp3x on 2011-04-01
Yeh that's the thing, everything I know of that manages the login sound is enabled to play the login sound. It's enabled in user privileges, Gnome login sound, sounds are enabled, the volume is up etc etc.

There must be an associated filesystem or user config that's stopping it from playing.

---

### Post by dniMretsaM on 2011-04-01
Hmm... You could download the original sound file and replace the one that doesn't appear to work. I believe the places to change it are

Administration -> Login Window -> Accessibility

Preferences -> Sound -> Sounds.

If nothing else you could restore the default settings and that should turn it back on.

---

### Post by Torp3x on 2011-04-01
```
locate "desktop-login"
```*file not found*


```
locate desktop-login
```/usr/share/sounds/ubuntu/stereo/desktop-login.ogg

Hmmm..... now the command in 'Gnome login sound' starts with 

```
/usr/bin/canberra-gtk-play --id="desktop-login"
```So I removed the "" and now the sound plays at login. However, logged in as a different user, the command finds the file regardless of whether it is in "" or not. Go figure!

Ubuntu - The Windows Vista Of Linux?

---

