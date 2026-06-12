---
title: "dpkg vs apt-get vs aptitude"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by lnvisible on 2010-08-02
IMHO aptitude is much better, since it is a top-level approach that automates a lot of things.

however, I cannot find how to use it to install several packages. Specifically, right now, I was trying to install skype in my debian squeeze, and all I got from its site is a .deb for debian lenny. Not to speak about a nice repository to add as in the case of google software...

Do I have any chance not to get (too) dirty if I would like to use skype in my debian. All help is welcome.

Thank you!!

---

### Post by snowpine on 2010-08-02
Hi Invisible, a friendly reminder to give your threads descriptive titles. I think your *actual* question is "how do I install Skype in Debian Squeeze?" right? :)

[http://wiki.debian.org/skype](http://wiki.debian.org/skype)

There is no Skype for Debian Squeeze since Squeeze hasn't been released yet ;) so try the Lenny version.

---

### Post by CharlesA on 2010-08-02
Just install the lenny version. Should be fine.

---

### Post by lnvisible on 2010-08-02
Yes, probably that would be a better title.

I think I cannot install skype in my debian at all. I tried with the lenny version (which is older, should work) but it is for the i386 architecture, and my debian is using the amd64.

Then I tried the bz2 files, but it looks like there is no way it will find libgthread-2.0.so.0. It's in /usr/lib and I added that path to the PATH variable and I even created a LIBPATH variable.

So I don't know what to do for that library to be found.

What next? I'm thinking of wine...

---

### Post by lnvisible on 2010-08-02
I used this:
[INDENT][FONT=Courier New]dpkg -i --force-architecture skype-install.deb[/FONT]
[/INDENT] Now it is installed, but I cannot run it, if I click on it from the start menu nothing will happen. If I type skype in a terminal I get this message:
[INDENT][FONT=Courier New]skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory[/FONT]
[/INDENT] [FONT=Verdana]More no found libraries...[/FONT]

---

### Post by snowpine on 2010-08-02
The link in post #2 describes how to install Skype on 64 bit Debian.

Debian forums are here by the way: [http://forums.debian.net/](http://forums.debian.net/)

---

### Post by lnvisible on 2010-08-02
> **snowpine said:**
> The link in post #2 describes how to install Skype on 64 bit Debian. I see, I'm using that, let's hope it works. Thank you.

> **snowpine said:**
>  Debian forums are here by the way: [http://forums.debian.net/](http://forums.debian.net/)Unfortunately google keeps taking me back here. But I get it, I won't be adding trash in your community any more.

---

### Post by snowpine on 2010-08-02
> **lnvisible said:**
> But I get it, I won't be adding trash in your community any more.

Don't worry; Debian talk is allowed here. :)

---

### Post by jtarin on 2010-08-02
> **lnvisible said:**
> 
Unfortunately google keeps taking me back here. But I get it, I won't be adding trash in your community any more.
I think what he meant to say was that your problem could be solved easier in a forum more familiar with Debian architecture. Maybe it would have been avoided if your help statement had included something along the lines of...."Debian forums have been no help so I thought I would come here and ask the experts.":p
Flies with honey.
When I'm looking for something unusual to install I usually search for a possible ppa repository.
Sometimes...not always when you get the message libraries cannot be found it is usually because of a different version number. I have sometimes been successful linking libraries to newer versions of the same library.
For example....you need  libQtDBus.so.4......but your install has  libQtDBus.so.5.
```
ln -s /path/to directory/libQtDBus.so.5 libQtDBus.so.4
``` (this will create a [soft-link]("http://thelinuxlink.net/lvlinux/resources/commands/ln.html") in the same directory.

---

