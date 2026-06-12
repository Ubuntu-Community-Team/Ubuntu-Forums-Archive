---
title: "WordPerfect in Linux (from year 1999)"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-03-28
I'm helping someone get into Ubuntu. For 25+ years he has used the wordprocessor: WordPerfect (windos)

I have the RedHat GUILG00.TAR.GZ (note Upper Case) file. (~23 meg). I'm stuck. When can I run Alien on this? Before or after untaring? Before or after the ./Runme?

Odd, no mention of guilg00 anywhere at these forums.

---

### Post by jrusso2 on 2010-03-28
I have tried to get that running on Ubuntu before.  It doesn't have some files it needs to run.  Never got past the install.

---

### Post by Mark_in_Hollywood on 2010-03-28
Where you working with the mispackaged: guilg00.gz or the Red Hat (properly packaged) GUILG00.TAR.GZ  ?

And have your read / tried:


[http://www.linuxtoday.com/news_story.php3?ltsn=1998-12-21-012-10-NW-SW&tbovrmode=1](http://www.linuxtoday.com/news_story.php3?ltsn=1998-12-21-012-10-NW-SW&tbovrmode=1)

---

### Post by jrusso2 on 2010-03-28
You can just rename it I did.

---

### Post by Mark_in_Hollywood on 2010-03-28
I'm not understanding your response. I have the Red Hat version of "guilg00". By "guilg00" I mean the Red Hat version. Why would I rename it?

Also, did you have a look at the (very short) article about installing WP in Linux from the URL? Thanks.

---

### Post by jrusso2 on 2010-03-28
some said tar.gz but they were really .tar files. If yours is in Redhat form should be .rpm which I never saw like that.

---

### Post by Mark_in_Hollywood on 2010-03-28
There were two versions. I have (eventually) found both on the net. I tried the re-naming approach to the guilg00.gz. It would not open/extract. After more searching, I found the Red Hat version: GUILG00.TAR.GZ. That extracts and I know have 11 tarred files in /wordperfect. 

Can you tell me whether I can Alien these files, or do I have to extract and then Alien them?

I'm going to be gone from the 'puter for 30 minutes or maybe a little longer starting at 12:33 pacific Daylight time. Back ASAP. thanks.

---

### Post by Sef on 2010-03-28
Have you looked at this [thread]("http://ubuntuforums.org/archive/index.php/t-998675.html")?

---

### Post by srs5694 on 2010-03-28
Unfortunately, running WordPerfect for Linux in any modern Linux distribution is a difficult task. There have been quite a few changes in Linux between WP8's release (in 1998 or thereabouts) and the present. The most challenging of these is the libraries issue. In 1998, Linux was still using the old libc5 libraries, but these were abandoned shortly thereafter in favor of glibc. Modern systems invariably use glibc, and given its age, they seldom even provide backwards compatibility support for libc5. The two libraries are related but incompatible. This means that you must hunt down and install libc5 to get WordPerfect working. If the target system uses a 64-bit version of Linux, you'll also need a whole set of 32-bit compatibility libraries. Finding precisely what you need can be tricky. Some of the links others have provided might help with this, but I can't say I've looked at any of those links all that closely, nor have I tried installing WP8 for Linux on any very recent version of Ubuntu. My last such attempt was on an Ubuntu 8.04 system. The result was a program that ran and was mostly usable for short periods. It tended to crash very often, though, and some dialog boxes (including the file load/save dialog box) had quirks that made them painful to use.

As to using alien to convert the tarball to a Debian package, forget it. The tarball includes an installation script, which you must use to install the software. Although it's theoretically possible to create a Debian package to easily install the WP8 software, this is a task for somebody with at least moderate skill with both WP8's quirks and creating Debian packages, not a simple tool like alien.

Although I like WordPerfect a lot, and I even wrote a book on WP8 for Linux (*Special Edition Using Corel WordPerfect 8 for Linux,* published by QUE in 1999), IMHO its time is long past. For most people, it will be less painful to learn to use a modern word processor that's well supported by today's Linux systems, such as OpenOffice.org's Writer or AbiWord, than to try to get WP8 working. If you absolutely need WP8 for file compatibility reasons, you can certainly try jumping through all the hoops required to get it working (installing libc5 libraries, installing 32-bit compatibility libraries, creating a fake /etc/printcap to help it find your printers, etc.). If you still can't get it to work, you might consider running a ~10-year-old Linux distribution in a virtualization environment (QEMU, VMware, etc.) just so you can more easily install and run WP8 in it. In fact, Corel once released its own Linux distribution. IIRC, it included its own version of WP8 in package form. You could try hunting that down (I'm sure there's a site somewhere that's still got copies of it.)

---

### Post by Mark_in_Hollywood on 2010-03-28
I think that I shall go no further. Thank you, one & all ./Linux Community!

---

