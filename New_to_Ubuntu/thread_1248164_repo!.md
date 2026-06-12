---
title: "repo!"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Kyugetsuki on 2009-08-23
I tried apt on cd to create a repository cd for my crunchbang...,but I did'nt like it. I do'nt like synaptic very much...(I end up installing the wrong packages).

here is what I would like to know:

how to create a cd repository

-accessible by add/remove
-and synaptic

---

### Post by alexlafreniere on 2009-08-23
The easiest solution I can think of would be to download whatever programs you need in the form of .deb's and write those to a CD. That way you can just copy them over and install whenever you need them. It's even easier than making it readable by Synaptic.

---

### Post by sandyd on 2009-08-23
use aptoncd
then put the cd into your computer and type this into the terminal
```

sudo apt-cdrom add

```
done :)
you **should** be able to see everything in add-remove and synaptic now.

---

### Post by mthalis on 2009-08-23
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

---

### Post by kansasnoob on 2009-08-23
I've had excellent luck with aptoncd - which is Apt On CD. It's in synaptic:

[ATTACH]126026[/ATTACH]

Or run the command:

```
sudo apt-get install aptoncd
```

Edit: upon reading again that was a stupid answer! Sorry.

---

### Post by k3lt01 on 2009-08-24
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=352460"). The first post is quite large, it is a "HowTo" afterall, but it does contain an answer to your question.

---

