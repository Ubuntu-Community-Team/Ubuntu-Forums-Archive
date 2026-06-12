---
title: "Resolution problems and haging on startup"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by tommalley on 2009-02-08
Hi,

Just installed 8.4 hardy heron as an upgrade. Everything is going fine except.

Os hangs on the splash screen unless i go into the grub menu and choose the second kernel.

I cannot change the resolution its stuck at 800x600

I have been chasing the answer and so far have accessed the xcon and discovered my radeon v100 card is installed. Apparently I should be looking for the restricted driver manager but that doesnt seem to exist in 8.4.

Tried installing RDM through synaptic but again it says point to something that used to exist.

Im guessing the hang is because of the graphics driver.

Im pretty new but have got used to the old cut and paste advice but cant seem to get round this problem.

any ideas?

thanks

---

### Post by bgates on 2009-02-08
The first thing I would try is editing grub to remove the splash screen.  This way you can see messages about what is happening during boot.  Full instructions to do so are here:  [http://ubuntuforums.org/showthread.php?t=542082](http://ubuntuforums.org/showthread.php?t=542082)

I'm guessing it's the video driver as well, but this way you will know for sure.

---

### Post by tommalley on 2009-02-08
Ok I did that and one of the messages state that the wrong chipset was detected. 915 only works with intel. does that mean that there is no hope.

Apparently it worked fine under feisty before one day the screen changed resolution and just stuck there.

thanks for that advice looks like the video card is the right avenue.

It never hung under feisty though so not sure why it does it now.

---

