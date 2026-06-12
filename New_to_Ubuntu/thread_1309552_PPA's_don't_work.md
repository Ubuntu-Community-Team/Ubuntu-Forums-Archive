---
title: "PPA's don't work"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-11-01
I had this problem once before and it sorted out but now its back again. I'm trying to add a PPA for flash (though this happens on all ppas) and when I click on the link for the signing key or I use the command to import the key either the browser doesn't load the page or the terminal is stuck at requesting the keys. What's going on here?

---

### Post by Brandon Williams on 2009-11-01
There is a recurring issue with the ubuntu keyserver that causes it to become unresponsive for extended periods of time. If you wait a while and try again, it will eventually work. I typically do something else for an hour or more, and it works when I get back to it.

If it is very important to you to get that software installed immediately, you can always ignore the warnings and install without the signing key. I don't recommend this practice (those signing keys are there for a reason), but it is an option.

---

### Post by Martin Marshalek on 2009-11-01
Okay, I'll wait, I just wasn't sure if it was my connection or launchpad itself. Thanks.

---

### Post by kellemes on 2009-11-01
Just replace the keyserver with another one..
[http://www.rossde.com/PGP/pgp_keyserv.html]("http://www.rossde.com/PGP/pgp_keyserv.html")

---

