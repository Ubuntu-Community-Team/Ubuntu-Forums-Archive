---
title: "Movie player not working???"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by TheMustangZone on 2010-02-22
I just installed a fresh version of 9.04 on a co-worker's computer and everything works perfectly except for the movie player.  It will open on its own just fine, but when you try to play any kind of file with it, it immediately closes.  If you click on a .avi file, for example, it will open and then immediately close.  It does the same thing when trying a MP3 file.  All of the restricted extras are installed.  Any ideas?  Thanks.
 
Rob

---

### Post by anewguy on 2010-02-22
Is it safe to assume that when you say all restricted extras, you mean ubuntu-restricted-extras (or whatever it's called), plus all of the gstreamer good, bad, and ugly sets?  If not, try installing all of those first.  When it fails, try running from the command line with "mplayer" - that way you should see the failure codes in the terminal window.

Dave :)

---

### Post by rlj1965 on 2010-02-22
Use vlc + add restricted extras from synaptic

---

### Post by TheMustangZone on 2010-02-23
> **rlj1965 said:**
> Use vlc + add restricted extras from synaptic
 
The restricted extras are already installed.  What is VLC?  Can it be installed through the package manager?  Thanks again.
 
Rob

---

### Post by head2head on 2010-02-23
VLC is a media player that will play pretty much everything you throw at it :).

and yes, you can get it in the repos.

---

### Post by jsmnuk on 2010-02-25
> **head2head said:**
> VLC is a media player that will play pretty much everything you throw at it :).

and yes, you can get it in the repos.


VLC also is the only package I've found that plays both Blu-Ray audio and video files at the same time. But these command-line suggestions are very helpful.

---

### Post by Alexandre Putt on 2010-02-25
> **anewguy said:**
> try running from the command line with "mplayer"

Isn't he referring to totem?

---

### Post by corncob on 2010-02-25
I finally solved my problem by installing libdvdcss from synaptic.
[http://ubuntuforums.org/showthread.php?t=1388553](http://ubuntuforums.org/showthread.php?t=1388553)

---

