---
title: "Looking to install Wine-Doors in Ubuntu 10.10"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by dan2794 on 2010-11-05
Hello everyone!

I'm looking to switch to Ubuntu 10.10, I'm coming from a MS Windows background (XP) However I rely strongly on Macromedia Dreamweaver and Fireworks....

I know there is a simple way to install this using a program called "Wine-Doors" because I did this when I had 10.04 installed...and I tried to install it the same way in Ubuntu 10.10 as before...However I get the following error(s)

[CENTER][U][B]Dependency is not satisfiable: python-gnome2-desktop 

[/B][/U][LEFT]I'm wondering if anybody here can possibly help me resolve the issue(s)

Many thanks in advance,

Dan :)
[/LEFT]
[/CENTER]

---

### Post by kaldor on 2010-11-05
Try using the command: 

```
sudo apt-get install python-gnome2-desktop
```

Report back if there are issues.

---

### Post by dan2794 on 2010-11-06
Hi kaldor,

Thanks for the reply, Just ran the command, I get the following output from terminal:

[B]daniel@Dans-PC:~$ sudo apt-get install python-gnome2-desktop
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gnome2-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-gnome2-desktop' has no installation candidate[/B]

Thanks,

Dan :)

---

### Post by ciberglo on 2010-11-28
Try this:

sudo apt-get install python-gnome2-desktop-dev

---

### Post by dan2794 on 2010-11-28
Hello ciberglo,

Thanks for the reply,

I'm now back using windows, Until I can simply install my web design software, I cannot rely upon linux.

Thanks for the help anyways, Hoping to try ubuntu when the next version is out as I always do!

Have a nice day :D

---

### Post by k50aker on 2011-01-17
Just for the recored, I had this problem and here is how i solved it:

first download and install python-gnomeprint from:

[http://mirror.anl.gov/pub/ubuntu//pool/main/g/gnome-python-desktop/python-gnomeprint_2.30.0-0ubuntu1_i386.deb](http://mirror.anl.gov/pub/ubuntu//pool/main/g/gnome-python-desktop/python-gnomeprint_2.30.0-0ubuntu1_i386.deb)

next download and install python-gnome2-desktop from:

[http://launchpadlibrarian.net/42544535/python-gnome2-desktop_2.30.0-0ubuntu1_all.deb](http://launchpadlibrarian.net/42544535/python-gnome2-desktop_2.30.0-0ubuntu1_all.deb)

```
then sudo apt-get install wine-doors
```

Worked for me.

---

### Post by Jetro on 2011-03-23
> **k50aker said:**
> Just for the recored, I had this problem and here is how i solved it:

first download and install python-gnomeprint from:

[http://mirror.anl.gov/pub/ubuntu//pool/main/g/gnome-python-desktop/python-gnomeprint_2.30.0-0ubuntu1_i386.deb](http://mirror.anl.gov/pub/ubuntu//pool/main/g/gnome-python-desktop/python-gnomeprint_2.30.0-0ubuntu1_i386.deb)

next download and install python-gnome2-desktop from:

[http://launchpadlibrarian.net/42544535/python-gnome2-desktop_2.30.0-0ubuntu1_all.deb](http://launchpadlibrarian.net/42544535/python-gnome2-desktop_2.30.0-0ubuntu1_all.deb)

```
then sudo apt-get install wine-doors
```

Worked for me.
Thanks, this worked for me too. :D

I tried installing, computertemp_0.9.6, for the record.

---

