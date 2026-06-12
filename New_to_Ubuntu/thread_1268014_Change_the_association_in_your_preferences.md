---
title: "Change the association in your preferences"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by pirate paul on 2009-09-16
Hi, I am trying totop up my vodafone pay as you go cred. I tried to download some software which I think will make a vodafone box come up, and thus allow me to top up. When I tried to down load what I think I  need, I get >

/tmp/vodafone-mobile-connect 1.99.178 all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I have not got the foggiest idea what that means, I can find preferences but hmmmmm?

I do not know how, or what to change it to, I am not too good with computers, I am learning though. Any bright ideas.

                                                Thanx.

---

### Post by quixote on 2009-09-17
Changing preferences in gnome is waaaay harder than it needs to be.  The simplest thing, for now, is to ignore all that and just do it from the command line.  Then you tell it what to do and you don't get all that backchat.

One thing: it looks like it's put the software in your /tmp directory.  The contents of that dir are generally dumped on shutdown, so if the file has disappeared, that's what happened and you'll need to download again.  (Assuming you're using Firefox, you may want to change your download directory in Firefox preferences.) You may want to move it out of there before installing, in case it decides to install as a subdirectory of /tmp, which would not be good.  For instance:```
mv /tmp/vodafone-and-so-on.deb /home/yourdir/vodafone-and-so-on.deb
```

Open a terminal (Start > Accessories > Terminal).```
sudo dpkg -i /tmp/vodafone-and-so-on.deb
``` (or whichever dir you put it in).  Type "man dpkg" in a terminal to get more information on dpkg (stands for "debian package manager") than you ever wanted.

---

### Post by roger_1960 on 2009-09-17
Hi

I agree it should not be saved in a tmp folder.  To change file type asociations:

In Nautilus (fle manager) right click the file.  Select "properties".  Select the "open with" tab and select the program you wish to have open this file type.  The change is permanent until you change it again.

---

