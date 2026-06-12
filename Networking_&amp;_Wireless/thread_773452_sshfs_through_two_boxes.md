---
title: "sshfs through two boxes"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by zackiv31 on 2008-04-28
I use a gateway to connect to my work box, which I ssh into.  I then have to ssh over to my dev box from there, in order to access my files.

I'm trying to mount my dev box as a local drive on my desktop (gnome) so I can work on the files as if they were right there.

does sshfs do what I want?  if so how would you set it up for best performance?  If it won't work, what will?

---

### Post by RDouglasC on 2008-05-05
I use sshfs in a similar fashion... it should work fine for you. I put my mount commands in /etc/rc.local and have the proper keys setup so there's no response required.

---

