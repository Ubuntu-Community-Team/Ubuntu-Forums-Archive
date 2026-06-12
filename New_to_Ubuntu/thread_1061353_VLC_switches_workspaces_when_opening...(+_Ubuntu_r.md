---
title: "VLC switches workspaces when opening...(+ Ubuntu rant)"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Adamantus on 2009-02-05
Neither Totem (gstreamer and xine) nor Mplayer can play movies consistently without freezing. About 90% of the time they freeze or play about 1/20 of the speed. And if they do play, they freeze at the end forcing me to force quit. So I tried VLC and it worked well for the most part (although it does freeze at the end a lot). But now, all of a sudden (I didn't do any updates or change anything on my system really), whenever I open a movie, VLC will open in another workspace (always the furthest to the right). I'm running Hardy Heron with an ATI Radeon HD 3200 graphics card.

How can I fix this (both the workspace switching and freezing at the end)?

**Ubuntu Rant**: What is it with open source software that makes it so buggy. I can't go a day without my media player messing up, or even Ubuntu itself doing something annoying. I had always heard Linux was so much more stable than Windows, yet I've never had any problems in Windows whereas there are tons of little bugs in Ubuntu (the supposedly stable, long term support Hardy Heron). Anyway, rant over.

---

### Post by emarkd on 2009-02-05
First, I use totem to play movies on my desktop and use mplayer + mythtv as a media center in the living room (running on 10-year-old hardware) and never have a hiccup.  It "just works" for me, and for a lot of people.

Also, the Linux kernel is much more stable than Windows.  It also manages resources much better.  That doesn't mean that every piece of software you run on your Linux box is going to be as stable.  And remember that most of this stuff is put together by volunteers.

As to your problem, have you installed all the necessary codecs?  Like the w32codecs package?

---

### Post by sandyd on 2009-02-05
maybe haven't installed ubuntu-restricted-extras yet?

try this

go into synapatic. right click on vlc, select complete remove
then after its finished complete removing it, install it... again.

---

### Post by Adamantus on 2009-02-05
I just did a complete removal of VLC and re-installed it. I also downloaded the ubuntu-restricted-extras. It's still switching to another workspace when I open a movie. But it didn't freeze when it got to the end this time, so maybe it helped a little.

---

### Post by Adamantus on 2009-02-05
Wow, I ran it in terminal, and here's the output I got. It went on for a lot longer, but it was the same stuff with larger numbers. It once again opened in another workspace, but an error window popped up in the current workspace saying "cannot open file Never" (Never was the name of the movie). It's weird, because I don't get this error when I just click on the icon:

aj@aj-laptop:~$ vlc Never
VLC media player 0.8.6e Janus
/home/aj/.themes/Truth+/gtk-2.0/gtkrc:196: error: invalid string constant "theme-combo", expected valid string constant
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000292] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000306] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000310] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000314] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000318] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000322] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000326] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000330] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000334] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000338] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000342] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000346] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000350] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000354] main input error: no suitable access module for `Never'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Never
No such file or directory

---

