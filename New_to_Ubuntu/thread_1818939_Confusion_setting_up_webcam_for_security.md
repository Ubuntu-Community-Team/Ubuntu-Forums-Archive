---
title: "Confusion setting up webcam for security"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by adobrakic on 2011-08-05
Hey everyone,

I need a little (a lot) assistance setting up my webcam as a security system. I've found plenty of tutorials that say to use Motion, but there are always parts of the tutorial with dead links. I've tried figuring out what the tutorial is mainly aiming to do, and attempting it manually, but I always fail. If anyone can help me, I'd greatly appreciate it.

For starters, I have Ubuntu 10.10, 64bit. I'd like my webcam to begin recording whenever it detects movement in front of it, and save that recording to a certain folder. If possible, I'd like it to only record during specific times of the day, but it isn't necessary. 
Also, would this interfere with me being able to use other programs that utilize my webcam, such as Skype?

Thanks!

---

### Post by madjr on 2011-08-05
you mean tutorial like this one:

[http://www.paulanthonywilson.com/blog/setup-a-webcam-security-system-with-ubuntu-linux/](http://www.paulanthonywilson.com/blog/setup-a-webcam-security-system-with-ubuntu-linux/)

or this older one
[http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)


whats wrong with them?

---

### Post by adobrakic on 2011-08-05
I don't understand what I'm doing wrong. I get motion running in terminal, and it says it's saving to /tmp/motion, but when I go to that folder, there's nothing there.

---

### Post by realzippy on 2011-08-05
Did you install motion from regular sources?
Normally default saving location is your user's home folder.


edit:
I see,you started motion as root.
Try without "sudo" ..

---

