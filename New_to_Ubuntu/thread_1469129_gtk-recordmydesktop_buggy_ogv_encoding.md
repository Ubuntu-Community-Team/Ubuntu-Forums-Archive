---
title: "gtk-recordmydesktop buggy ogv encoding"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by CJay554 on 2010-05-01
Hey everyone a bit of a problem here... It may or may not be the best place to post this as it doesn't pertain Ubuntu in particular, but you'll see where im coming from.

In Karmic i was able to record through gtk-recordmydesktop and then use openshot to edit the resulting ogv file with little stress. A few frames would be completely white (about 5 seconds of each beginning ogv section) which I was able to work around by doing tricky video editing.

In Ubuntu Lucid the white frames are ALL OVER the video, i can play them fine in the movie player (with a bit of a bug, if i move the window or play around with other windows the video playback goes black, but the audio still goes, keeping the mouse still or hovering over the video a few times lets the video playback come back on). When i import them to openshot all the frames are completely white. Now the movie player works fine with every other video, and i've heard of a upstream bug with the OGV coding. 

To be completely honest im not sure what to do, or why i even started this thread. But if i don't say something its one of those bugs that will live on till who knows when. If anyone has any ideas on where to begin please help me out!

---

### Post by Jon Monreal on 2010-05-01
You can report bugs in gtk-recordmydesktop [here]("https://bugs.launchpad.net/gtk-recordmydesktop").

That said, I would suggest you try another program such as Istanbul Desktop Session Recorder and see if that works better for you. It can be found by searching the Ubuntu Software Centre.

---

### Post by CJay554 on 2010-05-03
I've had a few problems with my audio card being recognized with gtk-recordmydesktop though i figured out how to fix that easily, but with istanbul it doesn't record sound and just records video. 

Is that it for desktop recorders? =(

---

### Post by Jon Monreal on 2010-05-03
There's also recordmydesktop in the Software Centre, but I've never used it before.

---

### Post by CJay554 on 2010-05-03
Well thats just gtk-recordmydesktop without the gtk interface, basically command line. Still a no go...

---

### Post by Jon Monreal on 2010-05-03
You could try [this patched version of recordmydesktop from a PPA]("http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/").

There's xvidcap (although it outputs to MPEG and I'm not sure if it records audio. Also VLC can record a stream of the desktop (again, don't know about sound).

Ideas from [this thread]("http://ubuntuforums.org/showthread.php?t=1165763").

---

### Post by DodgeV83 on 2010-05-12
The new libtheora in Lucid doesn't play nice with Recordmydesktop. Specifically, Recordmydesktop gives libtheora some commands which don't make sense.  The old libtheora simply ignores those commands, the new one does not.

Here is my bug report on the problem

[https://bugs.launchpad.net/gtk-recordmydesktop/+bug/578397](https://bugs.launchpad.net/gtk-recordmydesktop/+bug/578397)

And here is a temporary solution:

1. Type this in a terminal - "sudo gedit /etc/apt/sources.list" and Add the following lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse

2. Open Synaptic and reload the files.

3. Do a search for libtheora, highlight the package "libtheora-bin" and select Package -> Force Version -> Karmic. Do the same for package "libtheora0" and hit Apply.

4.  Again highlight those two packages and select Package -> Lock Version.

This will fix the problems until recordmydesktop is fixed.

---

### Post by brk3 on 2010-05-26
Tried that and now video is just all white frames. :(

---

