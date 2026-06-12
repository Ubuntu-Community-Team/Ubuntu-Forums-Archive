---
title: "how to download source from launchpad and build the application ?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by legolas_w on 2009-11-03
Hi
Can someone please let me know how I can download the source code of [https://bugs.launchpad.net/panflute](https://bugs.launchpad.net/panflute)  and build it myself?

I want to download the 0.6 branch and its source code is not provided as a zip boundle. so I should somehow fetch it from server.


Thanks

---

### Post by snkiz on 2009-11-03
It appears panflute is using Bazar for devlopment see: [https://code.launchpad.net/panflute]("https://code.launchpad.net/panflute")
Haven't done fetched from bazaar in a while so I'm not going to try to tell you how, I'd just mess you up. But try Google for Bazaar snapshot or download and see where that takes you. Thats how I managed to do it before.

---

### Post by sandyd on 2009-11-03
> **legolas_w said:**
> Hi
Can someone please let me know how I can download the source code of [https://bugs.launchpad.net/panflute](https://bugs.launchpad.net/panflute)  and build it myself?

I want to download the 0.6 branch and its source code is not provided as a zip boundle. so I should somehow fetch it from server.


Thanks
```

bzr branch lp:panflute
```
says right on the branches section

also

[https://code.launchpad.net/panflute/+download](https://code.launchpad.net/panflute/+download)

---

### Post by legolas_w on 2009-11-04
Hi, Thanks for reply.


I did the previous command, it downloads the source code. what should I do now?

Thanks.

---

### Post by sandyd on 2009-11-04
> **legolas_w said:**
> Hi, Thanks for reply.


I did the previous command, it downloads the source code. what should I do now?

Thanks.
hmm...
im going to do this without looking....
cd to the directory and
```

./configure
make
sudo make install

```

---

### Post by legolas_w on 2009-11-05
Thank you very much.

Finally I used ./autogen to resolve the problems. although it caused me to install many new packages before it continued to work.

---

### Post by pSYcl0Ne on 2010-02-16
I also need help with this. I'll admit i'm a bit of a newb and i'm unsure how source compiling works - synaptic/apt-get from repo's helps with that. 

I'm also trying to get this panflute to work - gnome-music-applet is no good with exaile (does anyone know how to fix that?) and I dont like using KDE based music players. 

I followed the instructions posted previously and When I try the make command i get this:

lasher@windy-macwinlin:~/Desktop/panflute/panflute-0.6.1$ make
make: *** No targets specified and no makefile found.  Stop.
lasher@windy-macwinlin:~/Desktop/panflute/panflute-0.6.1$ sudo make install
make: *** No rule to make target `install'.  Stop.
lasher@windy-macwinlin:~/Desktop/panflute/panflute-0.6.1$ 

what am I doing wrong? lol... is there a .deb file somewhere for this? actually no I want to know how to do it through terminal. please help.

---

### Post by nothingspecial on 2010-02-16
Try typing ./autogen instead of make.

Allways read the README file first.

---

