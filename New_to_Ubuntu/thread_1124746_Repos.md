---
title: "Repos"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by rick astley on 2009-04-13
Hi all,

can someone please explain to me about "Repositories" that i have been hearing all about lately.

Any info is appreciated.


Thanks,
rick.

---

### Post by eeeandrew on 2009-04-13
The repositories are basically databases full of free software. The package manager connects to the repositories to download the packages that install software. If you click Applications->Add/Remove a list of available software from the repositories appears. If you check System->Administration->Software Sources you can see a list of the available repositories. Its also possible to create links to new repositories hosted by individuals or other companies. For example, the mediubuntu repository contains software from Skype, Adobe etc that are not open source but can be downloaded free. Its not recommended to add new repositories if you don't know whats in them.

Hope this helps,
Andrew

---

### Post by djbushido on 2009-04-13
Repositories are just big servers that gather a lot of programs etc. and put them together for you. This is also due to the fact that some programs are hard to compile (like the kernel) so it is easier to just distribute software like this in one central location.
In a nutshell, a repository is a big download location, like FilePlanet, only free.

---

### Post by SunnyRabbiera on 2009-04-13
The best way to explain how a repository works is to compare it to a library, its sort of like that.
It can also be compared to a Video rental store too, though everything is free and there are no late fees :D

---

### Post by Mortus Pryde on 2009-04-13
I am wondering, I added the mediubuntu repository and when I search anything in it does not show up, I have to manually go to the repository in Synaptic to access any programs inside. Is this normal of non out-of-the-box repositories?

---

### Post by Paqman on 2009-04-13
> **Mortus Pryde said:**
> I am wondering, I added the mediubuntu repository and when I search anything in it does not show up, I have to manually go to the repository in Synaptic to access any programs inside. Is this normal of non out-of-the-box repositories?

I don't quite understand what you mean.

Let's take an example of an app that comes from Medibuntu: Skype. If you go to Synaptic and search for Skype, what happens?

---

### Post by Mortus Pryde on 2009-04-13
It shows no results, and Google Earth only came back with the Deb creator which is in one of the preinstalled repositories for Ubuntu and did not show Google Earth in the repository.

---

### Post by SunnyRabbiera on 2009-04-13
> **Mortus Pryde said:**
> I am wondering, I added the mediubuntu repository and when I search anything in it does not show up, I have to manually go to the repository in Synaptic to access any programs inside. Is this normal of non out-of-the-box repositories?

You have to reload the sources list once you add a new repository.
Its not automatic, its sort of like adding a store inside of a mall... it doesn't open right away :D

---

### Post by Mortus Pryde on 2009-04-13
Next question, though I believe I tried several times, being new and all maybe did it wrong. ;) How to I relead the list?

---

### Post by SunnyRabbiera on 2009-04-13
In synaptic just hit the "reload" button :D

---

### Post by Mortus Pryde on 2009-04-13
Hmmmm... K did that... several times. :| When I did after adding the new repository the count to be updated went from 42? to 53, but anything in the new repository does not come up in search.

---

### Post by SunnyRabbiera on 2009-04-13
Hmm, try a log out and hit reload again after logging back in.

---

### Post by Mortus Pryde on 2009-04-13
In this case you mean fire it up when I get home and try, try again. ;) I am sure I have relogged enough times between my last attempt and now that it either works or it won't.

---

### Post by albinootje on 2009-04-13
> **rick astley said:**
> can someone please explain to me about "Repositories" that i have been hearing all about lately.


See here : [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
And perhaps also here : [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by Mortus Pryde on 2009-04-13
BTW, Sorry if I Hijacked the thread.

---

### Post by SunnyRabbiera on 2009-04-13
> **Mortus Pryde said:**
> BTW, Sorry if I Hijacked the thread.

Its fine as your issue is related to the subject matter, its not like you came in here and asked us what kind of pop tarts we like or something (but if you are curious I like the smores ones ;))

---

### Post by Mortus Pryde on 2009-04-14
Well mediubuntu finally became seachable, only took another component needing an update to work right. Wierd if you ask me, but who knows.

---

