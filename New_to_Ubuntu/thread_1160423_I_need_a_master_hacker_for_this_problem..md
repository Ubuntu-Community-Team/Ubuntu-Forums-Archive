---
title: "I need a master hacker for this problem."
date: 2009-05-15
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-05-15
Well I made my repository, but in my live cd state, which is chroot edit,

How can I put in a code to apt of that state to go into my main file system of my hard drive to look at the repositories I have made.

Like if I do a chroot edit apt-get install mplayer

How can I tell it to go to my repository, which is at /repo ( my main file system) of my hard drive.

Anyone have a solution, or should I just move my repository into the edit folder, so it can see it.

---

### Post by e_james on 2009-05-16
I am not a 'master hacker' which means I am not sure exactly what it is that you are trying to do but I believe I can offer some suggestions so that you can make progress yourself.

I think you need to edit the file /etc/apt/sources.list. You can edit it as text or you can use the gui application System - Administration - Software Sources. If you look at the last few lines you should see that part of the info. is a URL which you can look up using Firefox. I believe what you want to do requires additional lines pointing to your local directories.

---

