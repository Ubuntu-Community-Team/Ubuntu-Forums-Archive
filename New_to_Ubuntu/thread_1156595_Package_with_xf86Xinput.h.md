---
title: "Package with xf86Xinput.h?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by guedesav on 2009-05-11
I need to find the package that contains a newer version of the xf86Xinput.h file, one that contains the function xf86IsCorePointer. Anyone knows how to find it, or which is?

---

### Post by anewguy on 2009-05-11
don't know if these will help you or not:

[http://www.cs.mtu.edu/~cjblazek/d0/d6/xf86Xinput_8h-source.html]("http://www.cs.mtu.edu/~cjblazek/d0/d6/xf86Xinput_8h-source.html")

[http://www.cs.mtu.edu/~cjblazek/d3/d3/xf86Xinput_8h.html]("http://www.cs.mtu.edu/~cjblazek/d3/d3/xf86Xinput_8h.html")

Found these with a Google search of the function you were looking for.  Still looking to see if I can find more.

Dave :)

---

### Post by guedesav on 2009-05-11
Okay, let me rephrase what I need: I actually need the module with that function in, so I can load the driver for my tablet. Thus, I need to know which package(s) will install this module.

Thanks, anyway.

---

### Post by anewguy on 2009-05-11
Does the package xinput include that funtion?  I haven't looked at it but I've seen reference on the net to it.  I don't know if it's in the repos or not.

Dave :)

You may also want to see what gets loaded with libxi6 and libxi-dev.

---

### Post by guedesav on 2009-05-11
xinput is up to date already, and libxi-dev and libxi6 didn't help it, either, at least up to hardy repositories...

Still waiting for another alternative...

---

### Post by anewguy on 2009-05-11
Yeah, I just checked them in 9.04 and can't find that function either.  Doing some more googling to see if I can find it.

Dave :)

---

### Post by anewguy on 2009-05-11
I have found some references on the net indicating that, at least for openbsd and debian experimental [at some point in time - who knows, may have been moved mainstream now], that particular function was removed because it was causing some input devices to fail and crashing x.  Most of these seem to mention a tablet somewhere in their text - don't know if you are using a tablet or having some other error.

Since I don't know if it would "break" X, you may want to see if you can find an older version (perhaps pre-Hardy) to download but not install in the system.

Dave :)

---

### Post by guedesav on 2009-05-12
I'm actually trying to get a tablet to work. Here: [http://ubuntuforums.org/showthread.php?p=7261976](http://ubuntuforums.org/showthread.php?p=7261976)

---

### Post by anewguy on 2009-05-12
I see that driver on sourceforge hasn't been updated in eons, and refers back to an older version of xorg.  I also noted that it says to use core events, and I can only assume that probably has something to do with it.

BTW - what version of Ubuntu are you running?

Dave :)

---

### Post by anewguy on 2009-05-12
Found something from November of last year you may want to check:

[http://harishankar.org/blog/entry.php/getting-the-wizardpen-driver-working-on-xorg-debian]("http://harishankar.org/blog/entry.php/getting-the-wizardpen-driver-working-on-xorg-debian")


Dave :)

---

### Post by anewguy on 2009-05-13
Sorry I've been unable to find anything else.  Have you had any luck yet?

Dave :)

---

### Post by guedesav on 2009-05-13
I've downloaded the latest version of XFree86 from the official site. It messed my whole X server, but after that the tablet worked and I managed to change the X back to X.org.

---

### Post by anewguy on 2009-05-13
Wow!  Glad to hear you got it working.  Getting the xfree86 stuff was a smart idea in terms of getting the code you needed.  Quite a lot of work!

Congrats, and sorry I couldn't have been any help to you.

Dave :)

---

