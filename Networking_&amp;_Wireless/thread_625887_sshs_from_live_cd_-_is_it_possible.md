---
title: "sshs from live cd - is it possible?"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by lptr on 2007-11-28
Could please anyone telling me, if it is possible to (and if so how to temporary installing &) using [COLOR=Red]***sshfs***[/COLOR] when booting from a Gutsy [COLOR=Red]Live CD[/COLOR]?

Thanks

rob*

---

### Post by spd106 on 2007-11-29
Is this an ssh client or server?

You can use the command line ssh client from the live cd quite easily, it's in the live image. You can also use Nautilus to connect via ssh using Connect to Server.. from the Places menu.

If you want an ssh then you'll have to install openssh, which should be quite easy as long as you have an Internet connection.

There are a few wiki pages about setting up ssh, [https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ssh&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ssh&titlesearch=Titles)

---

### Post by lptr on 2007-11-29
No, it should be the server. Using ssh as client is clear. It is part of my daily work 

The goal is the following. Duplication of a (still) running server machine which is to old to shutdown - data loss is very possible.

The old machine (name it A) has openssh server and client installed. Machine B should do the work to mount via sshfs the old drives (one after one) to copy all 1:1 over to new storage. 

So it would be perfect to have sshfs on the live cd system, to mount the drives of A (mount points of them) to B.

rob*

p.s. Today evening I will setup a rudimentary Ubuntu system to get sshfs installed on it (call it plan B ;-) ). I want to see if this works as expected.

---

### Post by spd106 on 2007-11-29
openssh-server is not on the desktop CD, so you'll have to apt-get install or download the package and then transfer it over.  If you have the DVD then you can use that instead because it has it in it's package pool.

I'm not sure where the live environment installs these files to but it seems to work. I heard someone used it to recover a system when the binary nvidia driver messed up their video card.

---

### Post by lptr on 2007-11-29
DVD - good idea! Thanks that will maybe bring me to the solution. I will try this out after downloading DVD.iso.

A somehow OT question (but regarding to rescue the old box data):
In my logic the failure is to mount to the mount points. The stupid thing is that the other box has / , too (of course). This mounts also /var for example.

And I will do, after mounting it with sshfs:
$ cd /OLD
$ tar -cSp --numeric-owner -f - . | ( cd /NEW && tar xSpvf - )
this will bring over data, links and so on, really all inclusive rights.

Luckily on the new datastore /NEW is big enough to store complete /OLD inclusive OLD/var.

What would be the most elegant way to bring over all files&dirs in /NEW except this /NEW/var dir to another partition (assuming to have mounted it under /OTHER).

Any ideas?

rob*

---

