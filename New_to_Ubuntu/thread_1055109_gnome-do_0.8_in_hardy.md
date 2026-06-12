---
title: "gnome-do 0.8 in hardy?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Knacker on 2009-01-30
hi, 
i fear this is a really bad question, but how do i get packages for new gnome-do 0.8 in hardy? i've added the launchpad ppa repositories for gnome-do, but the version available is 0.6.1.0-0. 

am i missing something or is it simply not available? 

thanks.

---

### Post by Patricrawley on 2009-01-30
The latest release of Do is here [http://do.davebsd.com/](http://do.davebsd.com/)

---

### Post by gjoellee on 2009-01-30
it is in PPA:

for i386 download: [https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0~intrepid~ppa1_i386.deb]("https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0%7Eintrepid%7Eppa1_i386.deb")

for [lpia]("https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0%7Eintrepid%7Eppa1_lpia.deb"): [https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0~intrepid~ppa1_lpia.deb]("https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0%7Eintrepid%7Eppa1_lpia.deb")

---

### Post by Knacker on 2009-01-30
> **gjoellee said:**
> it is in PPA:

for i386 download: [https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0~intrepid~ppa1_i386.deb]("https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0%7Eintrepid%7Eppa1_i386.deb")

for [lpia]("https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0%7Eintrepid%7Eppa1_lpia.deb"): [https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0~intrepid~ppa1_lpia.deb]("https://edge.launchpad.net/%7Edo-core/+archive/ppa/+files/gnome-do_0.8.0-0%7Eintrepid%7Eppa1_lpia.deb")

yeah: but aren't these intrepid packages? i don't think i can add the intrepid repositories, can I?

EDIT: no, i can't. "dependencies not satisfiable...etc." or...?

---

### Post by picpak on 2009-01-31
Here are the steps to get gnome-do on Hardy:

1) Edit /etc/apt/sources.list:

```
gksudo gedit /etc/apt/sources.list
```

2) Add the following lines:

```
# custom mono
deb http://ppa.launchpad.net/directhex/ppa/ubuntu hardy main
```

Save and exit.

3) Update your repository cache:

```
sudo apt-get update
```

4) Install all the updates, and then download and install gnome-do and gnome-do-plugins:

[gnome-do_0.8.0-1ubuntu1~hardy1_i386.deb](http://www.mediafire.com/?nyn2wzznlmn)
[gnome-do-plugins_0.8.0-1ubuntu1~hardy1_i386.deb](http://www.mediafire.com/?vxdmglw4znm)

And then it should work. Good luck!

---

### Post by directhex on 2009-01-31
Did someone say my name?

---

### Post by inigomontoya on 2009-01-31
> **Knacker said:**
> hi, 
i fear this is a really bad question, but how do i get packages for new gnome-do 0.8 in hardy? i've added the launchpad ppa repositories for gnome-do, but the version available is 0.6.1.0-0. 

am i missing something or is it simply not available? 

thanks.

According to a fellow in the gnome-do IRC channel, there are no plans to package 0.8 for hardy.  The reason being is it's dependency on Mono 1.91 which is not available in the hardy repositories.  Mono can be installed in hardy from this repository, [http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html). You can then compile gnome-do 0.8.  I have done this successfully.  I havn't yet gotten the plugins to install correctly.

---

