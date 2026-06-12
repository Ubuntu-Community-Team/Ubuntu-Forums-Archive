---
title: "Ubuntu and Intel GMA 4500MHD"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Dreakon on 2010-03-04
Alright, I've been wracking by brain about this the last few weeks.

I really like Ubuntu.  I like how community-oriented it is and honestly, any contibutions to the project (be it simple bug reports or actually learning to program a bit of software) feels like a better use of my free time then most of anything I could waste my time on with Windows.  Windows has enough people working on it.  Plus most of the games I play have some kind of Linux port lol.

That said, the support for Intel graphics is pretty crummy at best.  The default drivers aren't good enough to even watch a YouTube video without intolerable amounts of stuttering, and the UI as a whole is pretty sluggish.

I would really like to make this work... but I'm at a loss for ideas.  I'm willing to try anything at this point.  Would newer, less stable kernels and Intel drivers provide significantly better performance?  Would it be worth it?  Is there anything I can do?

Would I be better off waiting for 10.04 in a month or two to install Ubuntu again (I'm currently on Windows 7)?

Thanks for any help guys!

---

### Post by Dreakon on 2010-03-05
I guess that's a negatory.  Would anyone mind letting me know if it's worth it to wait for 10.04 for Intel graphic support, if there's nothing I can do to alleviate this issue a bit now?

---

### Post by jmundale on 2010-03-05
I sure hope you get an answer.  I've been trying to run SecondLife on my dell latitude and I just is too buggy in ubuntu (windows ok)

---

### Post by kalaka on 2010-04-14
I have an integrated Intel GM965.
It's true that there are some problems with some Intel GPUs but mostly, it works OK (at least for me). I've heard of other people having Intel GPUs which work great but I've also heard of some of the problems you are talking about.


My advice is to use the xorg-edgers packages for the intel drivers. They are the latest development and it does make a improvement.

add these to your software sources
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main 
``` 
(replace *karmic* for your ubuntu version)
then add the key and upgrade
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
sudo apt-get update
```

I hope this helped (it helped me). Even though Intel's drivers for linux are open source, the support is much better for nVidia and ATI. Of course, this is an integrated graphics card, so its not very good anyway (even in Windows).

---

