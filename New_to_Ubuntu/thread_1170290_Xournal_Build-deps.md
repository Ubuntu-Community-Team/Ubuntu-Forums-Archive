---
title: "Xournal Build-deps"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by neo.patrix on 2009-05-26
Hello all,

I am interested in applying recent patches to "xournal" , but I am unable to install build-deps using apt-get. 

Has someone tried it? Is there a work around? 

```

patrix@patrix-laptop:~$ sudo apt-get build-dep xournal 
[sudo] password for patrix: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for xournal could not be satisfied.

```

Output from show command

```

patrix@patrix-laptop:~$ aptitude show xournal
Package: xournal
State: installed
Automatically installed: no
Version: 0.4.2.1-0.1ubuntu1
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 913k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7), libfontconfig1 (>= 2.4.0),
         libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.12.0), libgnomecanvas2-0
         (>= 2.11.1), libgnomeprint2.2-0 (>= 2.17.0), libgnomeprintui2.2-0 (>=
         2.17.0), libgtk2.0-0 (>= 2.14.1), libpango1.0-0 (>= 1.21.6), libx11-6,
         zlib1g (>= 1:1.2.0), gs, poppler-utils
Description: GTK+ Application for note taking
 Xournal is a GTK+ application for notetaking, sketching and keeping a journal
 using a stylus. It can also be used to add annotations to PDF files.
Homepage: http://xournal.sourceforge.net/


```

I use xournal to annotate PDF files, there are certain fixes and recent updates which I am interested in trying out.

---

### Post by neo.patrix on 2009-05-26
Bump !

It looks like I did find some part of the problem by excavation , there is a dependency libcairo2-dev. Now libcairo2-dev (1.8.0-0ubuntu1) depends on libcairo2 version (= 1.8.0-0ubuntu1). But my system has 
libcario2 version 1.8.0-0ubuntu1.1, naturally there is a conflict.

libcario2 turns out to be a root of problem because of following

> 
patrix@patrix-laptop:~$ apt-cache showsrc xournal
Package: xournal
Binary: xournal
Version: 0.4.2.1-0.1ubuntu1
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Mathieu Bouchard <mbouchar@bioinfo.ulaval.ca>
Build-Depends: debhelper (>= 5), autoconf, automake, libgtk2.0-dev (>= 2.4), libgnomecanvas2-dev, libgnomeprint2.2-dev, libgnomeprintui2.2-dev


Install dependency with apt-get

> 
sudo apt-get install libgtk2.0-dev libgnomecanvas2-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev
...
The following packages have unmet dependencies:
  libgnomecanvas2-dev: Depends: libgnomecanvas2-0 (= 2.20.1.1-1ubuntu2) but 2.20.1.1-1ubuntu3 is to be installed
  libgnomeprint2.2-dev: Depends: libpango1.0-dev but it is not going to be installed
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed


On further excavation...

> 
sudo apt-get install libpango1.0-dev

The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libcairo2-dev (>= 1.7.6) but it is not going to be installed
E: Broken packages


Also same trouble with libgnomecanvas2-0, newer version of library is installed but dev package depends on older version

Is there a work around to get proper development libs? Should I make a bug report? By the way I simply could not understand the fact how can developer versions be older than actual binary in-use on system, aren't they suppose to be newer, although it might still
result in conflict.

---

### Post by Mornedhel on 2009-05-26
This looks like the dependencies are a bit messed up. It happens sometimes.

Filing a bug report is probably a good idea, but

1. check for similar bug reports in case it has been reported already
2. make sure you have read [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Although you sound like you know what you're doing, so you probably know the above already.

Also, this app looks interesting. I didn't know there were PDF annotation tools in Jaunty. Last time I checked there weren't any (in Hardy) IIRC. I'll probably try it out. What exactly were the patches for ? Is the app unstable or is it additional functionality ? I would like to know in case I run into the same issues.

Edit: no, dev packages aren't supposed to be newer. Rather, they're expected to match the API of the non-dev package so you can compile against them. They usually contain header files and other things needed for compilation. The dev package should depend on any version of the non-dev package that matches the same API (not too old, not too recent).

---

### Post by neo.patrix on 2009-05-26
Xournal main has not been updated for nearly an year but still it is good application works with Intrepid. Some recent feature updates and bug fixes where made by community. 

You can find them [here]("http://sourceforge.net/tracker/?words=tracker_browse&sort=open_date&sortdir=desc&offset=0&group_id=163434&atid=827735")

It is really good utility for PDF annotation , I choose it after trying out Okular, PDFedit etc. These application are going Adobe Reader way becoming too intelligent for my taste, so I landed up using KPDF and Xournal.

---

### Post by neo.patrix on 2009-05-26
> **Mornedhel said:**
> 
Edit: no, dev packages aren't supposed to be newer. Rather, they're expected to match the API of the non-dev package so you can compile against them. They usually contain header files and other things needed for compilation. The dev package should depend on any version of the non-dev package that matches the same API (not too old, not too recent).

That makes sense, we do have a problem in that case worth making a report.

Edit : Makes sense, but according to precedent [BR#145786]("http://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/145786") related to feisty (about more than one year old BR) was closed being regarded as status:"Invalid". Although, I am sure I have installed Xournal from Ubuntu package repo. (also [UbuntuForum Thread 3436462]("http://ubuntuforums.org/showthread.php?p=3436462"))I also got the source using

> 
apt-get source xournal 
sudo apt-get build-deps xournal


Whatever is the dependency mess-up was suggested through standard process & not due to installation of directly downloaded non-standard package. More importantly both conflicting versions of libcario are also from Ubuntu. libcario2-dev is not being installed exactly because [COLOR="Red"]1.8.0-0ubuntu1.1(already installed) *is not equal to*  1.8.0-0ubuntu1 (unfortunately required)[/COLOR]

---

### Post by neo.patrix on 2009-05-28
Bump ! bug or no bug?

---

### Post by Mornedhel on 2009-05-28
The reply looks like it's from some boilerplate "another noob mistook Launchpad for the Beginner Forums" answer.

Notably "Your log mentions that you have installed a 1.4.10-1turner3~feisty0.1 libcairo version which is creating your issue, that's not an Ubuntu version so not a bug." The package the reporter tried to install is obviously from the Ubuntu repositories (his sources.list only includes Feisty repos). Although it's possible and recommended to build packages for anything you install from source so you don't break dependencies, the reporter mentions he's a newbie, so I doubt he'd done that.

I call bug.

---

### Post by neo.patrix on 2009-06-01
I think, I have overlooked one more point. Although I bugged it, probably it is incorrect because of 'apt-cache policy' output

> 
libcairo2:
  Installed: 1.8.0-0ubuntu1.1
  Candidate: 1.8.0-0ubuntu1.1
  Version table:
 *** 1.8.0-0ubuntu1.1 0
        100 /var/lib/dpkg/status
     1.8.0-0ubuntu1 0
        500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) intrepid/main Packages


So, Intrepid (main) has appropriate version "1.8.0-ubuntu1 0" but version on my notebook is higher "1.8.0-ubuntu1.1 0" now that could be from multiverse, universe or medibuntu (I simply don't know, but would be glad to pin-point). When I checked in Synaptic (usually I do not use it), I found that there was no shiny Ubuntu logo for libcairo, which I believe indicates it is not a package from Intrepid main. These probably does not warrant libcairo2-dev support for libcairo2 version "1.8.0-ubuntu1.1 0" package support, which makes sense to me. 

Unfortunately, libcairo has landed up being some ugly patchwork to support xyz package (which is also most probably not in intrepid main). Therefore, I will have to downgrade libcairo and get rid of the culprit. Question is how when majority of graphics package directly or indirectly depend on my libcairo2. I would not uninstall it outright and then try reinstalling, that is way too risky.

---

### Post by neo.patrix on 2009-06-01
Well that was not a bug after all, 

But still I got libcairo2 (1.8.0-0ubuntu1.1) without having intrepid-updates listed as package reposirtory but I needed it for libcairo2-dev, why so?

As far as topic of this thread is concerned, I am able to install required build-deps for Xournal. So, it is solved

---

### Post by kickwin on 2009-07-17
Sorry for deviating from the OP but I would like to know how I can uninstall Xournal. I found a better software  (okular) for my purpose (PDF annotation) and would like to remove xournal from the system. 

I installed it from terminal and I do not see xournal in my Synaptics.

Thanks!

---

