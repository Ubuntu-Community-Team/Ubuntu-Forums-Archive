---
title: "After installing ubuntu-restricted-extras login sound disabled"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by burcs on 2011-03-15
I installed ubuntu-restricted-extras, and rebooted and now the login sound is not playing. The initial prompt sound plays, but after entering password and logging on that sound doesn't play, nor does the log off prompt sound when I shut down. 

Searching around, and not sure if this info is outdated or not, but some threads refer to /etc/gdm/gdm.conf, but I don't have a gdm.conf, only a custom.conf and gdm.schemas. Any ideas? Thanks.

ubuntu 10.04, HP Mini 110

---

### Post by maqtanim on 2011-03-15
From the top panel go to **System > Preferences > Sound**. Check that whether **Ubuntu** is selected as the default sound theme.

---

### Post by burcs on 2011-03-15
> **maqtanim said:**
> From the top panel go to **System > Preferences > Sound**. Check that whether **Ubuntu** is selected as the default sound theme.

It is. And the login screen preferences is checked to play a login sound. The only that changed between it working and not working was installing the restricted extras. Uninstalling restricted extras didn't re-enable it, either.

I should add this has happened on every machine I've installed Ubuntu on, just never realized until now that installing the restricted extras is what made it stop playing the login sound.

---

### Post by burcs on 2011-03-16
I've also checked **System > Preferences > Startup Applications > Gnome Login sound**, and it is checked, and is pointing to

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```

I've tried changing that to point directly to the file with --file="path.to.file/file.ogg" but still didn't play. Have also checked the sound file itself with the default media player and vlc, and doesn't seem to be corrupt or anything.

Is there a script or config file somewhere I can check that's supposed to say "after login, play this sound"?

---

### Post by burcs on 2011-03-22
Any other ideas I can try?

---

