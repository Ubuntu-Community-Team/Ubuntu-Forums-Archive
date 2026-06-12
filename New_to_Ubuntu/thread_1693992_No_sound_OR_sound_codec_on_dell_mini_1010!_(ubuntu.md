---
title: "No sound OR sound codec on dell mini 1010! (ubuntu 9.10)"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by sheepo1 on 2011-02-23
Hi! So a couple of days ago I installed ubuntu 9.10 on my dell mini 1010. I installed video and wifi drivers and everything is going peachy, but I had one problem: I had no sound! I tried the guides here: [http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html ]("http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html")
and here: [http://ubuntuforums.org/showthread.php?t=1344172](http://ubuntuforums.org/showthread.php?t=1344172)
but I messed up on one of the guides and not only is sound not working, but it says I don't even have a codec directory when I enter this code! cat /proc/asound/card0/codec#* | grep Codec which is supposed to show your codecs. When I go to sound/hardware I don't get any options or drivers!

Does anybody know how I can get my codecs back and get sound? Thanks in advance!

---

### Post by jonny163 on 2011-02-23
Try going to the software centre and downloading the Ubuntu "restricted extras"
That should help

---

### Post by sheepo1 on 2011-02-23
I can't get altamixer to work either! it says command is not found. :(

---

### Post by sheepo1 on 2011-02-23
I reinstalled the restricted extras and it didn't work. :( thank you though.

---

### Post by Chris Edgell on 2011-02-23
How about sunjavadb-common

also you could look for:  flashplugins-nonfree-extrasound and flashplugin-installer

It would be nice if this would do the trick...it can't hurt.

Chris

---

