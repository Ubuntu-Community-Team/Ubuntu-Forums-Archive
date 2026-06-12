---
title: "using connect to server"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by ja660k on 2010-02-24
hey guys,
i always use connect to server app that comes with ubuntu.
but i find it quite annoying that everytime i log in, i need to enter in the address and username all over again, is there a way to automate this, so i can click a icon and it will automatically connect?

can this be done using that app?
or should i write launchers that will invoke a sshfs command?

thanks

---

### Post by spiderbatdad on 2010-02-24
Nautilus, your file browser, will bookmark these connections for you, assuming you use Nautilus in browser type windows with a places menu on the left hand side. In the connect to server dialog you should see an add bookmark option.

---

### Post by undecim on 2010-02-24
How about setting up public key authentication? It's more secure than using a password, and everything happens behind the scenes.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins)

---

### Post by spiderbatdad on 2010-02-24
Public key auth is a very good idea but doesnt address the issue of not having to re-enter login information (ie. command, user, server) every time. After public key is established bookmarking is the simple solution.

---

### Post by Iowan on 2010-02-24
If you always connect - and the "share" is always available, would an [fstab]("http://ubuntuforums.org/showthread.php?&t=283131") entry work?

---

