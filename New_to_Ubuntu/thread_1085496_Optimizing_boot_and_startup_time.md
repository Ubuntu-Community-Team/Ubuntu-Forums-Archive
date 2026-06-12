---
title: "Optimizing boot and startup time"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by rosstheboss on 2009-03-03
A fresh install of ubuntu is considerably slower than a fresh install of windows XP to load, from the time of pressing the power button to reaching the desktop. How can the bootup speed be reduced. So far I've found the sessions manager, where I can remove some unneeded programs at startup. What other ways are there to prune the operating system?

---

### Post by skymera on 2009-03-03
Don't forget XP is pushing 8 years old this year.
That's 8 years of technological improvements and more speed.
Ubuntu is only a few months.

My Ubuntu boots in 20 seconds in guess.
Try

System > Preferences > Sessions
Disable some stuff there. Leave power manager on etc

System > Administration > Services
Disable ones you dont need. Don't disable communication bus (dbus)

More:
```
 sudo apt-get install sysv-rc-conf 
```

Rumours say Ubuntu 9.04 on EXT4 is a speed demon

---

### Post by swoody on 2009-03-03
EXT4 is a bit quicker than EXT3, but there's no real need to jump the gun into Jaunty before you need to :)

As far as speeding up your system, there's a TON of info on booting Ubuntu faster. Just spend a little time Googleing, and you'll find more info than you'd care to know :) In the meantime, here's some reading material to get you started:

[https://wiki.ubuntu.com/FasterBootProcess](https://wiki.ubuntu.com/FasterBootProcess)
[http://resources.zdnet.co.uk/articles/features/0,1000002000,39454355,00.htm](http://resources.zdnet.co.uk/articles/features/0,1000002000,39454355,00.htm)
[http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html](http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html)
[http://www.openfirmware.info/Welcome_to_OpenBIOS](http://www.openfirmware.info/Welcome_to_OpenBIOS)
[http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html](http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html)
[http://blogs.techrepublic.com.com/10things/?p=387](http://blogs.techrepublic.com.com/10things/?p=387)
[http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast/](http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast/)

Good luck! Keep us updated with your progress, and if you encounter any problems :D

---

### Post by Scubdup on 2009-03-03
I am a bit disappointed at my Ubuntu boot time too, but I have an Intel P4 based machine. I read that there are some problems with this chip which should be resolved in the new Jaunty release 9.04.

This, together with the ext4 developments have got me looking forward to April!

---

