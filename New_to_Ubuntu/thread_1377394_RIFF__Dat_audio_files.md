---
title: "RIFF / Dat audio files"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by jermza on 2010-01-10
I'm in the process of migrating across from Windows and am busy putting Ubuntu to the test.  So far, it's playing my music and video files smoothly.

Except for .dat files.

In XP, VLC plays .dat files, but I see that Ubuntu's standard players don't.  I don't want to install VLC since I like the out-of-box apps.

Any ideas on how to make this work?

---

### Post by mk1w86 on 2010-01-10
You could try:

```
sudo aptitude install ubuntu-restricted-extras
```

which will install all non-free codecs etc. but I am not sure if that includes dat. :-k

---

### Post by 3rdalbum on 2010-01-10
"dat" is a file extension that means that the developer can't be bothered to think up a new extension. It's commonly used (originally used?) on VCDs. You can play VCDs in Totem Movie Player, but just don't try to play the files themselves because VCD doesn't work that way (it's not actually a data disc).

---

