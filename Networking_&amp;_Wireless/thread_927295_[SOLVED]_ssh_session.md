---
title: "[SOLVED] ssh session"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Stolea on 2008-09-22
Silly question of the day:
In the Howto instruction on networking it says
```
WARNING! These examples may stop remote networking service if executed. Always, use restart option over ssh session.

$ sudo /etc/init.d/networking start

$ sudo /etc/init.d/networking stop
```

Unfortunately I have no idea how to run a ssh session. I have opensshserver installed, but that's as far as I can work out what to do. I am pretty sure this is something pretty basic, but at this point a bit beyond me.

---

### Post by Iowan on 2008-09-22
What it seems to be saying is: If you have an SSH connection and try to run ```
$ sudo /etc/init.d/networking stop
$ sudo /etc/init.d/networking start
``` The first command will shut down networking (thus the SSH session, and the second command cannot be received to bring the connection back up). The **sudo /etc/init.d/networking restart** will still lose the SSH session, but the machine will at least be available to reconnect.

Have you seen [this]("https://help.ubuntu.com/community/SSHHowto") How-To?

---

### Post by Stolea on 2008-09-22
I think I got the idea. Networking in Ubuntu is still a bit of a mystery to me. I sort of got it working, but it tends to be a bit temperamental.
I guess its all a part of the learning curve.
Cheers

---

