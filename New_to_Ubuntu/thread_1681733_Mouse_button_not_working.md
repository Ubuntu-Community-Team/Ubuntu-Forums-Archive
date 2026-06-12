---
title: "Mouse button not working"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by TheJokerV on 2011-02-04
I recently installed 10.10 64 on my laptop and I'm having a problem where a minute into my login the left mouse button stops entirely. Sometimes the right mouse button stops working as well. It's the same for my external mouse, touchpad and touchscreen. I was looking for a solution online and came across this:

[http://ubuntuforums.org/showthread.php?t=1593318](http://ubuntuforums.org/showthread.php?t=1593318)

but the package that was poitned to by the links is no longer there. Can anyone help me?

Thanks

---

### Post by Tyggna on 2011-02-04
The package you need is just the evdev driver.  Try searching for evdev in the package manager and it should come up.

From there, [this]("http://www.x.org/archive/X11R7.5/doc/man/man4/evdev.4.html") may be of help getting it configured and ensuring its working.  The "Synopsis" section of that page is what you'd put in your /etc/X11/xorg.conf file.

Not sure if the new ubuntu uses that--or if there's an easier way, but that's the generic linux solution.

---

### Post by TheJokerV on 2011-02-04
I have the X.Org X server - evdev input driver installed, however there is no xorg.conf file in the folder you mentioned above. Also its not that this mouse never works. It simply works wfor a couple minutes and then cuts out. Any ideas?

---

### Post by Tyggna on 2011-02-04
My best guess is that you have two drivers fighting for control over the bus.  My guess is that you're running evdev and mouse simultaneously.

I haven't tried the newest version of Ubuntu, so I don't know exactly where they put these kinds of directives to check.  In the terminal you can type modprobe -l to get a complete list of loaded drivers.  It may just be a matter of removing the evdev or the default keyboard/mouse drivers.  You're likely to get a very long output from modprobe -l, so you may want to do modprobe -l | less
or try 
modprobe -l | grep evdev
modprobe -l | grep mouse 
and see what comes up

---

