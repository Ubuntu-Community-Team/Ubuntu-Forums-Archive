---
title: "Strange error(s) when playing video clips"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-03-13
My default video player is Totem Movie Player (2.32.0). For some unknown reason, it doesn't play my wmv files any more. Instead, I get a dialogue box saying:
```
An error occurred
Internal data stream error.
```

It seems to play other formats of video though as normal.


I have a different but perhaps related problem when I try to play a video on gnome-mplayer (0.9.9.2). All formats of video play fine, but the first thing I get is a an error dialogue box saying:
```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
```

I have a bog standard laptop with the usual on-board Intel graphics card doo-dar. Why the heck would my system be searching for something related to nvidia??

---

### Post by Roger Allott on 2011-03-15
bump?

---

### Post by TeoBigusGeekus on 2011-03-15
[This]("http://forums.opensuse.org/english/get-help-here/multimedia/427063-gnome-mplayer-error-vdpau-backend.html") perhaps?

---

### Post by Roger Allott on 2011-03-15
> **TeoBigusGeekus said:**
> [This]("http://forums.opensuse.org/english/get-help-here/multimedia/427063-gnome-mplayer-error-vdpau-backend.html") perhaps?

Thanks. That certainly solves the problem with gnome-mplayer, but wmv files still don't play in Totem Movie Player.

---

### Post by TeoBigusGeekus on 2011-03-15
> **Roger Allott said:**
> Thanks. That certainly solves the problem with gnome-mplayer, but wmv files still don't play in Totem Movie Player.

Reinstall ubuntu restricted extras
```
sudo apt-get install --reinstall ubuntu-restricted-extras
```
and if that doesn't help, see [this]("http://forum.mandriva.com/en/viewtopic.php?t=130563").

---

### Post by Roger Allott on 2011-03-15
> **TeoBigusGeekus said:**
> Reinstall ubuntu restricted extras
```
sudo apt-get install --reinstall ubuntu-restricted-extras
```
and if that doesn't help, see [this]("http://forum.mandriva.com/en/viewtopic.php?t=130563").

Thanks, but neither of those solutions worked. I already had gstreamer0.10-ffmpeg installed. I reinstalled it anyway just in case, but still no luck with playing wmv files on Movie Player.

---

### Post by TeoBigusGeekus on 2011-03-15
Only thing I can suggest is (yes you guessed it) VLC.

---

### Post by oudalrich on 2011-03-26
I had the exact same problem and found the solution [here]("http://ubuntuforums.org/showthread.php?t=1006901"):

```
sudo ln -s /usr/lib/codecs /usr/lib/win32
```

No idea why it stopped working in the first place though.

---

