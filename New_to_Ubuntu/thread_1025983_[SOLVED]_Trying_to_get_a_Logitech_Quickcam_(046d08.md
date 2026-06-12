---
title: "[SOLVED] Trying to get a Logitech Quickcam (046d:08dd) to work with Skype/Ibex"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by diablo75 on 2008-12-30
I am trying to find a good guide for getting a Logitech Quickcam (hardware id number produced by lspci is 046d:08dd) to work.  I found one for 7.10... but that seems a bit dated to me and wanted to check and see if there is a more updated guide available.  Upon first trying the cam out with skype, the video test produced a bunch of garbled digital noise...nothing close to a picture at all.

---

### Post by spiderbatdad on 2008-12-30
have you tried LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

---

### Post by diablo75 on 2008-12-30
> **spiderbatdad said:**
> have you tried LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

Do I just paste that into terminal?  And if it works, do I have to do that every time I want to run skype?  I could make a custom launcher for it if that's the case... just wondering...

---

### Post by spiderbatdad on 2008-12-30
yeah try pasting that into your term. There was some incompatibility with libv4l in intrepid and existing apps. There has been a lot of work and patches for supported apps, but programs like skype obviously can't be patched by ubuntu developers. There is a sticky in "general help" with this workaround and a link to the bug on launchpad. If it doesn't work for you, IDK what to suggest...maybe you need the gspca driver and modprobe it.

---

### Post by diablo75 on 2008-12-30
That special command work...

But I don't want them to have to paste that into a terminal every time they want to run skype with that webcam.  I tried to create a custom launcher on the upper panel, but I get an error saying something like.... "Blah blah no child process blah" sorry I can't remember what it said.  I even tried to change the launcher type from Application to Application In Terminal, and it still failed....

How else might I create a shortcut for this special command?

---

### Post by spiderbatdad on 2008-12-30
```
mkdir ~/bin
touch ~/bin/skype.sh
gedit ~/bin/skype.sh
# paste in the little #!/bin/bash script below. make sure #!/bin/bash is the very first line.no space or indent or skipped line.

chmod 775 ~/bin/skype.sh
```

```
#!/bin/bash
sleep 2
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

~/bin is in my path as set in .bashrc. But there might be a provision in intrepid to automatically put bin in your path, if you create the directory...a little .gconf prog, i think, anyway...

If it doesn't work...append .bashrc by adding the following at the end of the file.

```
export PATH=$PATH:$HOME/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/bin
```

Then right click your launcher, select properties, and in the command box, use the browse button to locate the script. Just run it as an application...not Application in Terminal.

Of course you can do all of the above graphically, as well by right mouse clicks in your home folder...then make directory bin...click into bin and right click...create document...rename document...click into document...paste in code...save...right click doc again...select allow execute as program...set other permissions...etc.

---

### Post by diablo75 on 2008-12-30
There happens to be a microphone built into this webcam.  I've not had a chance to check within Skypes audio settings whether or not it appears as a selectable source... anyone know if it does appear or it it's even a possibility?  If nothing else I can get a cheap mic from radioshack I guess.

---

### Post by diablo75 on 2008-12-30
> **spiderbatdad said:**
> ```
mkdir ~/bin
touch ~/bin/skype.sh
gedit ~/bin/skype.sh
# paste in the little #!/bin/bash script below. make sure #!/bin/bash is the very first line.no space or indent or skipped line.

chmod 770 ~/bin/skype.sh
```

```
#!/bin/bash
sleep 2
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

~/bin is in my path as set in .bashrc. But there might be a provision in intrepid to automatically put bin in your path, if you create the directory...a little .gconf prog, i think, anyway...

If it doesn't work...append .bashrc by adding the following at the end of the file.

```
export PATH=$PATH:$HOME/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/bin
```

Then right click your launcher, select properties, and in the command box, use the browse button to locate the script. Just run it as an application...not Application in Terminal.
Who's awesome?  You're awesome!
\\:D/

---

### Post by spiderbatdad on 2008-12-30
changed permissions to 775 just in case...to match /usr/bin/skype....except not owned by root...so 775 instead of 755...the mic should work but you might have to fiddle with audio settings in skype...glad that worked out. :D

---

### Post by dislocated on 2009-01-07
I've used Skype on previous versions of Ubuntu with no video problems. Now I also get the green static video playback, or Skype just crashes.

I tried the solution above, but it doesn't seem to work for me.

I'm using 64bit Ibex with a logitech webcam.

---

