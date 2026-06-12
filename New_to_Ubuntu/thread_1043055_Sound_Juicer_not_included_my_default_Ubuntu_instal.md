---
title: "Sound Juicer not included my default Ubuntu installation"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Free4Eternity on 2009-01-18
Hi guys. I am trying to rip my beloved Epica CD, and realised that Sound Juicer is not installed on my system. (Well, I did a system file search on the word 'juicer', and there are only two png images and a .desktop file) Then I tried to compile it from source. Terminal complained that libnautilus-burn is absent, even though I am pretty sure I installed it with a deb (since I couldn't find the source anywhere). Here are the logs btw:

```


configure:23040: $PKG_CONFIG --exists --print-errors "libnautilus-burn >= 2.15.3"
Package libnautilus-burn was not found in the pkg-config search path.
Perhaps you should add the directory containing `libnautilus-burn.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libnautilus-burn' found
configure:23043: $? = 1
configure:23058: $PKG_CONFIG --exists --print-errors "libnautilus-burn >= 2.15.3"
Package libnautilus-burn was not found in the pkg-config search path.
Perhaps you should add the directory containing `libnautilus-burn.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libnautilus-burn' found
configure:23061: $? = 1
No package 'libnautilus-burn' found
configure:23099: error: Package requirements (libnautilus-burn >= 2.15.3) were not met:

No package 'libnautilus-burn' found

```

Any help will be very much appreciated, and thanks in advance.

---

### Post by gandaran on 2009-01-18
> Then I tried to compile it from source. Terminal complained that libnautilus-burn is absent, even though I am pretty sure I installed it with a deb (since I couldn't find the source anywhere).
didn't you look first in add/remove or synaptic package manager for sound juicer and install it from there?

---

### Post by Dirjel on 2009-01-18
sudo apt-get install sound-juicer

I just did that a couple minutes ago, but I got rid of it in favor of goobox.

---

### Post by Free4Eternity on 2009-01-18
thanks guys. You see, I am a total noob. Anyway, I installed it from synaptic. For some reason, apt-get did not work on me.

---

### Post by midimarcus on 2009-01-18
What version of Ubuntu ar you using?

In 8.10 Intrepid Ibex, you can insert your Cd, open Rhythmbox and use the "Extract" button on top toolbar to rip all cd and save tracks in ogg audio (.oga) format.

---

