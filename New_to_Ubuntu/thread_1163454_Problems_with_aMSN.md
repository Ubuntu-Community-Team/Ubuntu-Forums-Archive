---
title: "Problems with aMSN"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by casa202 on 2009-05-18
Hi I installed Ubuntu 9.04 jaunty 64bits a few days ago and it's been running fine so far, the only thing I can't get to work is aMSN 0.97.2
The package installed fine but it never logs in, can someone help me with this? thank you!

btw my msn account works fine with pidgin

---

### Post by nolliecrooked on 2009-05-18
> **casa202 said:**
> Hi I installed Ubuntu 9.04 jaunty 64bits a few days ago and it's been running fine so far, the only thing I can't get to work is aMSN 0.97.2
The package installed fine but it never logs in, can someone help me with this? thank you!

btw my msn account works fine with pidgin

Unless you use a webcam, emesene is wayyyyyyyyy better than aMSN.

---

### Post by casa202 on 2009-05-19
Hi, I tried emesene as well but it didn't work either...I got the latest version.
I don't know what the problem is...

---

### Post by ellgor on 2009-05-19
Hi,

It may be that your version of "tk and /or tcl" is not up to date (theses are part of the network protocols) I remember fixing mine this way before, hope this helps.

Regards, Ellgor.

---

### Post by Mornedhel on 2009-05-19
> **ellgor said:**
> "tk and /or tcl" is not up to date (theses are part of the network protocols)

Uhm.

Tk is a GUI toolkit. Tcl is a programming language.
[http://en.wikipedia.org/wiki/Tcl](http://en.wikipedia.org/wiki/Tcl)
[http://en.wikipedia.org/wiki/Tk_(framework](http://en.wikipedia.org/wiki/Tk_(framework))

---

### Post by bacardiandwatermelon on 2009-05-19
Are you running a firewall?

---

### Post by Roadbloc on 2009-05-19
Yh. if u have firestarter running it can interfear. i dunno whats up wi pidgin. why not just use that?

---

### Post by newbuntuxx on 2009-05-19
> Unless you use a webcam, emesene is wayyyyyyyyy better than aMSN.

Agreed! emesene is the best out there. It is simple and elegant, and very very light.

---

### Post by casa202 on 2009-05-19
well I don't use a firewall, also pidgin is ok but I wanted to try other options. the problem with emesene is that it freezes after I click login and then it stops responding.

I tried launching it with the terminal and this is what i get:

/usr/share/emesene/emesenelib/SignalHandler.py:21: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/usr/share/emesene/emesenelib/Msnobj.py:21: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha


But I don't know what it means :P

---

### Post by casa202 on 2009-05-20
anyone...??

---

### Post by caravel on 2009-05-20
I had a problem with the version of amsn in the repositories in the past, not in Jaunty but in an earlier release.  The solution for me was to download the "distribution independent installer" version from their site and that worked flawlessly.  Personally though I don't think much of it.  Pidgin (gaim) is way preferable.

-Edit: If you're going to go down that route, completely remove the old amsn first in synaptic.

-Edit: Gah, I just realised that you did try the lastest version anyway...

Try running it from the terminal and see what errors appear when it tried to connect?

---

### Post by casa202 on 2009-05-21
Ok I'll do that with aMSN, I have posted what the terminal shows when I try to use emesene, anyone knows what that is?


/usr/share/emesene/emesenelib/SignalHandler.py:21: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/usr/share/emesene/emesenelib/Msnobj.py:21: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

---

