---
title: "[SOLVED] xubuntu vnc currently running session"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by Skooj on 2008-03-17
Hello.

I recently setup xfce on my main ubuntu (gutsy) install as gnome tends to suck up too many resources for my  linux box to handle. Upon doing this I found out that there is no remote desktop by default for xubuntu, so I followed this thread to install it: [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

The problem here, is that I need vnc to show me a session that is currently logged in on the machine, and not create a new one that runs through the vnc server. Basically, I want it to work like it does in the normal gnome ubuntu. How do I do this?

Any help is greatly appreciated.

EDIT:
figured out that I can run vino instead and it works fine, as can be seen here: [http://ubuntuforums.org/showpost.php?p=1108676&postcount=9](http://ubuntuforums.org/showpost.php?p=1108676&postcount=9)

---

### Post by chewearn on 2008-03-17
What you need is the same vnc server used by Ubuntu Gnome remote desktop feature, which is "vino".

Install the vino package:
```
sudo aptitude install vino
```Set-up preferences:
```
vino-preferences
```Then, add vino to the Xubuntu start-up (this is to fix a bug; vino is supposed to automatically start-up by itself after the vino package is installed, but did not)

Panel Menu > Applications > Settings > Autostarted Applications
Click +Add button; enter "vino-session" as the command.

---

### Post by Skooj on 2008-03-29
hehe, thank you, I forgot to post that I figured this out myself a few hours later. Thanks though =D

---

