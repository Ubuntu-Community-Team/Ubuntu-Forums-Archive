---
title: "Listen won't Scrobble?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by jpoRS on 2009-06-23
*Disclaimer:  I find it hard to believe that I am the first person to post about this, but after searching for every relevant topic I have found no helpful results.*

I installed Listen as part of my quest to find an Amarok 1.4-esque player since Jaunty forces you to use Amarok 2.0.  I like Listen, but it won't scrobble any tracks over one minute in length.

Like I said, extensive Googling and forum searching hasn't yielded any helpful results, since the Launchpad bug only references the Listen Project's Trac ticket for the problem, but trying to follow the link leads to an error. ([See]("http://www.listen-project.org/ticket/826"))

So does anyone know where I could find the solution that Listen used to have available?

Thanks,
jim

---

### Post by jpoRS on 2009-06-23
Solved on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/listen/+bug/280859"):

Download the [new audioscrobbler_manager.py]("http://launchpadlibrarian.net/28257295/audioscrobbler_manager.py") file then replace the current audioscrobbler_manager.py

Thanks!
jim

---

