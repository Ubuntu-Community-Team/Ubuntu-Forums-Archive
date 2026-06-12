---
title: "Off-internet install"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by dekamps on 2010-04-17
Hi,
I'm new to Ubuntu. I downloaded the CD and installed 9.10 successfully on an off-internet machine. I'm left somewhat confused about how to install further packages, even after reading the documentation, which seems to be understandably biased towards connected machines.

My questions are the following:
-I have access to internet via a windows machine. I'd like to get some packages, which are not on the standard installation CD. How do I proceed?  Apparently there is a package APTonCD, which comes with a *.bat file for windows usage, but I could not get it to work. Is this the best way of doing things?

-Is it possible to simply download an individual package you need? Where do I get that package? How do I then install it from my USB?

Thanks,
Marc

---

### Post by k3lt01 on 2010-04-17
Check out [this link to keryx]("http://keryxproject.org/"). It has all the information you need.

---

### Post by unixisfreedom on 2010-04-19
I'm in exactly the same situation.  There's a directory of 'packages' you can install off ubuntu.org or something (you have to pick your version first... like there's a 'karmic' subdirectory and I go there cause I have 9.1)...  and they show you what the package you are downloading 'depends' upon.  But you don't even need to know that from there necessarily.  The way it works is that you need to download a .DEB file for what you want and get this over onto the machine you want to install on.  You then double click on this in Gnome (that Windows-like GUIy thing) and the DEB either installs or tells you there's a dependency.  If you have a dependency, you download that DEB and install that DEB first...  It sounds "daunting" at first, but it gets better as there are popular DEBs that tend to be 'dependencies'... Atleast that's been my experience...

---

### Post by k3lt01 on 2010-04-19
> **unixisfreedom said:**
>  Atleast that's been my experience...and that is a very long and complicated way to go about the process.

In your case you could use aptoncd if the application you are downloading is also on the machine you are downloading it onto to swap it over.

---

### Post by anewguy on 2010-04-19
I could be remembering incorrectly, but I thought you could also go through the synaptic package manager, check those you want, and then you could have it create the download script for you.  That way you should be assured you'll be getting all of the dependencies with out fighting for them (been there - it gets frustrating when you download 1 dependency only to find you need another, only to find you need another, etc.).

What I can't remember right now (I'd check it but I'm on Windows right now) if it creates a script you can run in Windows, but at least in looking at that script you should be able to identify all the packages you need to download so all the dependencies are met as well.

EDIT:  forgot to mention - you can do these downloads on another computer, copy the files to a USB flash drive, CD or whatever, then bring them to your Ubuntu computer and install them.

Dave ;)

---

### Post by mac9416 on 2010-04-19
> Atleast that's been my experience...

unixisfreedom, that's the way I used to have to do it, and it is very daunting. Especially if you need a package that has a lot of dependencies such as VLC.

> I could be remembering incorrectly, but I thought you could also go through the synaptic package manager, check those you want, and then you could have it create the download script for you.

anewguy, yes, it's 'File > Generate package download script' in Synaptic . But since dekamps's machine is completely offline, Synaptic won't know about the latest packages. dekamp could use a tool like [UbuntuOfflineUpdater]("http://sourceforge.net/projects/ubuoffupdater/"), but is an all command-line tool and not the easiest thing to use.

> What I can't remember right now (I'd check it but I'm on Windows right now) if it creates a script you can run in Windows, but at least in looking at that script you should be able to identify all the packages you need to download so all the dependencies are met as well.

The script doesn't work with Windows right away, but this page describes a few ways to make it work: [https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

Overall, dekamps, I think k3lt01 is right. [Keryx]("http://keryxproject.org") will do what you need.  :)

---

### Post by scottiw2000 on 2010-04-19
There is also the nice site [www.getdeb.net](www.getdeb.net) that allows you to download pre-built .deb files for many applications. Since you're downloading the .deb file you can use it from any OS. Then just copy the .deb file to your Ubuntu machine and click on it to install.

Another useful resource is launchpad ([https://launchpad.net](https://launchpad.net)). In addition to using launchpad repositories (or PPA repositories) for automatic updating, most of the repositories there also let you download pre-packaged .deb files manually. 

I know, the whole "package" concept threw me at first too, but I've come to love how user-friendly it is once you make the shift.

---

### Post by mac9416 on 2010-04-19
Hey, scottiw2000, I don't believe that will solve the problem of getting dependencies though, will it?

---

### Post by viralmeme on 2010-04-19
> **k3lt01 said:**
> Check out [this link to keryx]("http://keryxproject.org/"). It has all the information you need.
I tried kervy and it does download the DEPs except it don't check for dependencies.

---

### Post by mac9416 on 2010-04-19
ymitchell, it does check for dependencies.

---

### Post by viralmeme on 2010-04-20
> **mac9416 said:**
> ymitchell, it does check for dependencies.
I'll give it another go ...

---

