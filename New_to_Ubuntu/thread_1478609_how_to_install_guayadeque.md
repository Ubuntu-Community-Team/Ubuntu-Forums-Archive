---
title: "how to install guayadeque"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by harry003 on 2010-05-09
guayadeque looks interesting, and I would like to install it.

where do I find it and how do I do it?

it does not turn up in either Synaptic Package manager or Software Center.

---

### Post by dagdeniz on 2010-05-09
they seem to have .deb files on sourceforge; both for lucid and karmic. here:
[http://sourceforge.net/projects/guayadeque/files/](http://sourceforge.net/projects/guayadeque/files/)

---

### Post by harry003 on 2010-05-09
I love sourceforge and have used them many times before, but your link returns a 400 error

---

### Post by eriqjaffe on 2010-05-09
There's a PPA for it which will get you the latest version.  In a terminal:

```
sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn
```

---

### Post by dagdeniz on 2010-05-10
by the way, i clicked now and it worked; unlucky of you. try this (direct link to lucid version for i386):
[http://sourceforge.net/projects/guayadeque/files/guayadeque/0.2.5/guayadeque_0.2.5~lucid-1_i386.deb/download]("http://sourceforge.net/projects/guayadeque/files/guayadeque/0.2.5/guayadeque_0.2.5%7Elucid-1_i386.deb/download")
or this (google search; sourceforge is on the first rank):
[http://www.google.com/search?client=ubuntu&channel=fs&q=guayadeque+sourceforge&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=guayadeque+sourceforge&ie=utf-8&oe=utf-8)

the ppa option is of course better, at least you can get the updates automatically.

---

### Post by harry003 on 2010-05-10
Thank you!

eriqjaffe - your instructions worked properly and I got a good install

dagdeniz - both of your new links also returned a "400 Bad Request" on my box.

weird, huh?

---

### Post by dagdeniz on 2010-05-11
nope! it was a puzzle. a bit trickier that typing ctrl+k guayadeque in firefox, but more fun!

---

### Post by Elfy on 2010-05-11
[Guayadeque Music Player Test request ]("http://ubuntuforums.org/showthread.php?t=1398128")

just in case anyone else finds this thread.

---

