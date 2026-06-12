---
title: "trying to set up pidgin updates"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by eldutcho on 2009-10-20
Hello, I'm trying to set up pidgin so i get updates for it, as per teh instructions on this page
 [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/) 

however, after I enter the first command in the terminal, it just hangs after requesting to key until it times out about 5 minutes later. Is there something I'm doing wrong? I have multiverse and universe repos enabled

msi wind netbook U100

thanks in advance for any help

---

### Post by rs_man on 2009-10-20
I do believe that it would be much easier installing it through Add/Remove Applications. Applications > Add/Remove Applications once that launches change the *Show* option to 'All available applications'. Then type the name of the application you are looking for in the *search* textbox.

---

### Post by Mike_IronFist on 2009-10-20
> **eldutcho said:**
> Hello, I'm trying to set up pidgin so i get updates for it, as per teh instructions on this page
 [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/) 

however, after I enter the first command in the terminal, it just hangs after requesting to key until it times out about 5 minutes later. Is there something I'm doing wrong? I have multiverse and universe repos enabled

msi wind netbook U100

thanks in advance for any help

Don't bother with that method, I tried it, and it doesn't work... their PPA seems to have issues.

Instead, try installing the latest version of Pidgin using the necessary .deb files from getdeb.net:
[http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin")

Just be sure to remove your current version of Pidgin via Synaptic Package Manager before you try to install those .deb files.

The .deb files must be installed in order. If I'm not mistaken, libpurple, followed by libpurple0, then pidgin-data, then pidgin. It's fairly easy to do.

---

### Post by eldutcho on 2009-10-21
Thanks, I'll try mikes suggestion in the a.m.

---

### Post by kevdog on 2009-10-21
Id compile pidgin from mtn if you ask me -- but again that's just me!

---

### Post by mcduck on 2009-10-21
> **Mike_IronFist said:**
> 
The .deb files must be installed in order. If I'm not mistaken, libpurple, followed by libpurple0, then pidgin-data, then pidgin. It's fairly easy to do.
Alternatively you can just install them all at the same time, and dpkg will automatically handle the correct order for you.

Just put the .deb files in the same place, and run "sudo dpkg -i *.deb".

So you only need to worry about the correct order if you want to use the graphical .deb installer. :)

---

