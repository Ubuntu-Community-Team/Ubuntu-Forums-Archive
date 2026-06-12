---
title: "Amarok Downgrade"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by atngplusultra on 2009-05-01
So, when i upgraded to Jaunty, I installed Amarok 2, which I'd heard was different, and annoying in some ways, but, I figured it was something I could put up with. a week later, it's been acting up, and i figured downgrading would do the trick.

Problem is, I can't find even an externally-downloadable package for 1.4.x, which i was what i liked more, and what worked better.
why do they not want me to downgrade?

and if I'm just not looking hard enough, please say so, and help me out. This newest-version-only stuff is completely bogus

---

### Post by fifth on 2009-05-01
Before you downgrade, why not try upgrading to the 2.1 [beta]("http://amarok.kde.org/wiki/Download:Kubuntu") and give that a go.

Easy to do, just add the ppa to your source list;

```

deb http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main
```

---

### Post by Lenny99 on 2009-05-01
I agree with you. Amarok 2 does not work properly and has no business in the JJ release if it's going to be buggy.  I was very happy with Amarok 1.4.

---

### Post by atngplusultra on 2009-05-01
Yes, they should at least make downgrading easier if they're going to integreate it into the new release.
speaking of downgrading, thanks fifth!

---

### Post by Didius Falco on 2009-05-01
If you do decide to go back to the 1.4.x version of Amarok, this blogger has found a repo that has it, and has listed the steps you need to do to accomplish it.

[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)

I hope this helps...

---

### Post by atngplusultra on 2009-05-01
> **Didius Falco said:**
> If you do decide to go back to the 1.4.x version of Amarok, this blogger has found a repo that has it, and has listed the steps you need to do to accomplish it.

[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)

I hope this helps...


PERFECT. thanks.
actually, i'd found that guide on someone else's page in spanish or portugese or something, and i was doing fine but then my machine crashed. (which is also something peculiar to Jaunty that was uncommon in Intrepid, but that's a different issue than this)

---

### Post by george1984 on 2009-05-02
Hello

Bogdan's pp worked for me.

It can be found in this thread :-


[http://ubuntuforums.org/showthread.php?t=1084971](http://ubuntuforums.org/showthread.php?t=1084971)

Note...If Amarok14 does not appear in Synaptic as expected, Empty Search Box and then click Origin>pp

---

### Post by whoey on 2009-05-06
> **fifth said:**
> Before you downgrade, why not try upgrading to the 2.1 [beta]("http://amarok.kde.org/wiki/Download:Kubuntu") and give that a go.

Easy to do, just add the ppa to your source list;

```

deb http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main
```

Well this is a bit better for me here... the version of Amarok2 that installed with jaunty was a pos... the splash screen would popup over all windows for 60-90sec (and occasionally crash). After this update, it takes like 3 sec.

---

