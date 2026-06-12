---
title: "Distros compatible with Ubuntu/Debian repositories"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by jhsu802701 on 2010-01-01
I'm looking for lightweight distros that make use of the Ubuntu/Debian repositories.  And I don't mean Xubuntu - it's almost as heavy as Ubuntu with GNOME.  Are the Ubuntu derivatives (CrunchBang, Debris, gOS, Jolicloud, U-Lite, etc.) compatible with the Ubuntu repositories?

I'm a user of Puppy Linux and Ubuntu, and I have tried Debian.  I like the user-friendliness and lightweight performance of Puppy Linux and STRONGLY recommend it as a first distro.  But it falls short in the area of the repository.

As an engineer, I need something with a better repository than Puppy Linux.  (Version 4.3.1 has a feature called Woof that's supposed to address this weakness, but Woof took a long time to install, and I wasn't able to get things working.)  Both Debian and Ubuntu have Scilab and various software for programming microcontrollers.

I found Debian difficult to configure, and that's why I'm not a Debian user.

Ubuntu is easier to work with than Debian but is heavier and less suitable for old computers with only 256 MB of RAM.  Over time, Ubuntu terminates support for older versions while making the latest version more power-hungry.  Thus, a segment of the Ubuntu user population gets cut off each year.

---

### Post by Max_Mackie on 2010-01-01
What are you going to run this on?
Im using an eeepc with 1GB ram and a crappy little processor and its running UNR very well.

---

### Post by michaelzap on 2010-01-01
One nice lightweight Debian distro is DreamLinux. It will run on a P3 with only 128 megs of RAM. It's also an XFCE distro, but way lighter than Xubuntu.

You might also try out the LXDE Debian Live CD, which is available from lxde.org.

I've used and like Crunchbang as well, but you do need to configure some things manually and be comfortable with OpenBox and keyboard shortcuts (if you are, that might be a very good choice).

---

### Post by cenzorrll on 2010-01-01
i would suggest downloading the mini.iso from ubuntu.  you'll need an internet connection, but you get to install what you need.  most of what slows your computer down is the graphical environment.  xfce is actually pretty lightweight, but xubuntu doesn't really take good advantage of it.  the lightest environment that i find to still be very user friendly is lxde, there is very little configuring necessary to get it working, unlike pretty much anything else out there i've tried using.

for a lightweight install from the mini.iso i would install the base system (this includes ubuntu-standard i believe by default)  then from the command line do:

```
sudo apt-get install lxde xdm xinit
```

and that should get you on your way. all you'll need to do is decide what programs you'll need. (xdm is a lightweight login manager)

i would also research all you can about different desktop environments so you can make the best decision on what you need. (my lxde box only uses 112mb of memory, although i installed from a debian cd).

i think i'll try this on a virtual machine to see what happens:)

Edit: well, finished the virtual machine setup, and gkrellm shows 34mb of ram being used with the very basic setup

---

### Post by bodhi.zazen on 2010-01-01
That is one of the major advantages of Ubuntu or Debian, the sheer size of the repositories.

You just hit on th major weakness of many many light weight distros. Puppy, DSL, to semoe extent even Slackware / Zenwalk.

The bad news is, no you can not mix and match repositories that way, and just because it is a .deb does not mean it will install cleanly on a Debian or Ubuntu system.

If you want to go with a light weight ubuntu flavor I suggest you perform a minimal install and add only those apps you need / want.

Other options would be Crunchbang, Lubuntu, etc.

Or you could try one of the many respins, Zenix is one.

---

