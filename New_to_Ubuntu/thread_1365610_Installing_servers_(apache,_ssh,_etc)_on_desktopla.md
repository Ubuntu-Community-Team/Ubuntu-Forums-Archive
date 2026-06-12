---
title: "Installing servers (apache, ssh, etc) on desktop/laptop edition"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by aplonis on 2009-12-27
So I wiped out my former NetBSD, overwriting it with Karmic Koala laptop/desktop edition. Now I'd like to add some servers, the same ones I'd run for years on NetBSD on this same box.

Can't seem to get things like Apache or OpenSSH to install via any method. I've tried the graphical ones plus this...

sudo apt-get install openssh-server
sudo apt-get install apache2

...which both say the package is not available.

I also tried this...

sudo aptitude install openssh-server
sudo aptitude install apache2

...but both say "No candidate version found for..."

Both those methods I got from recent web pages about Ubuntu. It's rather frustrating. Any clues?

---

### Post by louieb on 2009-12-27
Commands you ran look just fine. Check your software sources.
System>Administration>Software Sources.

If your still have problems please copy file **/etc/apt/sources.list** in your next post.

---

### Post by Cheesemill on 2009-12-27
Have you updated your sources since you installed? Try doing this:
```
sudo apt-get update
```and then try the *apt-get install* commands.

---

### Post by aplonis on 2009-12-31
Thank you both. 

What it was... Having been away from Ubuntu since a brief flirtation with version 6.06 on a laptop some years ago, I had forged ahead, without having first enabled the Multiverse and Universe repositories.

---

