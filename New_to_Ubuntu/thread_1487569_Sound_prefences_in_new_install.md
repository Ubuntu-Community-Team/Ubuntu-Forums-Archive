---
title: "Sound prefences in new install"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Maupertus on 2010-05-19
Dear all,

I did a clean install of Lucid, where I did upgrades from 8.04 till 9.10, during those releases, PULSE was implemented and I had to install some features to tweak it and get it working.

Now I believe I'm missing a couple of sound options, and when I click the Sound Preference option in my volume-panel-app, I don't get any actual preferences.

Can anyone recommend what to install to get some more control? I have looked in the Software Centre (and Rep) but I get a couple of (PULSE)options and don't want to mess it up.

Thanks!

---

### Post by mikewhatever on 2010-05-19
Do you mind elaborating on what should options you need? Does your sound input/output work? If so, perhaps it's best to leave it be. ;)

---

### Post by lidex on 2010-05-20
When you click "Sound Preferences" in panel volume control it opens "gnome-volume-control". Just make sure these packages are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common
```
Logout/in.
I wouldn't mess with anything else as *mikewhatever* points out.

---

### Post by Maupertus on 2010-05-24
Thanks guys, it's just that I have a the same problem in 10.04 that I had in 9.04 where every sound appears (even on low volumes levels in the main volume applet) continuously to be on a too high output for the speakers. In windows this problem does not occur. I remember that back with 9.04 I had to fiddle for ages with Pulse to get it right and I was looking into it when I realized the 'lack' (I agree with mikewhatever that it doesn't have to be a lack) of sound preferences.

---

