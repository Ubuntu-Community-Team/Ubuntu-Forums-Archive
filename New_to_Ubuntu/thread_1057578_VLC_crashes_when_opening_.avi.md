---
title: "VLC crashes when opening .avi"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2009-02-01
When I right-click on an .avi video and choose "open with VLC", VLC opens for a second and then crashes.  I can play .avi's with Movie PLayer just fine.  I also noticed that when I open VLC (applications>>sound/video>>VLC) it opens fine, but when I try to open an .avi file from within VLC (media>>open file) there is no .avi file in the folder where I saved it.  It's as if VLC doesn't recognize .avi's.  What should I do?? Thank you.

---

### Post by spcwingo on 2009-02-02
Have you tried removing and reinstalling vlc?

```
sudo apt-get remove vlc
```

then

```
sudo apt-get install vlc
```

If that doesn't work then try renaming your .vlc folder in /home/yourname/

---

### Post by Crafty Kisses on 2009-02-02
You may want to purge VLC to remove anything that was associated with VLC as well:
```
sudo apt-get remove --purge vlc
```

---

### Post by FAMUgolfer on 2009-02-02
Nadda. I still can't open or view avi's from the folders I stored them when opening VLC.  And when I right-click on an avi to open with VLC specifically, VLC shows up for about a half second and then crashes (disappears).  Any other suggestions?

---

### Post by spcwingo on 2009-02-02
You can try:

```
sudo apt-get install --reinstall vlc libwxgtk2.6-0 libdvbpsi4 libxosd2 libvlc0 vlc-nox libwxbase2.6-0 libiso9660-5 vlc-plugin-pulse libmodplug0c2 libtar libvcdinfo0 libebml0 libmatroska0 libsdl-image1.2
```

This will just reinstall vlc and all of it's dependencies.  If this doesn't get it, just hang out until someone a little more skilled comes along.

---

### Post by FAMUgolfer on 2009-02-02
thanks for the help but same thing happens:(

---

### Post by mikechant on 2009-02-03
Run vlc from the terminal and you should get some error messages to post here.

I expect the command is just

vlc yourfile.avi

Then copy & paste any error messages to here (note that Copy in the terminal is Cntl+Shift+C if you haven't come across this)

---

