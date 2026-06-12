---
title: "Questions on samba security settings and uShare"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by kevmev12 on 2009-05-03
Hi, I'm a bit of an Ubuntu n00b so please be gentle!! I've installed the desktop and server edition a couple of times over the last week on both a laptop and desktop - and although the learning curve was a little steep, I finally got the hang of the installation and usage. I've used an unused desktop PC and installed Ubuntu 9.04 server edition on it - I've got root on an 80GB HDD, and installed two 1TB HDDs in an Ubuntu software-controlled RAID1 configuration with /home on it. This is my home file server, and it is working very well - with samba, I can access and modify files and folders on my Windows laptop, and I've got uShare installed so the Xbox 360 can see my movie files (although I have a problem with Xbox not seeing the music folder properly, but I've since found that it's more a limitation with the Xbox, not with uShare or Ubuntu).

My questions is basically on samba and the security settings on file and folder access. I've found that when I try to access my shared folders on my Windows laptop and one other Windows desktop, Windows never asks me for my username or password. Does that mean that if anyone connects to my network, they can see my shares? Is it possible to set the security so that only my laptop and Xbox can access my shares without restrictions or ask for username/password, but if I try to access my shares with my desktop or any other 'foreign' computers, a username/password is asked everytime?

I've done a bit of research on this issue and found that most people actually want the authentication to stop when accessing their shares. Although the only likely person to access my shares is me anyway as I live alone, I have enabled wireless access on my router so I'm just being security conscious; it's also to control share access to any friends that may bring their laptop/iPhone over to my place.

Also just a quick question on uShare - do I have to stop and restart uShare everytime I add/delete a file and/or folder?

Thanks for reading my questions.

---

### Post by nhasian on 2009-05-03
Hello kevmev12,

I love uShare and use it everyday on my 360.  I dont think it works with mp3s though.  At least I've never gotten it to work with MP3s.  You may want to try out fuppes [http://fuppes.ulrich-voelkel.de/download/](http://fuppes.ulrich-voelkel.de/download/) svn636 is the most recent version.  fuppes is a bit more complicated to setup but it has many more options.

as for your security question, you could put firewalls on your computers and tell them to only accept smb connections from an approved list of computers.

---

