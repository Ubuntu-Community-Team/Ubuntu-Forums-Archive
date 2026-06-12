---
title: "Galaxy screensaver for 9.10"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by timmyhiggy on 2009-11-02
Hi

9.04 had possibly my favourite screen saver of all time: the galaxy one where you had a small number of galaxies all spinning away and gravitationally attracting each other before piling into one another and spitting everything everywhere! I love it...
I was gutted when i upgraded to 9.10 and it was gone!! I searched "screensaver" in synaptic package manager and it wasnt there, any advice to get this screensaver back would be very welcome!

Cheers
Tim

---

### Post by Da CalebMan on 2009-12-10
Yeah! I miss that too! I've been googling for ages and got nothing! It's gotta be *somewhere* in synaptic...

---

### Post by tbear2500 on 2010-07-27
I found the file (screensavers are in /usr/lib/xscreensaver/), and I tried doing what I would do with Microshaft screensavers, fonts, etc. (sudo cp [directory]/galaxy /usr/lib/xscreensaver/galaxy) but to no avail; it won't appear in the screensaver list, and if I try to drag it there it says it does not appear to be a valid screensaver theme.  Maybe it needs extra files?  This was the best screensaver in existence though; when it wasn't available in 9.10, I considered for a long time reverting to 9.04 simply for that reason.  If you do get the galaxy file from 9.04, you can at least run it (in a small window) by double-clicking it in 10.04 (and probably also 9.10).  I'm currently working on some other ideas for getting it back.  I'll let you know if those get anywhere.

---

### Post by tbear2500 on 2010-07-27
I got it to work!  What one must do is install the appropriate package from [this]("http://packages.debian.org/unstable/x11/xscreensaver") ([http://packages.debian.org/unstable/x11/xscreensaver](http://packages.debian.org/unstable/x11/xscreensaver)) page (I believe I required [this]("http://packages.debian.org/sid/i386/xscreensaver/download")  [i386] package) and you may need to also have the galaxy file in  /usr/lib/xscreensaver/ (it can be obtained from a 9.04 installation in  /usr/lib/xscreensaver/ or [here]("http://tbear2500.x10hosting.com/other/galaxy") ([http://tbear2500.x10hosting.com/other/galaxy](http://tbear2500.x10hosting.com/other/galaxy)).  You will need to use sudo to copy it, but that's not a big deal.  If  you have a problem with working with terminal, you can even just run  sudo nautilus and drag-and-drop the file.  Once you do this, under System->Preferences you will see two screensaver options.  I believe you want the first one, but use whichever looks different from Ubuntu's original screensaver dialog.

---

