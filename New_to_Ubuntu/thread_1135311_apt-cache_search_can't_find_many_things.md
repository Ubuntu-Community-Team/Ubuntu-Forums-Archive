---
title: "apt-cache search can't find many things"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by perito on 2009-04-24
For example:
> ubuntu@ubuntu-laptop:~$ apt-cache search jdk
ubuntu@ubuntu-laptop:~$ apt-cache search vlc
ubuntu@ubuntu-laptop:~$ 


... I want to install java and vlc and several other things ... whats up?

---

### Post by Flyingjester on 2009-04-24
aptitude search

---

### Post by Malalo on 2009-04-24
what happens if you type

```
sudo apt-get upgrade
```

---

### Post by perito on 2009-04-24
> ubuntu@ubuntu-laptop:~$ aptitude search jdk
ubuntu@ubuntu-laptop:~$ 

> ubuntu@ubuntu-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$ 

I'm thinking its a resporatiry problem (like ticked off or something?)
How can I find out ... ?

---

### Post by Flyingjester on 2009-04-24
system > administration > software sources

---

### Post by Malalo on 2009-04-24
What I meant was 

```
sudo apt-get update
```

sorry about that.

---

### Post by perito on 2009-04-24
The server was set to a local one, I changed it to Main Server and it seems to work.
Thanks

---

### Post by Flyingjester on 2009-04-24
No problem :)

---

### Post by drs305 on 2009-04-24
> **perito said:**
> ... I want to install java and vlc and several other things ... whats up?

Do you have the *universe* and *multiverse* repositories enabled?
System, Administration, Update Manager or Synaptic. Settings, Repositories, Ubuntu Software. Make sure you have multiverse and universe ticked. For other popular software, you may need to add additional repositories, such as medibuntu.

If you think it may be a repository problem, here is the ubuntu wiki link:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

