---
title: "ALSA update problems"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by leeelson on 2009-09-30
I have a new HP mini 110 running Ubuntu 8.04. I want to update the ALSA drivers from 1.0.16 to 1.0.21.
I tried using the update script ([http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)) but it failed because
it couldn't find alsa-oss. (I tried installing with 'apt-get install alsa-oss' but that failed too with 
the message 'Package alsa-oss is not available...').

I followed the ALSA instructions ([http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)) and that 
completed with no errors. However, I still seem to be running 1.0.16:

 cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on May  3 2009 for kernel 2.6.24-22-lpia (SMP).

Can anyone suggest how to get 1.0.21 working?

---

### Post by mikeyphi on 2009-09-30
Alsa-OSS is not a default install. Open Synaptic - you should be able to find and install version 1.0.15-1
Following that, the mentioned upgrade script should find something to upgrade.

Don't know why apt-get didn't work - unless you tried the wrong site?

---

### Post by leeelson on 2009-09-30
> **mikeyphi said:**
> Alsa-OSS is not a default install. Open Synaptic - you should be able to find and install version 1.0.15-1
Following that, the mentioned upgrade script should find something to upgrade.

Don't know why apt-get didn't work - unless you tried the wrong site?
Synaptic doesn't show alsa-oss. Here's my sources.list:
cat  /etc/apt/sources.list
deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted 
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted 

deb [http://hpmini.archive.canonical.com/mi/](http://hpmini.archive.canonical.com/mi/) hardy-hpmini public 
deb-src [http://hpmini.archive.canonical.com/mi/](http://hpmini.archive.canonical.com/mi/) hardy-hpmini public 

What is the correct source for alsa-oss?

---

### Post by mikeyphi on 2009-10-01
I note that your source list is all from hpmini.

I guess that most of us use the standard source, for example, in my case
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe

Is your OS specialised? That would explain why alsa-oss in not available.

You might want to ask HP if you can use vanilla Ubuntu sources.

---

### Post by leeelson on 2009-10-01
> **mikeyphi said:**
> I note that your source list is all from hpmini.

I guess that most of us use the standard source, for example, in my case
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe

Is your OS specialised? That would explain why alsa-oss in not available.

You might want to ask HP if you can use vanilla Ubuntu sources.
I don't know if there is something special abo0ut the HP mini OS. HP is not very helpful there (a long story of frustration).

When I add the repository you recommend, Synaptic gives the following error message:
people.ubuntu.com/~ubuntu-archive/ddebs/.../**binary-lpia**/Packages - [Similar]("http://www.google.com/search?hl=en&client=firefox&rls=com.ubuntu:en-US:unofficial&q=related:people.ubuntu.com/%7Eubuntu-archive/ddebs/dists/intrepid-updates/main/binary-lpia/Packages") - **[Package: libdirectfb-dev-dbgsym Priority: extra Section: libdevel [B]...**]("http://people.ubuntu.com/%7Eubuntu-archive/ddebs/dists/jaunty/main/binary-lpia/Packages")[/B]


Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I'm new at this. Any idea what is going on?

BTW, thanks for your input.

UPDATE

It looks like I need binary-lpia packages and the ones in my sources.list do not contain alsa-oss. There *is* an old alsa-oss package in the "pool" directory but it is a source file. Since I don't know how to list this in my sources.list file, I tried to do a manual install (configure, make, make install) but I'm a bit over my head here. What I really need is a binary package but can't seem to find one.

---

