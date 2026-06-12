---
title: "What's With All The Updates?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by 29Tudor on 2009-01-30
I downloaded over 200 when I first installed Ubuntu, have downloaded several more since, now have 62 more waiting. Is this normal...if yes, why?

---

### Post by yeats on 2009-01-30
Every time you log in (and probably once every so many hours/minutes - don't know how often exactly), Ubuntu queries the repositories to see if newer versions of software have been added.  You can watch this happen yourself in Synaptic when you open it or refresh the available programs.  There are programs and dependencies (like software libraries) that get updated in the repositories constantly.  It's lighter on some days than others - looks like you're seeing it on heavy days.  

Anyway, as a convert from Windows, I'm very happy that at least all the updates are coming from one place and I have a say in what's installed! :-)

---

### Post by perlluver on 2009-01-30
> **29Tudor said:**
> I downloaded over 200 when I first installed Ubuntu, have downloaded several more since, now have 62 more waiting. Is this normal...if yes, why?

Security, and any bugs that might have been there when they released the software.  Since there are so many eyes looking at the code, updates are issued faster on Linux than in Windows.

---

### Post by slakkie on 2009-01-30
> **29Tudor said:**
> I downloaded over 200 when I first installed Ubuntu, have downloaded several more since, now have 62 more waiting. Is this normal...if yes, why?

It is normal. Applications have bugs and security issues (bugs). When these get fixed upstream (by the developer) the package in the repositories is "upgraded" and released. This is pretty standard. I have disabled the visual notification in my GUI. I only apply updates once a week. You can limit the updates you get by pinning packages at a particular version if you want. If you want to read more about that read here: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

You can also disable all other repositories and only enable the security repositories, that way you will only get updates related to security issues.

---

### Post by 29Tudor on 2009-01-31
Thanks for the responses...this is a great forum.

---

