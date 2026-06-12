---
title: "package manager SLOW"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by atonalpanic on 2008-04-25
Lately, esp. after the upgrade, package manager has been slow.  Like 1 kb per second slow.  Is this a problem with ubuntu, the developers of the packages, or my computer settings?

---

### Post by jetsam on 2008-04-25
I think the servers are just getting over-worked by the Hardy release.  It's slow here too.

Took me two minutes just to install beep (22k):
> sudo time apt-get install beep
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgd2-noxpm
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  beep
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.0kB of archives.
After unpacking 111kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe beep 1.2.2-19 [22.0kB]
Fetched 22.0kB in 1m49s (200B/s)
Preconfiguring packages ...
Selecting previously deselected package beep.
(Reading database ... 155315 files and directories currently installed.)
Unpacking beep (from .../beep_1.2.2-19_i386.deb) ...
Setting up beep (1.2.2-19) ...

2.02user 0.28system 1:53.82elapsed 2%CPU 

---

### Post by Tim Sharitt on 2008-04-25
Try a different download server in software sources.

---

### Post by Perpetual on 2008-04-25
> **Tim Sharitt said:**
> Try a different download server in software sources.

Yup.  I normally use the US Main Server but had to switch to the gatech server yesterday.

---

### Post by Oldsoldier2003 on 2008-04-25
> **Tim Sharitt said:**
> Try a different download server in software sources.

another option is to select other... from the list in software sources an then click the select best server button from the ensuing dialog box. Its really hard to tell which download server is best right now since its the day after a release and most of the servers are being hammered pretty hard.

---

### Post by Tim Sharitt on 2008-04-25
> **Oldsoldier2003 said:**
> another option is to select other... from the list in software sources an then click the select best server button from the ensuing dialog box. Its really hard to tell which download server is best right now since its the day after a release and most of the servers are being hammered pretty hard.

That seems to work best because a closer server isn't a sure thing if it's swamped.

---

### Post by jetsam on 2008-04-25
Much better.  Thanks!

New test after changing server and doing apt-get clean:
> 
sudo time apt-get install beep
...
Fetched 22.0kB in 1s (18.0kB/s)
...
Setting up beep (1.2.2-19) ...

2.02user 0.29system 0:04.82elapsed 47%CPU 

---

