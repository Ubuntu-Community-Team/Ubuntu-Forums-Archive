---
title: "libgtk-1.2.so.0 missing"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by aam-aadmi on 2009-12-18
Hi All,

I am using Ubuntu 9.10 on my HP dv2500 laptop; I have just now installed Stata 9. But the Stata GUI does not work because the libgtk-1.2.so.0 is missing.

When I type xstata at the command prompt I get

[HTML]xstata: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory[/HTML]

I saw that libgtk-1.2.so.0 is not available in the Synaptic Package Manager (because it is a very old and outdated library, I guess). How do I get it and install it?

Thanks in advance.

Aam-aadmi

---

### Post by fooman on 2009-12-18
search in synaptic for the "libgtk2.0-dev" package and install it....or just open a terminal and type or copy/paste the following:

```
sudo apt-get install libgtk2.0-dev
```hope that helps.

---

### Post by aam-aadmi on 2009-12-18
I did install that but the problem still persists. Any further suggestions?

Aam-aadmi

---

### Post by anewguy on 2009-12-18
I'm a little out of my element here, but I think it might be possible to set up a symbolic link linking libgtk-1.2.so.0 to the libgtk-2.0 "stuff".  Someone else would need to help you on the syntax for that.

dave :)

---

### Post by Kebrethian on 2009-12-18
I am having the same problem.  I ran the aforementioned code and I had already tried all the suggestions on this thread: [http://www.uluga.ubuntuforums.org/showthread.php?t=599032](http://www.uluga.ubuntuforums.org/showthread.php?t=599032)

What I end up with is this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk2.0-dev

Same thing happens minus the -dev

I am running the 32-bit Karmic

---

### Post by mc4man on 2009-12-18
see here
[http://ubuntuforums.org/showthread.php?t=1341472&highlight=libgtk1.2](http://ubuntuforums.org/showthread.php?t=1341472&highlight=libgtk1.2)

---

### Post by Flos Headford on 2010-09-24
Thanks to the thread above, I've been able to install and run GSview (a great front-end for Ghostscript).
Bless you!
Phil

---

### Post by ankurchaudhary8931 on 2013-02-10
I am getting following error on adding the line to Synaptic package manage and running the update command for apt

 apt-get update

Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 1,724 kB in 53s (32.0 kB/s)                                            
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.202 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I am using ubuntu 12.04

---

### Post by wildmanne39 on 2013-02-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

