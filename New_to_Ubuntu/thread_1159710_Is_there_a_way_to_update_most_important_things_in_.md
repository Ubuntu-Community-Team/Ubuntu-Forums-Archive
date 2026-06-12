---
title: "Is there a way to update most important things in 8.10?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by gymophett on 2009-05-14
I need 8.10 because of Xorg and my graphics card. I want to update Pidgin, Gnome, Firefox, etc to all the latest versions. What is the fastest and easiest way to do this? I heard something about launchpad.  So can you help? Thanks! :D

P.S. Is there a way to get the new notifications in 9.04 in 8.10?

---

### Post by kpkeerthi on 2009-05-14
You can download the debs from [www.getdeb.net](www.getdeb.net). You may find latest versions of your favorite packages here.

You may also enable the [backports repository]("https://wiki.ubuntu.com/UbuntuBackports") from System -> Admin -> Software Sources. This repository is community maintained and if you are lucky (there is no guarantee that all applications will be backported) you'll find some updates for your applications here too.

The other option is to use [PPA]("https://launchpad.net/ubuntu/+ppas"). You can search for a PPA [here]("https://edge.launchpad.net/ubuntu/+ppas"). If you find a PPA for your favorite application, you can add it as a repository and update your packages using apt or update manager. Google to find out more.

---

### Post by mprince on 2009-05-15
-

---

### Post by ainsworth_t on 2009-05-15
Try adding the repositories for jaunty (9.04) along side the repositories for intrepid (8.10) within /etc/apt/sources.lst. Then, for the files you want to update, try

```
sudo apt-get install <file> -t jaunty
```

---

