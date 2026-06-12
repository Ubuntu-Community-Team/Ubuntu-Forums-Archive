---
title: "Skype on x64"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by sunrex on 2009-05-15
How do I install skype if I am using the x64 distro?. It says wrong architecture 'i386' and its making me want to pull my hair out since my understanding was x64 could emulate x32 applications.

---

### Post by Anthon on 2009-05-16
This is probalby the package installer complaining. I think you can override that (with --force or so) and you might get that to install.
I tried the x64 version of the package which I downloaded. That installed fine, but did not work out that well (under 8.10). I eventually  went back to the i386 distro of Ubuntu for my desktop machine, because I did not want to deal with these issues and on that machine speed is not so much of an issue. So I cannot tell you if things are better with 9.04

---

### Post by sunrex on 2009-05-16
Well I'm using the package managers for this - I don't know command line to well. So, what would I need to type in?.

Edit: It's still not working. sudo dpkg -i --force skype*

---

### Post by Anthon on 2009-05-18
> Edit: It's still not working. sudo dpkg -i --force skype*
I assume you mean the package does not install, not that the resulting installed binary does not run.
Unfortunately your use of the wildcard hides if you downloaded the 64 bit version of the package or not.
   mkdir tmp
   cd tmp
   wget [http://download.skype.com/linux/skype_ubuntu-2.0.0.72-1_amd64.deb](http://download.skype.com/linux/skype_ubuntu-2.0.0.72-1_amd64.deb)
   sudo dpkg -i skype_*amd64.deb
you probably have to run
   apt-get -f install
after that. As some dependencies to libqt4 are probably not installed.
I have no idea how to do this with just the mouse or even if you can.

---

### Post by Kimm on 2009-05-18
Best is probably to follow the instructions on how to add these  repositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and then install from there :)

---

### Post by mateuszbaranski on 2009-05-18
thank you for hint Kimm. It works great on my Core 2 Duo (64bits)!
Sunrex: change the topic to [SOLVED]

---

