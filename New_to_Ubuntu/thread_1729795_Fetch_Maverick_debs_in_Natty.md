---
title: "Fetch Maverick debs in Natty"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-04-15
Hello!

I'm trying out Kubuntu 11.04 and I like it. Now I want to test it under more than just surfing around conditions, so I wanted to install the texlive deb to work a little bit. As my bandwith is limited and all of texlive-full is already stored on another computer with apt-cacher-ng, I was wondering whether I could just get the packages from there via the *--target-release* option in apt-get.

Will using the old packages break something? I think it shouldn't as the texlive packages shouldn't have changed too much, but still asking doesn't hurt.

Question 2: Might the use of an Maverick apt-cacher-ng from a Natty machine break the cacher?

Thank you very much,

Blutkoete

---

### Post by Paqman on 2011-04-15
> **Blutkoete said:**
> 
Will using the old packages break something?

Nope, as long as the package manager can satisfy all the dependencies it will go ahead and install it.

---

### Post by Blutkoete on 2011-04-15
Thank you!

But what am I doing wrong?

```
sudo apt-get -t maverick install texlive-full
```still tries to download the Natty packages. Are those packages *pinned* (whatever that means) or is the *-t* option not availabe in Ubuntu? Or am I using the wrong syntax?

EDIT: Gosh is Google fast. If I google for "sudo apt-get -t maverick" my posting here is already #1. But the second entry hints that my syntax should be ok.

---

### Post by Blutkoete on 2011-04-15
Ah, I actually solved my problems by using a Texlive 2010 DVD. No updates, but should be working.

Does anyone know a way to install Kile via apt-get without it installing texlive packages? Everything is there, the paths are set, but of course Kubuntu thinks that Texlive is not installed and obviously wants to install it with Kile.

The *--no-recommended* option isn't enough, still wants to install at least texlive-base.

Thank you!

---

