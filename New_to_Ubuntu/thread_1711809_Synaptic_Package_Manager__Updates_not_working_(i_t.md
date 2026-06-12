---
title: "Synaptic Package Manager / Updates not working (i think i broke them)"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by thiefzer0 on 2011-03-21
I already posted this a little bit ago in another thread but I figured I would make a new one so it grabs the right peoples attention.  Here is my post, I see no reason to re-edit: :D


Hi everyone!  I am new here as well.  I briefly tried Ubuntu on my  netbook about a year ago but it wasn;t fully supported yet so I gave up  (got overly confused trying to enable some "hacks" for my atheros wifi  card) and uninstalled.

Anyways, I installed Ubuntu 10.10 Netbook Remix last night, everything  installed fine.  I set up a 6 GB parition to play with, and of course a  swap partition.  I was trying to install java (not realizing it was  preinstalled) and the minecraft (a game) client last night and some  tutorial had me doing alot of terminal commands i am not yet familar  with.  Apparently i broke something because now when I try to open  synaptic package manager or run the updates i get the same error that  reads:

Could Not Resolve the Packaged Information

An unresolvable problem occurred while initializing the package information.  

Please report this bug against the 'update-manager' package and include the following error message:

E:Malformed line 61 in source list /etc/apt/sources.list (dist parse)'.


I followed some other instructions and managed to use the sudo command  in terminal to use gedit to open the source file, enabled numbered lines  and found line 61.  I don't know but it looked perfectly fine to me.   Should I attach the file so you guys can tell me whats; wrong?  I will  go ahead and post several lines including line 61 so you can see what's  wrong.  I do however distinctly remember in the terminal doing something  involving canonical, which happens to be in the line(s?) throwing error  messages.  I will paste them in now.

This is line 50-64 from the sources.list file:

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner


thanks guys!

Chris Ameigh
[EMAIL="ameighc@gmail.com"]ameighc@gmail.com[/EMAIL]


-edit
I am also copy pasting the error from synaptic:

An error occurred
The following details are provided:

E:Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E:The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open() failed, please report.

---

### Post by yeats on 2011-03-21
> **thiefzer0 said:**
> 
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner


These are duplicate lines.  You might try doing

```
sudo gedit /etc/apt/sources.list
```

And removing the first two of these four, then do

```
sudo apt-get update
```

to see if it works.

---

### Post by linuxman94 on 2011-03-21
You need to delete lines 61 to 64 because as you can see they point to the lucid repositories and you are running maverick.  Once you delete them, you can enable the partner repositories from synaptic.  Just go to Settings -> Repositories and click "Other Software" then check the tick box next to "Canonical Partners."

---

### Post by thiefzer0 on 2011-03-21
> **linuxman94 said:**
> You need to delete lines 61 to 64 because as you can see they point to the lucid repositories and you are running maverick.  Once you delete them, you can enable the partner repositories from synaptic.  Just go to Settings -> Repositories and click "Other Software" then check the tick box next to "Canonical Partners."

Ok I have sucessfully deleted lines 61-64 and saved.  Might I ask where the Settings -> Repositories is located?  I am on the netbook remix so sometimes I can't find things where people send me to look for them.  Thanks again for the quick response!

Chris

---

### Post by linuxman94 on 2011-03-21
Sorry i should have been more clear.  It is in synaptic package manager

---

### Post by yeats on 2011-03-22
> You need to delete lines 61 to 64 because as you can see they point to the lucid repositories and you are running maverick. 

Good catch!  I completely missed that ;-)

---

### Post by Paqman on 2011-03-22
> **yeats said:**
> These are duplicate lines.  You might try doing

```
sudo gedit /etc/apt/sources.list
```


Just a small point: you should use gksudo instead of sudo. Sudo is only used for command line apps, not graphical ones like gedit.

---

### Post by thiefzer0 on 2011-03-22
Thanks for the pointers!  I have the updates/software manager working!  Getting skype now :))  Also I got java working when I realized there was a built in program to run executable .jar files.  Good to go until my next question, thanks :)

---

