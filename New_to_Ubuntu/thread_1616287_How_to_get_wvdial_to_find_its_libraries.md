---
title: "How to get wvdial to find its libraries"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by Ralph L on 2010-11-08
I installed from tarballs wvstreams 4.6.1 and wvdial 1.61 into karmic.  I believe these should be compatible as they are the latest versions I could find of each.  I know I could have done the installation from Synaptic, but for various reasons I wanted to do the tarball install.  For each of tarballs, I "cd" to the folder extracted from the tarball, and under Terminal, entered the command sequence:
./configure
make
sudo make install

I installed wvstreams first and then wvdial.  Everything seemed to go ok except for some warning messages.  No fatal errors.  However, when I try to run "sudo wvconf" (or ust "wvconf") I get the message "wvdialconf: error while loading shared libraries: libuniconf.so.4.6: cannot open shared object file: No such file or directory".

I found wvconf in /usr/local/bin/.  I found libuniconf.so.4.6 in /usr/local/lib/.  If I put a symbolic link in /usr/lib/ that points to /usr/local/lib/libuniconf.so.4.6, that library will be found, but then wvconf cannot find the next library, etc.  So it seems that wvconf is searching in the wrong directory--/usr/lib/ rather /usr/local/lib/.  Being very much a newbie I don't know how Ubuntu programs link to libraries, nor why wvdial is linked to the wrong library.  I suppose I did something wrong in the install, but I don't know what.

Any help appreciated.

Thanks
Ralph

---

### Post by lkraemer on 2010-11-08
Typically you need to install build-essential and the headers for the
kernel you are running.

```

uname -r

```
will tell you the kernel you are running
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install what is needed to compile code.

You then download the source and extract
```

cd /path/to/source
tar xvf packagename.tar.gz
cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

```
make clean won't remove anything on the first compile, but will clean up
on successive compiles.

But, this won't get the dependencies.......
You need wvdial dependencies also:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


OR..............

You need to download wvdial and the following dependencies for 10.04,
or whatever version you have installed......

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP or Ubuntu, then copy the *.deb files to USB Flash Drive, & then to Ubuntu subdirectory /var/cache/apt/archives & then install using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.

lk

---

### Post by Ralph L on 2010-11-09
lkraemer,

Thank you very much for a very informative writeup.  You taught me things I had no inkling existed--namely [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .  You are correct that using this site to download .deb files would have been a much easier way of accomplishing what I wanted to accomplish--downloading the wvdial package on a Windows machine and then transferring it to karmic.

However, I was hoping that you could explain a little more on where programs like wvdial search to get their libraries.  I got wvdial 1.61 and wvstreams 4.6.1 to work under karmic by placing, in /usr/lib/, symbolic links to all the wvstreams libraries that were placed in /usr/local/lib/.  Now I would like to understand the search process, and hierarchy that is used, when a program like wvdials want to satisfy its library needs.

Under an old operating system I used (not Linux or Unix related), a number of libraries were searched in order according to a set of rules.  First, a program like wvdial could specify internally what libraries were to be used.  However, this could be overridden by a parameter in the program invocation command so that the user could specify a different library.  This override lasted only for the execution of the single program--say wvdial.  Second, something like an Environment variable could specify libraries that would be used for all programs run in the future for the entire session.  It had a "force" parameter that allowed the session Environment library to be forced to be used, or to allow it just to be used to satisfy externals that hadn't been satisfied earlier.  Finally there was a system wide default library that was used to satisfy any remaining unsatisfied externals that weren't satisfied earlier.  

Does Ubuntu have any library structure like this for satisfying library needs, and if so, what are the variables and files involved, and what would be the "normal" way that wvdial would satisfy its library needs?  Did wvdial just neglect to add /usr/local/lib/ to a file that specified libraries to be searched?

If you have the time I would really appreciate an explanation of, and/or a reference to some place that explains all this.  I am particularly interested in what is the "normal" way that a source tarball like wvdial would specify its library search.

Thanks
Ralph

---

### Post by lkraemer on 2010-11-09
Ralph,
I have the time, but I don't have the knowledge.  I only compile what
is absolutely necessary to do what I need to make something work.  I would
rather download via Synaptics or a deb and install that way.

What you are looking for is a developer, or someone that writes code,
and that isn't me.  I only know what I have posted be reading, testing,
trying, and asking questions, as you have done.

So, Sorry I can't be of more help.

lk

---

### Post by QLee on 2010-11-09
[QUOTE=Ralph L]lkraemer,
Thank you very much for a very informative writeup.  You taught me things I had no inkling existed--namely [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .  You are correct that using this site to download .deb files would have been a much easier way of accomplishing what I wanted to accomplish--downloading the wvdial package on a Windows machine and then transferring it to karmic.[/QUOTE]
Wow, you've been a member since 2007 and haven't yet encountered any of the package managers, that surprises me.

[QUOTE=Ralph L]However, I was hoping that you could explain a little more on where programs like wvdial search to get their libraries.  I got wvdial 1.61 and wvstreams 4.6.1 to work under karmic by placing, in /usr/lib/, symbolic links to all the wvstreams libraries that were placed in /usr/local/lib/.  Now I would like to understand the search process, and hierarchy that is used, when a program like wvdials want to satisfy its library needs.[/QUOTE]
It's coded in the deb package to put it in the "correct" location in the filesystem, another reason to use the repositories for your Ubuntu version when installing software, that doesn't require user action the way compiling from source does. Using one of the package managers is the best way for an inexperienced user to install.

[QUOTE=Ralph L]Does Ubuntu have any library structure like this for satisfying library needs, and if so, what are the variables and files involved, and what would be the "normal" way that wvdial would satisfy its library needs?  [/QUOTE]
Normal way would be to use the package manager and those needs would be satisfied.

This might show you some differences from that other OS.
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)

[QUOTE=Ralph L]Did wvdial just neglect to add /usr/local/lib/ to a file that specified libraries to be searched?[/QUOTE]
No, the person compiling and installing has to be responsible for configuration.
 
[QUOTE=Ralph L]...or a reference to some place that explains all this.  I am particularly interested in what is the "normal" way that a source tarball like wvdial would specify its library search....[/QUOTE]
Have a look at this:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

