---
title: "DVD decoder"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by sctb082552 on 2008-12-20
Ok, so I have 8.10 installed and my internet working good. I hope I don't anoy anyone with all my questions.

I need to find a DVD decoder or codec, something like that to may my dvd play movies.

Where to start, Thanks for any help you can provide.:confused:

---

### Post by mapes12 on 2008-12-20
Go [here]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by ibizatunes on 2008-12-20
This will help fix your issue

[http://www.medibuntu.org/](http://www.medibuntu.org/)

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

You need mediabuntu to decode dvd

k9copy that is in add\remove is a good program to copy dvds

---

### Post by MyR on 2008-12-20
These commands will allow you to play DVDs and other nonfree formats. More info at [http://www.medibuntu.org/](http://www.medibuntu.org/)
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
sudo aptitude update && aptitude install medibuntu-keyring && aptitude update
sudo aptitude install w32codecs libdvdcss2
```

You can also install the following media player. More info at [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
```
sudo aptitude install vlc
```

Please note that these codecs are restriced by copyright/other legal stuff in certain countries

peace

---

