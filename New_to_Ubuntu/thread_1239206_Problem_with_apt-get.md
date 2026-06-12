---
title: "Problem with apt-get"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by linuxnovice on 2009-08-13
Hi,

I recently upgraded my laptop from Ubuntu 8.04 to 9.04. I am trying to setup my desktop to the way it was before. The problem I am facing with apt-get is that it does not seem to resolve dependencies. I wanted to install blubuntu-look. But here is what I got:

```
E: Broken packages
sudarshan@lucky-top:~$ ins blubuntu-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  blubuntu-theme: Depends: gtk2-engines-ubuntulooks but it is not going to be installed
E: Broken packages

```

And this is not only for blubuntu. I wanted to install robot-player-dev (dev files for a robot interface software). I got similar results:

```
sudarshan@lucky-top:~$ ins robot-player-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  robot-player-dev: Depends: libplayerdrivers2-dev but it is not going to be installed
E: Broken packages

```

I am not new to Ubuntu. But I have not encountered this problem before.
Any help is appreciated.

Thanks.

---

### Post by Hospadar on 2009-08-13
I think usually this error comes about when there are conflicts.  Probably it has something to do with your upgrade, often times during an upgrade package names change or packages are added or removed and this sometimes causes unexpected conflicts if the package maintainer forgets to update his/her package or makes a mistake doing so.

For example a library that does the same thing as a different library might cause conflicts.

I would try installing the trouble dependency itself and see if that gives you more information.
apt-get install gtk2-engines-ubuntulooks

Alternatively you could try downloading the .deb from the package site manually and seeing what happens.  That might give you some helpful errors/solve the problem

for example: [http://packages.ubuntu.com/jaunty/gtk2-engines-ubuntulooks](http://packages.ubuntu.com/jaunty/gtk2-engines-ubuntulooks)

---

### Post by asmoore82 on 2009-08-13
I have a clean install of 9.04 and I had the same problem just yesterday...
blubuntu depends on that gtk-ubuntulooks package which in turn conflicts with ubuntu-desktop
manually installing the gtk-ubuntu package and allowing the removal
of ubuntu-desktop worked for me.

---

### Post by linuxnovice on 2009-08-13
> **asmoore82 said:**
> I have a clean install of 9.04 and I had the same problem just yesterday...
blubuntu depends on that gtk-ubuntulooks package which in turn conflicts with ubuntu-desktop
manually installing the gtk-ubuntu package and allowing the removal
of ubuntu-desktop worked for me.

Hi,

Thanks for that. That worked for me. I also did a clean install. 

However, the problem with robot-player-dev still remains. Since the problem seems to be similar, I tend to assume that robot-player-dev is in conflict with some other lib/package. However, I have no idea of finding out which though.

Thanks.

---

