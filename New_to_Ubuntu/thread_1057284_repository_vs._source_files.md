---
title: "repository vs. source files"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Montblanc_Kupo on 2009-02-01
So I've heard how compiling source files is great because it's built just for your machine... although... I've never successfully gotten something to install this way... just... doesn't work... so I avoid it.

Leads Me to the question though... is there an advantage to installing via compiling source files vs. downloading from the repositories. I'm still a little unclear exactly how customize a compile is... if it's just for your particular distro... then it seems like the repositories would be exactly the same.

Also, if anyone has some links to information about how to successfully compile source files (mostly use Ubuntu 8.10 right now) that would be great. I've gotten a few things that said they were specifically usable on ubuntu and I never could get them installed. I googled around some... but none of the instructions I found really helped.

T.I.A.

---

### Post by binbash on 2009-02-01
let me give you an example : 

package a maintained by ubuntu OR repos etc is compiled with enabling debug support.However you may want to remove debug support to make things faster or lighter etc.This is just an example.


If you are interested compiling the WHOLE system, you should check out gentoo instead of ubuntu.

---

### Post by Montblanc_Kupo on 2009-02-01
gentoo was on My list of things to do... but I think I need to become more familiar with linux before I go to the dark side... ;)

Like I said... I haven't even gotten an app to successfully compile and install itself yet... let alone tweak the compile. If you have any information about actually DOING this... that would be great. :)

---

### Post by Paqman on 2009-02-01
> **Montblanc_Kupo said:**
> So I've heard how compiling source files is great because it's built just for your machine... 

Well, yes, but it's actually not a great idea to compile on a distro like Ubuntu.

Bascially, Ubuntu's package manager does a really good job of handling dependencies between packages. If you install something outside of the package manager (ie: compiled from source) then you risk breaking that dependency system. This can make your system unstable. It's not likely to create any system-wide carnage, but you could have individual packages stop working.

It's always better to install from the repos if you can. Next best thing is a proper .deb file. Compiling from source is an absolute last resort.

---

### Post by jerome1232 on 2009-02-01
Start with something easy, this is a neat little applet that shows cpu usage. Now for beginers to compile anything you need the build-essential package

```
sudo apt-get install build-essential
```

[http://hules.free.fr/wmforkplop/](http://hules.free.fr/wmforkplop/)

If you look at the site it gives you the requirements, there's also a README file that tells you about the packages you need included in the archive. Always look at the README and INSTALL files included with source code.

> 
Requirements:

    * gcc
    * imlib2 devel package.
    * libgtop2 devel package. 

So to get this program installed you need these pacakages. So search the repos for the required packages. In ubuntu devel packages have a -dev at the end.  gcc you have from the build-essentials package so don't worry about that one.

```
 apt-cache search imlib2
adesklets - interactive Imlib2 console for the X Window System
came - Rewrite of the xawtv webcam app using imlib2
eterm - Enlightened Terminal Emulator
feh - imlib2 based image viewer
giblib-dev - headers for giblib
giblib1 - wrapper library for imlib2, and other stuff
giblib1-dbg - debugging symbols for giblib1
libimage-imlib2-perl - perl interface to the imlib2 imaging library
libimlib2-ruby - Ruby Extension for the Imlib2 C library
php-imlib - PHP Imlib2 Extension
python-kaa-imlib2 - Imlib2 Wrapper for Python
scrot - command line screen capture utility
libimlib2 - powerful image loading and rendering library
[COLOR="Red"]libimlib2-dev - Imlib2 development files[/COLOR]

```

```
 apt-cache search libgtop2
libgtop2-7 - gtop system monitoring library
libgtop2-common - common files for the gtop system monitoring library
[COLOR="Red"]libgtop2-dev - gtop system monitoring library[/COLOR]

```

Ok so you need to install those two development packages then you should be able to compile this particular program.

```
sudo apt-get install libimlib2-dev libgtop2-dev
tar xzf wmforkplop-0.9.3.tar.gz
cd wmforkplop-0.9.3
./configure
make
sudo make install
```

---

### Post by SunnyRabbiera on 2009-02-01
Yeh keeping to the repos is a good idea unless its mission critical to use a compiled app

---

### Post by HotShotDJ on 2009-02-01
> **Montblanc_Kupo said:**
> gentoo was on My list of things to do.I used Gentoo for several years. I learned quite a bit by using that distro.  However, with all the tweaking and customizations to squeeze the last bit of efficiency out of every program, the difference between Gentoo and Ubuntu (speed wise) was pretty much imperceptible (if it existed at all!).

ALSO, "compile from source" distributions take A LOT of work to maintain.  To make matters worse, if you do a major-version upgrade to your gcc, you need to recompile the tool-chain TWICE, and then recompile the entire OS and installed software.  The time for this is measured in days, not minutes. Furthermore, if you want to just "try out" some software, you have to wait for it to compile (large apps can take 8 or more hours to compile and install).  This was my primary reason for switching from Gentoo to Ubuntu.  I just didn't have the time to devote to my operating system and software.  I needed to use it to get a job done... in other words, my computer is a tool that I use to get something done, not a hobby in and of itself.

On the upside, you DO learn a lot from compiling software... just from the debugging process ("&$%#, now what..."  look up, fix, ./make && make install, "&$%#, now what..."  look up, fix... repeat until successful).  LOL... I'm exaggerating. But you get the point.

Just decide what you want to get out of compiling from source rather than using the binaries.  If you are looking for increased speed and efficiency, you'll likely be disappointed.  But if it is a learning experience that you're after, you'll get that in buckets!

---

### Post by Montblanc_Kupo on 2009-02-01
jermome1232 -- thanks for the detailed instructions. I've done pretty much exactly what you listed there and usually something mysterious goes awry during the process and it just doesn't work. So many variables to worry about though, it's hard to say what is really going wrong. Thanks again.

HotShotDJ -- Yeah... that's one of the things that has kept Me away from gentoo so far... I tend to install and remove a LOT of software pretty constantly... so having to wait until tomorrow to try it seems like a pain in the *** for a few miliseconds of speed.

---

