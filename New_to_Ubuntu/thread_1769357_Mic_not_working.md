---
title: "Mic not working"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by ff-addict on 2011-05-27
I just upgraded to 11.04 Natty Narwhal a few days ago, now the microphone on my webcam isn't working. It shows up in the sound preferences, but I can't get it to work. Help?

---

### Post by papibe on 2011-05-27
Try to unmute them with [alsamixer]("http://alsa.opensrc.org/Alsamixer"). Check [this]("http://www.patheticcockroach.com/mpam4/index.php?p=62").

Run it like this:
```
$ alsamixer
```
Unmute the speakers, test them. When you get the results you're going for, save the settings like this:
```
$ alsactl store
```
Regards.

---

