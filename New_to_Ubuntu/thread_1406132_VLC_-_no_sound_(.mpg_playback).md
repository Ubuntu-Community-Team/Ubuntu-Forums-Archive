---
title: "VLC - no sound (.mpg playback)"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Julita on 2010-02-13
Hi! I have this problem with .mpg file. With SMplayer there are no problems, so I guess I have to configure VLC. The question is - how? Or are there additional libraries that I need to install? Please help.

---

### Post by chewearn on 2010-02-14
Check under VLC Audio Preferences.  There might be a misconfigured setting that cause no audio.  E.g. "enable audio" is unchecked (d'oh! :mrgreen:) or "Use SPDIF when available" is checked.

---

### Post by Julita on 2010-02-14
I have done that, to no avail. I have contacted the developer and he has said that the file is a non-standard, and VLC would play only a definite .ts format. It appeared that only (S)MPlayer would play it. Kaffeine and KMplayer would not. It's the file issue...

---

### Post by chewearn on 2010-02-14
Okay, if you know what the unsupported format is, please post to help people who stumble into this thread in the future.

Also, please mark this thread as solved, thank you.

---

### Post by Julita on 2010-02-14
It is advisable to run VLC *file* in the terminal to see the problem. If VLC indicates errors about its incompatibility with the file because of the "wrong" ISO standard, then the problem is within a file.

---

