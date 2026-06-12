---
title: "Help with DVD's"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by eldutcho on 2009-01-30
Well I'm running a dual OS, this is my second try with Ubuntu(I missed it to be honest and I'm finding a dual boot set-up extremely handy for learning Linux while maintaining the functionality I get with windows)

anyway, im trying to tackle a problem i had before
It seems no matter what 'libdvd' package I get from synaptic, Totem video player will always recognize the movie, but I will the error message "Could not read from resource" and fail to play the movie.

any suggestions? Thanks in advance

---

### Post by jpoRS on 2009-01-30
If you have installed the proper codecs (Restricted and Multiverse) Totem can still be a little finicky with DVDs.  Try using VLC, it is a media player that is much better and dealing with DVDs.

Or if you haven't installed the codecs, try that.

Good Luck,
jim

---

### Post by egalvan on 2009-01-30
If you haven't already found this:
An excellent guide to installing/fixing multimedia in *buntu.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by IEKnight on 2009-01-30
If the DVD's encrypted, you need to install the libdvdcss2 package available here:

Hardy: [http://packages.medibuntu.org/hardy/libdvdcss2.html]("http://packages.medibuntu.org/hardy/libdvdcss2.html")
Intrepid: [http://packages.medibuntu.org/intrepid/libdvdcss2.html]("http://packages.medibuntu.org/intrepid/libdvdcss2.html")

Generally, it's a good idea to install that package anyway.

Also, jpoRS is right - use VLC; it's better, and has full support for menus ;)

---

