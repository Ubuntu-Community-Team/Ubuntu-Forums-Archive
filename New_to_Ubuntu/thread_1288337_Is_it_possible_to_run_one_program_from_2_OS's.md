---
title: "Is it possible to run one program from 2 OS's?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Fabled One on 2009-10-11
I am dual-booting Vista and Ubuntu and I am wondering if it is possible to run a program, say Eclipse, from either OS if the program is only installed in one location. 

I have a big shared partition and was hoping that I could install Eclipse there and just run it from Ubuntu or Vista since Eclipse runs on the java runtime environment (or am I completely wrong here?).

Also, is it only possible to use programs on Ubuntu if they are installed via tools such as apt-get or synaptic package manager?

---

### Post by SuperSonic4 on 2009-10-11
> **Fabled One said:**
> I am dual-booting Vista and Ubuntu and I am wondering if it is possible to run a program, say Eclipse, from either OS if the program is only installed in one location.

It's possible but would be easier to install it in both places.

> I have a big shared partition and was hoping that I could install Eclipse there and just run it from Ubuntu or Vista since Eclipse runs on the java runtime environment (or am I completely wrong here?).

In theory yes, as long as JRE was on the system you wanted to run it on. In ubuntu I'd create a symlink to /usr/bin to make it easier to launch although no idea how well it'll work.

> Also, is it only possible to use programs on Ubuntu if they are installed via tools such as apt-get or synaptic package manager?

No, it's just preferred. You can install from an ubuntu .deb file or you can compile from source

---

### Post by The Cog on 2009-10-11
> **Fabled One said:**
> I am dual-booting Vista and Ubuntu and I am wondering if it is possible to run a program, say Eclipse, from either OS if the program is only installed in one location. 

I have a big shared partition and was hoping that I could install Eclipse there and just run it from Ubuntu or Vista since Eclipse runs on the java runtime environment (or am I completely wrong here?).

I think in theory it should be possible, but if Eclipse stores paths, resolving differences between D:\blah and /home/blah might be more effort than it's worth. You may find copying your source files between two separate installs is easier in the long run. I don't use Eclipse so I don't really know what I'm talking about though.
> 
Also, is it only possible to use programs on Ubuntu if they are installed via tools such as apt-get or synaptic package manager?
You can install and use programs installed by other means, such as downloaded .deb installers, downloaded binaries, downloaded source code that you compile yourself. But the preferred way is to use the Ubuntu repositories if the program you want is there. Stuff you download from the internet may be geared more towards other Linux distros, which can cause compatibility issues. You stand more chance of it working if it's been packaged for Ubuntu, and less chance of installing malware if you avoid downloading from the wilds of the internet in general.
That said, I run some stuff that I downloaded from other sites, and generally don't have too much trouble with it.

---

### Post by Fabled One on 2009-10-11
Awesome, thanks for the help guys!

---

### Post by ikisham on 2009-10-11
Sometimes the software in the official repository is somewhat outdated and you may want/need to install a newer version. For that you can either:
1) download the .deb for Ubuntu of the newest version on the software site if it's available.
2) [search for a PPA]("https://launchpad.net/ubuntu/+ppas") (Personal Package Archive) that has a newer version of the software.
3) look if there's a newer version in Ubuntu's [backports]("https://help.ubuntu.com/community/UbuntuBackports") repository or ask for someone to include it there.

---

### Post by Fabled One on 2009-10-11
Great, good to know :) thanks

---

