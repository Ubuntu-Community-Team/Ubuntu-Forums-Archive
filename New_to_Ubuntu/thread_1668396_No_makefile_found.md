---
title: "No makefile found"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by jvacek996 on 2011-01-16
Hi everyone.
I'm having difficulties installing from tarballs.
Nobody really never told me how to do it nor I found a tutorial which might be the problem, but i seriously have no idea and every README just gives a few terminal commands which for some reason don't work.
I extract the folders into my home folder, then open them up and right-click to get an "Open Terminal here" option (might this be the problem?)
Normally you would run a "configure" file by doubleclicking it and "running in terminal", and that works. BUT, when i cd into the location and type "make" into the terminal, it vomits this.
> jvacek996@Ubuntu-6730s:~/clutter-1.5.12/build$ make
make: *** No targets specified and no makefile found.  Stop.

And that's where I'm stuck. When I look into the folder however, there are always files called Makefile with .am and .in appendixes.
I am running a 10.10 64-bit, i used to run 32-bit but don't remember whether I used to have the same or not.
Thanks for helping me!

---

### Post by cariboo on 2011-01-16
I would suggest opening a terminal first before running any of the commands.

---

### Post by mc4man on 2011-01-16
> i seriously have no idea and every README just gives a few terminal commands which for some reason don't work.
While some sources have no decent readme's or install file(s), when they do there is usually some worthwhile info (which I believe is the case here so read thru a little closer.

Not sure what source you're using, what you posted suggests a tarball. In that case you probably should be 1 directory up, ie. not in the build directory.
It's likely that in there will a configure script that you'll need to run and PASS before a Makefile is created
(Makefile.am and Makefile.in are used by the Makefile

If there is no configure script then look for an autogen.sh

In cases where there is a configure and no worthwhile text file then sometimes useful to run, at the extracted source prompt, 
./configure --help

As mentioned before you'd be better off cd'ing to your extracted source directory and running from there., ie.
vacek996@Ubuntu-6730s:~/clutter-1.5.12$

It's also possible that this is a source you'd be better off not building, though borking things up isn't the worst way to learn stuff.

---

### Post by oldos2er on 2011-01-16
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

