---
title: "Which Ubuntu?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Doug11 on 2009-02-05
Just wondering which version is the most stable with the most support. I just loaded an old 7.04 Feisty and tried to do the distro upgrade to Gutsy but it keeps failing saying it can't connect to the proper server. I know Intrepid is new and have tried it but there seems to be still a few more issues with it such as webcam support and a few others. Any opinions?

---

### Post by SuperSonic4 on 2009-02-05
I'd say Hardy LTS is best.

If you want long support you can get the 8.04 ubuntu server which is supported until 2013 I think

---

### Post by yeats on 2009-02-05
I think you'd probably want Hardy Heron (8.04 LTS).  It will be supported through April of 2011 and has proven to be very stable and reliable.  I moved to Intrepid on two computers back in the fall, but have moved *back* to Hardy because I found Intrepid to be buggy and unreliable (I'm also a Kubuntu user and KDE 4.1 might have been a little too bleeding edge for me after all :-) ).

I'd say to go with Hardy.

As far as connecting to hardy's repositories goes . . . I would do Alt-F2 and 

```
sudo gedit /etc/apt/sources.list
```

And select Replace ... from the Search menu.  Replace "fiesty" with "hardy," (no quotes) then save and open Synaptic, which should offer you MANY updates which will take a long time :-).

Good luck with your decision.

---

### Post by Voland on 2009-02-05
It depends. Ask yourself what do you want to get? If you want to be on the bleeding edge, try Jaunty :) For stable release choose LTS, but I think 8.10 is pretty good for everyday use on laptop/desktop.

---

### Post by Doug11 on 2009-02-05
Thanks for the quick response,,will have to download and burn i guess. This is the error i keep getting when i try to upgrade whether i use the main server or the canada server.

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found

---

### Post by SuperSonic4 on 2009-02-05
> **chrissharp123 said:**
> I moved to Intrepid on two computers back in the fall, but have moved *back* to Hardy because I found Intrepid to be buggy and unreliable (I'm also a Kubuntu user and KDE 4.1 might have been a little too bleeding edge for me after all :-) ).

Good luck with your decision.

KDE 4.2 is far better than KDE 4.1 ;)

---

### Post by Doug11 on 2009-02-05
Another quick questionon Hardy Heron,,is the 64bit just as stable and supported as the 32bit?

---

### Post by yeats on 2009-02-05
Looks like they've taken the Fiesty repositories down.  You can probably change this in Synaptic by going to Settings -> Repositories, but Fiesty was before my time :-).  You can try my name substitution method if you can't do it automatically in Synaptic.

---

### Post by yeats on 2009-02-05
> **SuperSonic4 said:**
> KDE 4.2 is far better than KDE 4.1 ;)

Thanks - I'm thinking I might try again with Jaunty, but I'm much more conservative about things than I was when I started, the main reason being that I actually need to get work done (for my job) and the KDE 4.1 milieu just wasn't a good fit.  Thanks for the feedback though - I haven't entirely given up :-)

---

### Post by yeats on 2009-02-05
> **Doug11 said:**
> Another quick questionon Hardy Heron,,is the 64bit just as stable and supported as the 32bit?

Yes - as far as I know.  I only use the 32 bit at the moment . . .

---

### Post by vasco.debian on 2009-02-05
Yeah

Hardy Haron 8.04 LTS rocks,
There heard several issues with 8.10 but not tried yet ;)

Regards,
Vasco

---

### Post by hyper_ch on 2009-02-05
java and flash used to be the biggest concerns in 64bit. There's now flash player 10 alpha in 64bit availble, I've been using it for a long time and works much better than flash on 32bit ever worked... and for java there's also 64bit version, I haven't used it yet but I read on the forums here that it works also.

There's no reason anymore to not run 64bit.

---

### Post by Voland on 2009-02-05
**Doug11**, AFAR support of 7.04 is ended, so there are no such folders.

---

### Post by Doug11 on 2009-02-05
Thanks all. Download is just about complete,,should be back shortly on Hardy.

---

### Post by hyper_ch on 2009-02-05
I'd use intrepid and not hardy...

---

### Post by Doug11 on 2009-02-05
> **hyper_ch said:**
> I'd use intrepid and not hardy...
I tried Intrepid and found it to buggy with some things like webcam support and a few other things. Just booted up Hardy and was very impressed. Had my broadcom wireless running in about two minutes with very little work.

---

