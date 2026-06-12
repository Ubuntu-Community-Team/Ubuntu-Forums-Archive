---
title: "question about processes on system monitor"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-13
among others i have  processes running named "sh","seahorse-agent","gvfsd","su-to-root" and "bash".
could you give me a simple description about what they do and if i really need them?

---

### Post by K7522 on 2009-09-13
> **heyyy said:**
> among others i have  processes running named "sh","seahorse-agent","gvfsd","su-to-root" and "bash".
could you give me a simple description about what they do and if i really need them?

sh is a shell process in a zombie state, you can find info about zombie states here; [http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

Seahorse is an app for managing PGP keys. It's integrated into nautilus, gedit and other places for encryption and decryption for GNOME.

gvfsd is a virtual filesystem for GNOME, I don't know much about it.

su-to-root is just a simple script for dealing with su; [http://manpages.ubuntu.com/manpages/hardy/man1/su-to-root.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/su-to-root.1.html)

bash is a shell for interpreting commands, and stands for Bourne-Again SHell. It is Ubuntu's default shell.

---

