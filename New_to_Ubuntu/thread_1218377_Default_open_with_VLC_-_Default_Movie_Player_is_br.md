---
title: "Default open with VLC - Default Movie Player is broken."
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Doman on 2009-07-20
As the title suggests, my "Movie Player" is broken.  It glitches my screen like Wine when it starts and then continues to not perform well.  If I could un/reinstall it, that'd be awesome.  If not, how do I change my defaults all to VLC easily?

---

### Post by bramming on 2009-07-20
To reinstall go to system => administration => synaptic package manager. search for "totem", right click and uninstall. press apply, and then install it again.

To change vlc to default: right click a sound file with the extension you want vlc to open (like an mp3 song) and press Properties => Open With and choose vlc.

btw i dont have any clue why it doesnt work for you. Im not too good with the technical stuff, but i hope im still able to help ;)

---

### Post by john183 on 2009-07-20
You shouldn't have to uninstall totem, follow the last poster's instructions about opening synaptic package manager and finding totem. When you click on the box to the left of the package name you should get the install/uninstall options and near the middle or bottom there should be a re-install option. just use that one. it will save you a few steps.

---

### Post by ajgreeny on 2009-07-20
Just in case it's the configs of totem causing the problem, in synaptic do a "completely remove" and then either reinstall it or preferably, I think, choose totem-xine, which is a better version of totem, particularly for DVD playback.

---

### Post by ghostborg on 2009-07-20
I vote for VLC 1.0

---

### Post by CatKiller on 2009-07-20
> **ajgreeny said:**
> Just in case it's the configs of totem causing the problem, in synaptic do a "completely remove"...

"Completely remove" doesn't touch a user's Home folder, which is where many per-user configuration settings are stored. Especially for the kinds of programs that users may be tempted to re-install to fix.

---

