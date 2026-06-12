---
title: "&quot;: ( ) { &quot;: | : &amp; } ; :&quot; on linux terminal"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by anantshri on 2011-04-09
Hi,

what does following sequence perform when typed on linux terminal

: ( ) { : | : & } ; :

my gnome-terminal gets stuck and i need to reboot my system

want to know what is actually happening

---

### Post by ubuntu27 on 2011-04-09
> **anantshri said:**
> Hi,

what does following sequence perform when typed on linux terminal
[SNIP! Censored]

my gnome-terminal gets stuck and i need to reboot my system

want to know what is actually happening

Oh, no! You got pwn'ed. (I bet someone tricked you to run that code)

I cannot explain it well, but, it is a really bad code.
If I remember correctly, it causes applications to consume a lot of RAM which makes your computer slow.

But, there is more than that. Let wait for someone more knowledgeable.

---

### Post by Daniel0108 on 2011-04-09
> **anantshri said:**
> Hi,

what does following sequence perform when typed on linux terminal

: ( ) { : | : & } ; :

my gnome-terminal gets stuck and i need to reboot my system

want to know what is actually happening

This starts an empty function again and again, and this function consumes ram, not much, but it consumes ram.
The problem is, the function gets started again and again, until your RAM is full and your computer gets slow, because it has to use SWAP. After a short time your computer gets stuck.

If you want to stop this, you can set a maximum process limit ;)

Yours,
Daniel

---

### Post by sisco311 on 2011-04-09
It's a fork bomb:
[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

---

### Post by gerowen on 2011-04-09
If you're just trying to reboot your system via command line you can do it with:

```

sudo shutdown -r now

```

---

### Post by Daniel0108 on 2011-04-09
> **gerowen said:**
> If you're just trying to reboot your system via command line you can do it with:

```

sudo shutdown -r now

```

You misunderstood him, he wants to know what a forkbomb does. and he says he HAD TO reboot after the forkbomb :P

Yours,
Daniel

---

### Post by gerowen on 2011-04-09
> **Daniel0108 said:**
> You misunderstood him, he wants to know what a forkbomb does. and he says he HAD TO reboot after the forkbomb :P

Yours,
Daniel

Ah, I thought he was trying to restart and someone gave that to him as the command to do it, :p

---

### Post by Paddy Landau on 2011-04-09
If you want to understand how this works, have a look at a [thread where I asked about it]("http://ubuntuforums.org/showthread.php?t=1392511") last year.

---

### Post by anantshri on 2012-06-05
Thanks for all the responses..

i did extensive study of this fork bombs and found a lot 
this article here talks about ways to prevent it.

[http://jbakshi.50webs.com/Linux_tutorial/Fork_bomb/forkbomb.html](http://jbakshi.50webs.com/Linux_tutorial/Fork_bomb/forkbomb.html)

Hope this could help someone.

---

### Post by Elfy on 2012-06-05
Old thread closed.

---

