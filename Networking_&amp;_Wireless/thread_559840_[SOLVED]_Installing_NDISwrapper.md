---
title: "[SOLVED] Installing NDISwrapper"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by NotoriousTF on 2007-09-25
Ok so I've downloaded and extracted the most recent version of NDISwrapper. After I navigated to the newly created folder made from the extraction, and try to run 'make', I am given this error:

```

make -C driver
make[1]: Entering directory `/home/tadhg/Wireless Drivers/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/tadhg/Wireless Drivers/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** No rule to make target `Drivers/ndiswrapper-1.48/driver'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tadhg/Wireless Drivers/ndiswrapper-1.48/driver'
make: *** [all] Error 2

```

Can anyone point out where I am going wrong? :confused:

---

### Post by SpiritIsReality on 2007-09-25
howdy
I don't know much about it, but I think what you're looking for is here
[http://ubuntuforums.org/showthread.php?p=601226](http://ubuntuforums.org/showthread.php?p=601226)
and heading #5 here (they are the same ?
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

so do you think you have those packages they talk about installed?

trails
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Ndiswrapper&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Ndiswrapper&titlesearch=Titles)

---

### Post by Old *ix Geek on 2007-09-25
Well, something jumped out at me right away:
```
make[1]: Entering directory `/home/tadhg/**Wireless Drivers/ndiswrapper-1.48/driver**'
...
make[2]: *** No rule to make target `**Drivers/ndiswrapper-1.48/driver**'.  Stop.
```

I think the space in your subdirectory's name, "Wireless Drivers" is causing confusion. Try renaming it--removing the space, of course--and/or start over in a new directory that doesn't have spaces in its name!  If that doesn't help...post again.

---

### Post by SpiritIsReality on 2007-09-25
Old *ix Geek ...thanks, good one!

---

### Post by NotoriousTF on 2007-09-26
Hey thanks Old *ix Geek, worked perfectly! I completely overlooked anything to do with file names. Would it be a good idea in future to not put a space in folder names to prevent this occurring again?

---

### Post by Old *ix Geek on 2007-09-26
You're welcome. :D

I NEVER put spaces in any names--directories or files--because that's how I was "brought up" in *nix, so to speak.  Back in the day, it was **possible** to put spaces, and other "special" characters, in names, but it wasn't advisable.  Therefore, other than just playing around (like in a directory that I could **rm -rf** without concern), I just never did it.  Even when I've used windoze computers I've followed that same protocol.  *I* don't think spaces belong in file/directory names, and as you just saw they CAN cause problems.  So why risk it?  When I want a space between characters, I use underscores, dashes, periods, or capital letters: DownloadedSoftware, letter_to_sister, fstab.orig, etc.

---

