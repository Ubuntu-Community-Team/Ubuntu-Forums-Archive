---
title: "Source repositories needed?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by RTrev on 2010-06-22
Is there any need to keep the **source** repositories enabled if one has no plans to examine or compile things manually?

Seems like it would speed up checks for updates by removing the check from the "Source Code" box in Software Sources.  Is there any reason not to do this?

Thanks.

---

### Post by Paqman on 2010-06-22
Nope, uncheck them.

---

### Post by wojox on 2010-06-22
Here find the closest on near you [Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/")

---

### Post by K.Mandla on 2010-06-22
> **Paqman said:**
> Nope, uncheck them.
Agreed. I regularly disable them on older machines because it compounds the time it takes to manage the software databases, and further slows down Aptitude. And unless you're planning on building something, there's no need for them.

And if you *do* need them in the future, you can enable them, build your software, then disable them again without too much trouble. ;)

---

### Post by RTrev on 2010-06-22
Thanks everyone.

Have to wonder why they are enabled by default.  I'm guessing that the average user would fall into one of two categories: 1) Will never need the source and would be better off not having it cluttering up the system, or 2) wants the source and can easily figure out what needs to be done to obtain it.

Hmm? <g>

---

### Post by Paqman on 2010-06-22
> **RTrev said:**
> 
Have to wonder why they are enabled by default.

Presumably because the license that most software in the repos is available under stipulates that the source code be available to anybody that wants it.

---

