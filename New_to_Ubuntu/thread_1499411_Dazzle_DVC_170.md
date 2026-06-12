---
title: "Dazzle DVC 170"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Mtrboat01 on 2010-06-01
I have installed Pinnacle Studio on my Ubuntu 9.04 with Wine. Software seems to work just fine with one problem the Dazzle DVC 170 can not be detected. The light comes on but nothing is coming up at all to let me know it has been detected . If you know of a driver and a way to install it Please help. I am still new to Ubuntu and just finding my way.

---

### Post by inameiname on 2010-06-01
I suspect the reason it can't be detected it because of Wine. Often times, a major bug with Wine is the inability to detect hardware devices, such as USB things, or even drives and adapters themselves. There might be a way to force Wine to detect it, but I don't know how to do that I'm afraid. If all else fails, perhaps try a native Linux application that's similar to what you want/use. Also, checking to see if it's at least detected through native Linux programs might tell you it's a problem with Wine and it's lack of detecting it, not just that your device just won't be picked up at all in Linux.

---

### Post by anewguy on 2010-06-02
Well, the last I had heard Wine doesn't support USB devices except for keyboards, mice and some printers.

But beyond that, I have found some threads on the net about your device.  One such thread mentions using a native application.  It also talks about recompiling the kernel, but I don't think you'll need to do that with the kernel version we are now at.  Instead, follow the thread but read mainly the parts dealing with the command line syntax for mencoder and also all of the parts regarding getting sound to work.  If worse comes to worse we could always try the kernel patch, but I don't think you'll need it.

I am not familiar with using the device in Linux, however I will gladly help as best I can with what is posted in the thread.

Here's the link:

[http://www.linuxquestions.org/questions/linux-hardware-18/dazzle-dvd-recorder-497596/]("http://www.linuxquestions.org/questions/linux-hardware-18/dazzle-dvd-recorder-497596/")

Note that it mentions the 100 model, but further in the thread it is mentioned the OP is dealing with a model 170 and did get it working with the native application.

Dave ;)

---

