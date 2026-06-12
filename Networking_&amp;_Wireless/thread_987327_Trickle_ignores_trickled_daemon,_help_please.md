---
title: "Trickle ignores trickled daemon, help please"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by lesergi on 2008-11-19
Hi all,

I want to limit bandwidth to some apps, for this, I want to use trickle, but trickle totally ignores trickled daemon. I always get 10 K/s connection, trickle's default:

```

lesergi@lesergi-desktop:~$ trickled -d 200 -u 10
lesergi@lesergi-desktop:~$ trickle wget http://ubuntu-releases.sh.cvut.cz/intrepid/ubuntu-8.10-desktop-i386.iso
--2008-11-19 19:12:20--  http://ubuntu-releases.sh.cvut.cz/intrepid/ubuntu-8.10-desktop-i386.iso
Resolent ubuntu-releases.sh.cvut.cz... 147.32.127.222
S'està connectant a ubuntu-releases.sh.cvut.cz|147.32.127.222|:80... conectat.
HTTP: Petició enviada, esperant resposta... 200 OK
Longitud: 732766208 (699M) [application/x-iso9660-image]
S'està desant a: «ubuntu-8.10-desktop-i386.iso.13»

 0% [                   ] 65.536      9,99K/s  eta 19h 53m

```

I don't know if I use wrongly trickle or maybe it's a bug.

Thanks a lot!!

---

### Post by lesergi on 2008-11-19
Well, I already solved this problem.

The problem was I must specify in trickle command download and upload limits too.

```

trickled -d 200 -u 10
trickle -d 200 -u 10 1stCommand
trickle -d 200 -u 10 2ndCommand
...

```

Bye!

---

### Post by SpmP on 2008-11-23
> **lesergi said:**
> Well, I already solved this problem.

The problem was I must specify in trickle command download and upload limits too.

```

trickled -d 200 -u 10
trickle -d 200 -u 10 1stCommand
trickle -d 200 -u 10 2ndCommand
...

```

Bye!
 sortof...
When you start the trickled service you need to specify some socket for it to create and monitor, this will be somewhere where the user has write access. Then when you start trickle you must specify this socket. eg:
```

trickled -d 200 -u 10 -n /tmp/trickle.socket
trickle -n /tmp/trickle.socket 1stCommand
trickle -n /tmp/trickle.socket 2ndCommand

```

You can do other fun stuff, like give average rates of download/upload withthe -N second... see the man page.

Good luck

---

### Post by lesergi on 2008-11-23
Hi!

Thanks for your reply.

I did what you say but it does not work:

```

lesergi@lesergi-desktop:~$ trickled -d 200 -u 10 -n /tmp/trickle.socket
lesergi@lesergi-desktop:~$ trickle -n /tmp/trickle.socket wget http://releases.ubuntu.com.ba/intrepid/ubuntu-8.10-desktop-i386.iso
--2008-11-23 11:47:59--  http://releases.ubuntu.com.ba/intrepid/ubuntu-8.10-desktop-i386.iso
Resolent releases.ubuntu.com.ba... 195.222.33.204
S'està connectant a releases.ubuntu.com.ba|195.222.33.204|:80... conectat.
HTTP: Petició enviada, esperant resposta... 200 OK
Longitud: 732766208 (699M) [application/x-iso9660-image]
S'està desant a: «ubuntu-8.10-desktop-i386.iso.1»

 0% [                                   ] 16.384      10,0K/s

```

---

