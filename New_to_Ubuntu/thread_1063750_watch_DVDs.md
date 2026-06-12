---
title: "watch DVDs"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by perito on 2009-02-08
what is a good program to watch DvDs?
I tried Totem Movie Player but it keeps saying An error occured, couldnt read from resource, while the Dvd movie works fine on windows.
thanks

---

### Post by m_duck on 2009-02-08
VLC is a good player```
sudo apt-get install vlc
```To play DVDs you need the libdvdcss2 package. The easiest way is to get it from the medibuntu repo. Check out [this wiki article](https://help.ubuntu.com/community/RestrictedFormats) about playing restricted formats and [here](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for DVD playback specifically. The medibuntu site is [here](http://www.medibuntu.org/).

---

### Post by carml on 2009-02-08
To use VLC,you also need to install ubuntu-restricted-extras or the G-streamer plugin,you can find them going to System->Administration->Synaptic package manager.Or try the suggestions on the previous post.:)

---

### Post by perito on 2009-02-08
Thank you a lot.
libdvdcss2 was the missing thing :)

---

