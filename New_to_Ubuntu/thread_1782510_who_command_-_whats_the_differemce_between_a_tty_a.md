---
title: "who command - whats the differemce between a tty and a pts"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-14
sam@HP:~$ who
sam      tty7         2011-06-14 23:15 (:0)
guest    tty8         2011-06-14 23:15 (:1)
guest    pts/0        2011-06-14 23:16 (:1.0)
sam      pts/1        2011-06-14 23:17 (:0.0)

---

### Post by el_koraco on 2011-06-14
[http://linux.die.net/man/4/pts]("http://linux.die.net/man/4/pts")

---

### Post by sisco311 on 2011-06-14
[http://en.wikipedia.org/wiki/Tty_(Unix)](http://en.wikipedia.org/wiki/Tty_(Unix))

pts/[0-9]+ is the filename of a pseudo terminal (xterm, gnome-terminal...)
and
tty[0-9]+ is the filename of a [virtual console]("http://en.wikipedia.org/wiki/Virtual_console").

---

### Post by kalimojo on 2011-06-14
> **el_koraco said:**
> [http://linux.die.net/man/4/pts]("http://linux.die.net/man/4/pts")

Way over my head

---

### Post by kalimojo on 2011-06-14
> **sisco311 said:**
> [http://en.wikipedia.org/wiki/Tty_(Unix)](http://en.wikipedia.org/wiki/Tty_(Unix))

pts/[0-9]+ is the filename of a pseudo terminal (xterm, gnome-terminal...)
and
tty[0-9]+ is the filename of a [virtual console]("http://en.wikipedia.org/wiki/Virtual_console").

How do I tell if someone is logged in remotely ?

---

### Post by sisco311 on 2011-06-14
If the user is logged in from a remote machine, then *who* displays the host name of the machine as well.

```

root   tty1   Jul 24 10:13
joe    pts/0Aug 1 14:17 (**somehost.com**)

```

---

