---
title: "What are these entries in my Passwords and Encryption?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by mmasroorali on 2010-01-21
Today I found some entries in my Password and Encryption Keys -> Other Keys. Please see the image. What are these and how did they end up there? I did not make these entries.

Thanks.

---

### Post by wheredidrealitygo on 2010-01-22
Those are a debian developer's keys.

Basically: You have keys on your system which determine levels of trust from certain people/organizations. If you install software sometimes it asks you to 'trust' it so the next time you install something from them it will be 'verified' and trusted by your system, you won't get as many prompts or warnings about security.

In this case, something you have installed has included this particular debian developer's keys.

If it truly concerns you that much then you can likely safely delete it.

Just FYI: his [site]("http://www.palfrader.org/projects.html") with projects listed and his [keys]("http://www.palfrader.org/keys.html").

---

