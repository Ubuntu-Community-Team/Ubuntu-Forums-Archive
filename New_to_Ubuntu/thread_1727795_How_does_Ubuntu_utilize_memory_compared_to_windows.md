---
title: "How does Ubuntu utilize memory compared to windows?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by Olivier 22 on 2011-04-12
I've just recently started to use Linux and I have a lot of questions about maintenance, security, defrag  etc and of course the thread question.
Is there a one source manual for all of this? I've been seduced by this OS.

---

### Post by kaldor on 2011-04-12
> **Olivier 22 said:**
> I've just recently started to use Linux and I have a lot of questions about maintenance, security, defrag  etc and of course the thread question.
Is there a one source manual for all of this? I've been seduced by this OS.

_Security_ 
- Download most everything from the repos (Software Centre)

- Don't run sudo or root blindly

- Don't run commands without reading about what they do. For example, *rm -rf* will delete everything on your system without warnings

- Use common sense.

_Defrag_

- Unless you did a WUBI install, it isn't needed.


There are a few places to look for Ubuntu help. Here's a community made guide, for example: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Good luck :)

---

### Post by K_45 on 2011-04-12
Look at the link in my sig for info on a whole lot of topics. Google also helps. For RAM look here:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by earthpigg on 2011-04-12
Ubuntu uses memory how you tell it to. Preload, swappiness, and many other tools let this be fine tuned.

For advanced users with buckets of ram on their system, [ramdisk]("http://en.wikipedia.org/wiki/Ramdisk") is an option that can result in basic desktop performance that is [instantly significantly faster]("http://en.wikipedia.org/wiki/Ramdisk#Performance") than any system of any specification (including multi-million dollar supercomputers) and any operating system *not* using ramdisk.

you will probably be interested in this, to get started: system -> administration -> system monitor.

and: 

```
sudo apt-get install htop
htop
```

---

### Post by Olivier 22 on 2011-04-13
Thanks to everyone.
I'm really having fun with this.

---

