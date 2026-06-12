---
title: "'Synaptic' conflict with  DVD Authoring ManDVD QDVD or DVD Styler"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by matt-lisa on 2009-06-22
G'day Linuxians of the tribe Ubuntu!

I have been trying to install DVD Authoring programs from the applications list and they all seem to conflict with something that I already have installed.

How do I 

a) find the conflict using synaptic package manager as suggested
b) or is there an alternate that doesn't conflict

All I want to do is patch together a few home videos to play on one dvd. Fancy titles/fades etc aren't really required but would be nice.

Was used to using MS Movie Maker (Which was alright until it had to play a big file) and Muvee. Something similar to these would be great.

Cheers

Matt

---

### Post by Closed_Port on 2009-06-23
Hi, I think synaptic should tell you what the conflict is. Does it say anything when you try to install these packages?

My suggestion would be to try to install them with apt-get. For example: sudo apt-get install mandvd

Apt-get should give you an error message about what is wrong. Copy and paste the output here and hopefully people will be able to figure out how to solve the problem.

---

### Post by gn2 on 2009-06-23
Have you tried DeVeDe?

It's in the repositories and can be installed either using Synaptic or by simply running ```
sudo apt-get install devede
```

---

