---
title: "Why should I use gksudo gedit instead of sudo gedit"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by swerdna on 2009-06-30
Hello, I have Ubuntu 9.04.

I edit configuration files while I'm setting up Ubuntu.
I see much advice to use "gksu gedit"  or "gksudo gedit" to edit files. But also "sudo gedit" works just fine too.

Please explain why there are three options and which is the recommended option and why.

PS what would it be in Kubuntu. I note that "sudo kate" works in my Kubuntu. Should I be using like "kdesu kate"?

Thanks
swerdna

---

### Post by Paqman on 2009-06-30
[Why to use gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo").

gksu and gksudo are effectively the same thing. And yes, kdesu for KDE.

---

### Post by porchrat on 2009-06-30
From the manual page of gksudo & gksu:

> DESCRIPTION
       This manual page documents briefly gksu and gksudo

       gksu  is a frontend to su and gksudo is a frontend to sudo.  Their pri-
       mary purpose is to run graphical commands that need  root  without  the
       need to run an X terminal emulator and using su directly.


EDIT: Sorry just realised that didn't really answer your question luckily my lack of comprehension was countered by the the response before mine.

---

### Post by swerdna on 2009-06-30
OK, that all makes sense, in light of the link, thanks.

And I see from "ls -l /usr/bin | grep gksu" that gksudo is now just a pseudonym for gksu in Ubuntu.

So gksu and kdesu for me from now on.

Another little thing laid to rest :)

---

