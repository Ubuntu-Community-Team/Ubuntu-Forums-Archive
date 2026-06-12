---
title: "Program installation directory? &quot;Program Files&quot; equivilant?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by wombatvvv on 2010-06-02
Hi,

1 - Where should I select to install programs to when I have a choice?

2 - Where do programs get automatically installed to using the Package Manager or whatever?

I had to install NetBeans just now, and took a guess and put it in /usr/bin/netbeans/ (?)

---

### Post by nhasian on 2010-06-02
yep your right programs accessable by all users will be put in /usr/bin while anything you install in your own home directory will only be accessible by you.

---

### Post by 3rdalbum on 2010-06-02
> **wombatvvv said:**
> Hi,

1 - Where should I select to install programs to when I have a choice?

2 - Where do programs get automatically installed to using the Package Manager or whatever?

I had to install NetBeans just now, and took a guess and put it in /usr/bin/netbeans/ (?)

1. On the extremely-rare occasion that you get a choice, just install to the default. If there's no default, then /usr/bin should be alright.

2. Programs specify themselves where they install their bits to. Each part of the package needs to go into a different place so it can be found. You don't really need to know anything about this, but if you do, you can find where each part of the package has installed to by going to Synaptic, right-clicking on the package, going to Properties and then the Installed Files tab.

---

### Post by wombatvvv on 2010-06-02
Thankyou both.

Is there any easy way to see where different files from one program are installed if it wasn't installed through the Package Manager? Through some kind of script for example?

---

### Post by BoneKracker on 2010-06-02
> **wombatvvv said:**
> Thankyou both.

Is there any easy way to see where different files from one program are installed if it wasn't installed through the Package Manager? Through some kind of script for example?

Linux/Unix is different than Windows.  Read this:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

If it wasn't installed by the package manager, then no.  If the application didn't happen to come with a good uninstaller (and they almost never do), then you'll eventually end up with cruft all over your system (like your average Windows box).

That's one of the many reasons you should really stick to installing packages through the Ubuntu package management system, except when truly necessary (at least until you've been using linux long enough that you can _effectively_ use it's tools to clean up).  I've been using Linux for five years and I almost never install something from outside the repositories maintained by the distribution I have chosen (e.g. Ubuntu, Fedora, Suse, etc.).  Linux isn't Windows, where you just download crap willie-nillie off the Internet and install it on your computer and hope for the best.  Each distro's developers and packagers/maintainers and security testers make adjustments and configurations to the software so it will work well with your distro, they track the dependencies of the package so they'll automatically be installed (and removed when you uninstall), and they test it for functionality and security.  They fix bugs.  When you download stuff off the Internet, unless you review the code, build it from source and test it, you really have no guarantee of its quality, interoperability with your system, or security.  That's what a distro does for you.  That's why you use the repositories.

That said, it's your system and you're completely free to do whatever you want with it. This is just friendly advice.  :)

---

### Post by nhasian on 2010-06-02
you can use the command

```
whereis
```

for example

```
whereis firefox
```

for more info see

```
man whereis
```

> **wombatvvv said:**
> Thankyou both.

Is there any easy way to see where different files from one program are installed if it wasn't installed through the Package Manager? Through some kind of script for example?

---

### Post by leg on 2010-06-02
I thought that software you installed yourself was meant to be installed either in your home directory or /opt not in /usr/bin which is where the package system puts things.

---

### Post by BoneKracker on 2010-06-02
> **leg said:**
> I thought that software you installed yourself was meant to be installed either in your home directory or /opt not in /usr/bin which is where the package system puts things.

I tend to agree.  However, the LHS itself doesn't differentiate between files installed with or without a package management system.

Some linux distributions issue guidance to their users about where to install 3rd party (or "user-provided") software, generally with the intent of keeping it separate from those items under control of the package management system (although this may not technically be necessary or even actually beneficial).  And some distros are very different than others (Fedora, for example, making heavy use of /usr/local).

The best advice about this is:

1. Read and understand the LHS (which I linked to above)
2. Read and understand any guidance regarding this from your distro
3. Observe and understand the behavior of your distro's package management tools
4. Based on these things, decide for yourself where to install 3rd-party packages

Your home directory is a good place to install 3rd-party software that does not require elevated privileges if you are the only user who will run it.

---

### Post by towheedm on 2010-06-02
For an explanation on the Unix Filesystem Hierarchy Standard (FHS) check out:
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

This would tell you what should go where.

---

### Post by wombatvvv on 2010-06-02
Thanks guys, some great advice here.

---

