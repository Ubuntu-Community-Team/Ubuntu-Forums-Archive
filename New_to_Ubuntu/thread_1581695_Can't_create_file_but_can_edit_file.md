---
title: "Can't create file but can edit file"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by jreiley on 2010-09-25
I am rather a beginner in the Linux world.  My problem is I can't create a file on my server.   A little background.   The server I am working on is at my home and is used as a development machine.  This machine was built by an employee of mine a couple weeks ago.   I live in the Midwest, the office is in NY so it's not always easy to get help from him.   Anyway the Ubuntu server is part of a novell network.  Workstations are XP and W7.  When I try to move a file from my Windows machine to the linux box, it won't allow me to create the file on Linux.   Help would be appreciated.

Jim

---

### Post by theozzlives on 2010-09-25
Where you trying to copy the file? If it's somewhere that requires root permissions, try the following:

Press F2 and type:
```
gksu nautilus
```

After password verification, you'll get the "File Manager" with root permissions. You can then copy/move the file to the desired destination.

---

### Post by The Cog on 2010-09-25
Are you aware that in general, users in Linux (or unix in general for that matter) are not allowed to create files outside of their home directory? If you knew that, ignore this post. Your home directory is /home/username and you should be able to create and edit files in there without restrictions. To go outside your home directory, you need to have extra permissions. You can start a file explorer that has root's privileges with the command gksu nautilus (as theozzlives said) but I would recommend against doing so - staying within your home directory is what you should normally be doing.

That said, I don't know how samba (the service that shares files with windows machines) deals with usernames and permissions, so I could be barking up completely the wrong tree.

---

### Post by jreiley on 2010-09-26
Thanks for the help - but I need to create Btrieve and Oracle tables in directories other than my home.  All 150 of my users access these tables on our production system.  Granted I am configuring my home server just for me but I have to emualate the office environment or the software developed won't work in both places.   Thanks again.

---

### Post by jreiley on 2010-09-26
gksu is/was not installed on my server.  There is no graphical interface installed on the server.  I install gksu and when I try to run it I get "cannot open dispaly" which makes sense.

---

### Post by qamelian on 2010-09-26
Since you aren't working in a gui, use sudo. the command gksu is only for launching gui applications.

---

### Post by jreiley on 2010-09-27
Since the graphic interface is not installed on my server, can I install it without too much pain?  If not, how can I remove the software I just installed?

---

### Post by Paqman on 2010-09-27
> **jreiley said:**
> Since the graphic interface is not installed on my server, can I install it without too much pain?

It's easy to install, but it's a big download, and then you'd need to set up remote desktop. And since it would be of highly dubious usefulness i'm going to say "too much pain"


> If not, how can I remove the software I just installed?

```
sudo apt-get remove gksu && sudo apt-get autoremove
```

The first command uninstalls gksu, the second uninstalls any dependencies it might have pulled in.

---

