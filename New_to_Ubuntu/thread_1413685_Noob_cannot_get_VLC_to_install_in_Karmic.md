---
title: "Noob cannot get VLC to install in Karmic"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Zerxez on 2010-02-22
Hi,
This is probably easy and obvious to someone.  I know it is just something basic, but...
I have spent three days trying to get VLC installed and done more forum and google searches than I can count.

All I want to do is install VLC media player.  So far there is always a dependency problem and it doesn't install.  I have tried installing from the package manager and from the terminal.  I enabled the medibuntu repositories.  I tried to install vlc-nox both ways and from a tarball.

What am I missing?  Is there some repository or ?

---

### Post by dmaxel on 2010-02-22
Which Ubuntu version are you using?

---

### Post by NightwishFan on 2010-02-22
Are you using the standard Ubuntu repositories or a PPA to install VLC? If you have the standard ones, try:
```
sudo aptitude update && sudo aptitude install vlc
```

---

### Post by Zerxez on 2010-02-24
Hi,
I am running Karmic.
Thank you Nightwishfan, I entered those commands and it seemed to get me a bit farther.  However the problem persists.  From my web searches is may be that I don't have a "multiverse" in my sources list...but being a noob I don't know how to do that.  I followed a couple guides to add medibuntu, but that didn't help.  When I ran your commands it seemed to perform the install then it said it had problems and did I want to use the solution so I hit y and then it deleted some items said it would leave old versions in place and then still came up with broken dependencies.

---

### Post by NightwishFan on 2010-02-24
If you have the standard Ubuntu, just go to Administrator -> Software Sources and make sure the first four boxes are checked in the the first tab.

---

