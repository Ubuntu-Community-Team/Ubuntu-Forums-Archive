---
title: "New network - workgroup share - advice"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by ibizatunes on 2009-02-04
Hello, I’m possible designing a new network, I’m offering my customer 2 options, open source vs ms route and they can pick 

I’m a reasonable Linux user, but I just want to check what configuration I would have to do to complete the task

There is only 3 pc, no internet access as of yet, - I will add a 3G connection when I’m on site to get patches etc
 
I want to 1 of the pc to be a server / desktop with all the home drives pointing to the server / desktop 

To complete this I would have to edit my  /etc/fstab ? and point it to the server / desktop and have a network services like NFS install?

Also I would like a GUI backup software utilities to backup dater (cost isn’t a problem) I would like some recommendation - this is for users to do themselves so easy to use software is a must!

---

### Post by petervk on 2009-02-04
NFS can be used to serve home directories to other computers, and yes you would have to edit your /etc/fstab.

As for backup software, the problem is that there is so many different packages it's hard to recommend one without knowing more. rsync in a cron job can do an amazing job.

---

