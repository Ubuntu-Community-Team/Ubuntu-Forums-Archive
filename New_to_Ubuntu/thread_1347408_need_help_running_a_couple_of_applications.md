---
title: "need help running a couple of applications"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by AlphaWhelp on 2009-12-06
So I downloaded 3 emulators for Linux, ZSNES, VBA-M., and Gens/GS.  Currently, Gens/GS is the only one that works, the other two simply don't run.  I click on them and nothing happens, not even an error message.  Can someone tell me what I did right with Gens so I could do it again with ZSNES and VBA-M?

---

### Post by NoaHall on 2009-12-06
Try running them from the terminal and post the output
It's probably something like ```
vba-m
```

---

### Post by AlphaWhelp on 2009-12-06
got zsnes to work, here is the output when trying to execute vba-m from the terminal

```
gvbam: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory
```

---

### Post by AlphaWhelp on 2009-12-06
So I just googled for the missing library and found out that I need to install an rpm file somehow which required a program called alien which I found and downloaded.  I am trying to install this rpm but it just doesn't seem to be working and giving me lots of errors.  The command I'm trying to use is:

```
sudo alien -d -i [libglademm24-2.6.7-3.fc12.src.rpm]("ftp://ftp.icm.edu.pl/vol/rzm1/linux-fedora-secondary/development/source/SRPMS/libglademm24-2.6.7-3.fc12.src.rpm")
```

Is this even right?  Here is the output when I type that.

```

error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/libglademm24
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'i386' does not appear in package's architecture list (sparc64)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: `libglademm24-2.6.7': No such file or directory


```

---

### Post by LuisGMarine on 2009-12-06
Hello, lets modify the commands you are using to run and install this .rpm.

Try these steps:

```
sudo alien -k libglademm24-2.6.7-3.fc12.src.rpm
```
-This will convert the .rpm to a .deb.
-The "-k" will keep the version number. Otherwise alien adds a "1" to the version number

Once you do that, install the package with

```
sudo dpkg -i libglademm24-2.6.7-3.fc12.src.deb
```

Let us know if this works! :popcorn:

---

### Post by MooPi on 2009-12-06
Now that is an awesome post on how to convert .rpm to .deb .  I'm savin' this one. Thanks LuisGMarine

---

### Post by LuisGMarine on 2009-12-06
> **MooPi said:**
> Now that is an awesome post on how to convert .rpm to .deb .  I'm savin' this one. Thanks LuisGMarine

Glad it helped, lol I was surprised it was that easy =).  Anyhow Alpha still waiting on you to see if it works, if so make sure you mark this as [SOLVED] :popcorn:

---

### Post by AlphaWhelp on 2009-12-06
It didn't work, I got the exact same error output as I posted before.  I figured maybe I downloaded the wrong library and so I downloaded the library for x86 instead of i386 and that actually just crashed even harder.

[http://www.rpmfind.net/linux/rpm2html/search.php?query=libglademm-2.4.so.1](http://www.rpmfind.net/linux/rpm2html/search.php?query=libglademm-2.4.so.1)

That is the website that I'm trying to get my library from, unfortunately there are so many of them I'm not even sure which one is the right one.  I don't want any development libraries or anything, I'm just looking for the one that will run on UNR

---

### Post by LuisGMarine on 2009-12-06
First past the output of:
```
uname -a
```

Second if you are using the 64-bit version of Ubuntu, I would recommend using a force architecture flag, just like I posted below:
```
sudo dpkg -i --force-architecture libglademm24-2.6.7-3.fc12.src.deb
```

Try all the steps above again, with the command I just gave you to install it and let me know if it works.

---

### Post by AlphaWhelp on 2009-12-06
Here are the results from uname -a

```
2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686 GNU/Linux
```

I don't think I'm running 64 bit but the force command is not likely to help since I can't even get as far as getting a deb file.  I'm kind of getting a little frustrated because I've spent so much time trying to make this damn thing work that I feel like I have to make it work now :)

---

### Post by aktiwers on 2009-12-06
That lib is in the repos.

[Click here]("apt:libglademm-2.4-dbg") to install it.

Or search for it in synaptic to install..  or type:
```
sudo apt-get install libglademm-2.4-dbg
```
in terminal

---

### Post by AlphaWhelp on 2009-12-06
> **aktiwers said:**
> That lib is in the repos.

[Click here]("apt:libglademm-2.4-dbg") to install it.

Or search for it in synaptic to install..  or type:
```
sudo apt-get install libglademm-2.4-dbg
```in terminal

boy do I feel defeated and yet relieved at the same time.

as an aside, how do I change the tag to [Solved]

---

### Post by aktiwers on 2009-12-06
> **AlphaWhelp said:**
> boy do I feel defeated and yet relieved at the same time.

as an aside, how do I change the tag to [Solved]

:D

In the top right corner find it in the "thread tools"

---

### Post by AlphaWhelp on 2009-12-06
ty everyone who helped

---

