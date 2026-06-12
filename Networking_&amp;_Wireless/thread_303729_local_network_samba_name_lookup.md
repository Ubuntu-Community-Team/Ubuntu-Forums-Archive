---
title: "local network samba name lookup"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by GaryMc on 2006-11-20
I have a small home network:

1 x debian server (called buzz, ip=192.168.1.200)
2 x XP machines (woody & jessie)

Now (as in yesterday!) I have installed ubuntu 6.10 onto another machine.
I have managed to install samba, and using the network browser I can browse the "Windows networks" and I can see the machines.

What I want to do from the ubuntu machine (which I can already do from the windows ones) is to be able to http: to the apache on buzz, and also ssh into that machine.
However, using "terminal" and
ssh buzz
I get
ssh: buzz: Name or service not known

If I use firefox and use [http://buzz/](http://buzz/) I get sent to a "yellow pages" site.

Is there something I can do to enable the windows machines to be resolved to IP addresses?
(I know I could add them to the hosts file - the machines all have fixed IP, so that's possible; but I'd rather see if there was a "better" way).

If this is just a really simple "noob" question, I'd appreciate a pointer to the relevant FAQ/Documentation; don't mind spending some time reading up, but a Yahoo search isn't giving me any help, maybe I'm just not entering the correct search string.

---

### Post by spd106 on 2006-11-21
If you don't have or want a DNS server then winbind is probably the way to go. There are pages in the wiki and several forum threads about it.

---

### Post by GaryMc on 2006-11-21
ok, thanks for the pointer, I'll check that out

---

### Post by scrooge_74 on 2006-11-21
This may give  you some light on the subject, is from another thread and it was very usefull to me.

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

---

