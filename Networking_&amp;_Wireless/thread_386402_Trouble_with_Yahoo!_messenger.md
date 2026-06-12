---
title: "Trouble with Yahoo! messenger"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by bradford72 on 2007-03-17
I'm having trouble installing Yahoo! IM on my machine (I know I could use GAIM or another IM-er...but then my Java run-time environment plug in thingie is gone ) (btw way, I do believe that thingie is the proper technical term)  I downloaded the package from Yahoo! (for debian) and followed the instructions, and came up with a bunch of dependency issues (rest assured the point of all this is right around the corner).  Long story short, I was able to get MOST of the libs from synaptic, and according to what my screen says, I SHOULD be okay...but no... here's what I did/got...
> bradford@bradford-desktop:~/Desktop$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb 
(Reading database ... 174003 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

Now, through synaptic, I cannot find libssl0.9.6...I can find 0.9.7 and 0.9.8 (both of which are currently installed), nor can I find an xlibs which is greater than 3.3.6...in fact when I search on xlibs I get libxsharp0 (installed), ude, uwm, xcursor-themes (ins), xkb-data (ins), xlibs-data, xlibs-dev, xlibs-static-dev, and xterm (ins)

anybody know where to find libss0.9.6 and an xlibs (newer than 3.3.6)?  Also, do I need to do anything to set up the libraries once I found em? (do they have to be linked to something? do they go in /bin/lib? ...etc...)

---

### Post by bradford72 on 2007-03-17
So, after a little bit of "check the forums for previous posts" I found this link:
[http://ubuntuforums.org/member.php?u=253855](http://ubuntuforums.org/member.php?u=253855) just thought I'd put it up here for anybody else who is in the same boat!

---

### Post by aysiu on 2007-03-17
> **bradford72 said:**
> So, after a little bit of "check the forums for previous posts" I found this link:
[http://ubuntuforums.org/member.php?u=253855](http://ubuntuforums.org/member.php?u=253855) just thought I'd put it up here for anybody else who is in the same boat!
That link points to the user profile for girard?

---

### Post by dbott67 on 2007-03-17
> **aysiu said:**
> That link points to the user profile for girard?

Maybe he means this post (or maybe the whole thread?):
[http://ubuntuforums.org/showthread.php?p=2307236#post2307236](http://ubuntuforums.org/showthread.php?p=2307236#post2307236)

Most of the thread is a bit on the old side and the consensus seems to be to use GAIM, but there does appear to be a solution offered by Girard.

-Dave

---

