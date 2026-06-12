---
title: "when i i do the update manager it says this"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by blake7 on 2009-06-04
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9


what do this mean and how can i sort it out


that you for your time :)

---

### Post by sisco311 on 2009-06-04
You have to add the key for your ppa repository:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3B22AB97AF1CDFA9
sudo apt-get update
```

[https://help.launchpad.net/Packaging/PPA#Adding a PPA's keys to your system]("https://help.launchpad.net/Packaging/PPA#Adding a PPA's keys to your system")

---

### Post by x33a on 2009-06-04
it means that the third party repository you are using isn't authenticated.

nothing to worry if you trust the maintainer.

but if it bothers you, go to that ppa's webpage and download the gpg key for that ppa.

which ppa are you using by the way?

post the output of
```
cat /etc/apt/sources.lst
```

---

### Post by tacantara on 2009-06-04
It sounds like the Public Key is not listed in your Software Sources (System >> Administration >> Software Sources >> Authentication Tab).  The instructions for copying the source address and the Public Key are on Launchpad.

---

### Post by blake7 on 2009-06-04
why are thier to differant anwers and which one is the right one??

thank you

or which one is the esayest

---

### Post by tacantara on 2009-06-04
> **blake7 said:**
> why are thier to differant anwers and which one is the right one??
 
thank you
 
or which one is the esayest
 
 
It sounds like sisco311 has the easiest solution.  I would have held back on my response if I'd seen that one earlier.

---

### Post by x33a on 2009-06-04
> **blake7 said:**
> why are thier to differant anwers and which one is the right one??

thank you

or which one is the esayest

there are different ways to add gpg keys to your system.

sisco's method is the easier one.

---

### Post by blake7 on 2009-06-04
thank you sisco311 that was perfectly easy and now all is now well again.

cheers for all your replays
and have a good afternoon

---

