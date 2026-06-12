---
title: "Home on a external HD"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by Maupertus on 2008-01-18
Hiya guys,

were working on the network of the Student Union at the moment. The idea we had was to have 8 workstations that connect to a Network Attached HD which can be approached via it's own ip-adress to house all the userprofiles. This way, every user can access his or her profile from each workstation.

Now, apart from the fact that the Uni has given us some crap Architecture to work with here, I wanted to know if this can be done and how?
Most of us three (we were suckered into this little chore) have a good working knowledge of Linux and no it can be done, only we want to have some back up knowledge before breaking to many pc's ;)

So if you can help, please let me (us) know.

Thanks!

---

### Post by clsgis on 2008-01-18
You could put your users' home directories on an NFS exported volume.

It seems to me your actual requirement is a little more than home directories outside the machine.  If it's semi-public access, you want a clean new workstation to appear with each new session, not eight workstations you have to maintain one by one.  Take a look at the Linux Terminal Server Project.  Especially if the workstations are underpowered.  You need one burly compute server with tons of RAM.  (You'll be amazed at the performance when everybody is running the same copy of Firefox etc.  When you come to run yours it's already in memory...  It's the magical "shared text" part of demand-paged virtual memory with shared text.)   Then the workstations are little more than X terminals.  Any particular workstation can blow up and you just swap it out.

[http://www.ltsp.org](http://www.ltsp.org)

---

