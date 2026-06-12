---
title: "Cant install apps"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by saint luke on 2009-12-28
Hey all, im in process of setting up a network, running ubuntu 9.1, all things are going well so far except i cant install an application. Im new to linux, but sudo apt-get always comes back with a not found error, and through software center, install (and for installed programs remove) is greyed out. Im the only user that is setup on this computer so i presumed im setup with full access, and from what i can see i have. Any suggestions on what to check or where ive gone wrong?

EDIT - I can remove installed apps..

---

### Post by jonest1 on 2009-12-28
Can you give a specific example of an apt-get command which is not working and I'll have a look on my system.

---

### Post by saint luke on 2009-12-28
It happens with any sudo apt-get command that ive tried, which leads me to believe its an error on my part somewhere.

EG - sudo apt-get install firestarter - this is what i get back.

[sudo] password for server: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firestarter

Also i cant figure out how to install an app through the ubuntu software center, so im guessing its got something to do with privileges.

---

### Post by avtolle on 2009-12-28
Which repositories are enabled? I do not recall which one holds firestarter, e.g., but I would check my repositories under software sources (System>Administration>Software Sources) and make sure that main, universe, restricted and multiverse are checked. If any of these is not, click on it and then reload the sources as the message that pops up will advise. Once that finishes, try the command again.

---

### Post by howefield on 2009-12-28
What happens when you do a 

```
sudo apt-get update
```

from a terminal ?

(Applications > Accessories > Terminal)

---

### Post by saadlulu on 2009-12-28
> **saint luke said:**
> It happens with any sudo apt-get command that ive tried, which leads me to believe its an error on my part somewhere.

EG - sudo apt-get install firestarter - this is what i get back.

[sudo] password for server: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firestarter

Also i cant figure out how to install an app through the ubuntu software center, so im guessing its got something to do with privileges.


works perfectly fine here 
```
 boza@boza-laptop:~$ sudo apt-get install firestarter 
[sudo] password for boza: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  menu
Suggested packages:
  dhcp3-server
The following NEW packages will be installed:
  firestarter menu
0 upgraded, 2 newly installed, 0 to remove and 20 not upgraded.
Need to get 855kB of archives.
After this operation, 4,002kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
boza@boza-laptop:~$ 

```

---

### Post by howefield on 2009-12-28
> **saadlulu said:**
> works perfectly fine here

Good for you. Cool story..

---

### Post by saadlulu on 2009-12-28
> **howefield said:**
> Good for you. Cool story..

woohoo :P

no really what i meant was it should work fine although i dont have anything added to repositories and everything is just default. 

did u try installing other stuff ??
what happens when you try this ?
```
 sudo apt-get install amarok 
```

---

### Post by saint luke on 2009-12-28
i tried sudo apt-get update and that worked fine

since then, apt-get & software center both work fine...

thanks for the help!

---

### Post by saadlulu on 2009-12-29
> **saint luke said:**
> i tried sudo apt-get update and that worked fine

since then, apt-get & software center both work fine...

thanks for the help!

+rep [howefield]("http://ubuntuforums.org/member.php?u=186490") :)

---

### Post by glubbdrubb on 2009-12-29
Please use the thread tool "Mark this thread as solved" if your problem has been fixed, thanks.

---

