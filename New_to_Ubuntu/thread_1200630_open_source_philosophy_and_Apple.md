---
title: "open source philosophy and Apple"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by marcopalla on 2009-06-30
Hi,
a very simple (stupid?) question, (no flame no trolling, I'm really new here :oops:)

On desktop side I was an old (10 years ago), Mac user, then passed to Win than to Ubuntu. 
Yesterday to have a flashback ;-) I installed Mac OSX on my laptop, and I see: yup! that's a unix x86 system (=linux), isn't it?

How is it possible that Apple has taken an opensource OS and has put it in a completly closed one?

would not be easier to run mac apps instead of win apps on linux? (I mean why wine Photoshop instead of....)

EDIT: 		   		 		 		Ok BSD unix license, here's the answer, (I always thought it was something like gnu license, but it is not)
thanx

the second part of the question:
> would not be easier to run mac apps instead of win apps on linux? (I mean why wine Photoshop instead of Mac Photoshop....)
> I never see Mac apps porting projectsto install  on Linux (gargeband, ILife etc.), why?
>If Iphone OS is open, why not porting Apple widgets on Linux, like androide ones?

linux community is always the coolest, my frinds :wink:


thanx for any answer,
m.

---

### Post by derekeverett on 2009-06-30
I'm a little out of my league answering this but my understanding is that not all versions of UNIX are open source...

Not to mention all the other software that comprises OS X would be proprietary...

---

### Post by derekeverett on 2009-06-30
To further clarify what I understand..

UNIX is not Liunx.

The proper term in fact is GNU/Linux to describe the linux kernel and all of it's associated software.

GNU stands for Gnu's Not Unix.

They are just meant to operate similar.

I hope somebody with a little more knowledge in this area comes along to answer further.

---

### Post by asmoore82 on 2009-06-30
Mac OS X is built on top of one of the BSD's - netBSD I think - so it's a Linux cousin.

My problem with apple is all of the bullcrap surrounding iTunes, iPods and
especially the iPhone/iPod touch. The iPhone is an Open Source OS at its core
but Open Source Developers are not welcome on it. And that App Store with its
schizo approval process and centralized payment systems - that is a
Bill Gates wet dream but Apple beat him to it.
No Thanks! - I demand Freedom on my Servers, Desktops, Laptops, AND Mobile Devices!

---

### Post by halitech on 2009-06-30
OS X is actually based on Darwin which is a BSD fork

[http://en.wikipedia.org/wiki/Darwin_(operating_system](http://en.wikipedia.org/wiki/Darwin_(operating_system))

Because of the way the BSD license is written, there is nothing stopping people from taking the code, making changes to it and making it proprietary and selling it.

[http://en.wikipedia.org/wiki/Free_open_source_software](http://en.wikipedia.org/wiki/Free_open_source_software)

[http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses)

---

### Post by marcopalla on 2009-06-30
Ok BSD unix license, here's the answer, (I always thought it was something like gnu license, but it is not)
thanx

the second part of the question:
> would not be easier to run mac apps instead of win apps on linux? (I mean why wine Photoshop instead of Mac Photoshop....)
> I never see Mac apps porting projectsto install  on Linux (gargeband, ILife etc.), why?
>If Iphone OS is open, why not porting Apple widgets on Linux, like androide ones?

linux community is always the coolest, my frinds ;-)

---

### Post by Sef on 2009-06-30
> OS X is actually based on Darwin which is a BSD fork

[http://en.wikipedia.org/wiki/Darwin_(operating_system]("http://en.wikipedia.org/wiki/Darwin_%28operating_system"))[Darwin]("http://en.wikipedia.org/wiki/Darwin_%28operating_system%29") is a fork of [FreeBSD]("http://freebsd.org"). [ FreeBSD]("http://freebsd.org"), and [NetBSD]("http://netbsd.org") are [BSD]("http://en.wikipedia.org/wiki/Berkeley_Software_Distribution") forks and [OpenBSD]("http://openbsd.org") is a fork of [NetBSD]("http://netbsd.org").

> Because of the way the BSD license is written, there is nothing stopping people from taking the code, making changes to it and making it proprietary and selling it.

[http://en.wikipedia.org/wiki/Free_open_source_software](http://en.wikipedia.org/wiki/Free_open_source_software)

[http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses)They are licensed under the [LGPL (Lesser General Public License.)]("http://www.opensource.org/licenses/lgpl-2.1.php")  The source code is open source, but you can use it and not release any changes to the source code, if the software is released to the public.  With the [GPL (General Public License)]("http://www.opensource.org/licenses/gpl-3.0.html"), If the software is released to the public, the source code must be released with any changes made.

---

### Post by Paqman on 2009-06-30
> **marcopalla said:**
> Hi,
How is it possible that Apple has taken an opensource OS and has put it in a completly closed one?


The BSD licence is ok with that. The GPL licence that most Linux software uses isn't.

> 
would not be easier to run mac apps instead of win apps on linux? (I mean why wine Photoshop instead of....)


The core of OS X is built on open source, but everything on top of it is pure proprietary Apple.

---

### Post by milton1 on 2009-06-30
When Apple first announced they were going to a *nix based system, they made a big deal about making at least part of their system open source. However, it is important to recall that open source does not mean free. To Apple, open source was a way to tell consumers and developers that programming for the new system would be easier and more resiliant as programmers would be able to see the open source OS code. There is certainly some validity to this idea. So OSX does have some legitimately open-source content, but it is also proprietary and tightly controlled by Apple.

---

### Post by el.otro on 2009-06-30
In fact Darwin IS open source, what is not OSS is all the graphics and apple programs/utilities; now: I'm not sure its Free Software, because it is not GPL-ed, it is given through Apple Public License (or something like that).

You could in fact download Darwin from Apple's site and (if you know how, which I don't) install gnome or KDE on top of it and run BSD applications on it, you'd just have a Basic Unix operating system.

There were some business moves they made, by creating a project called OpenDarwin, though which they took the OSS communities work and included it on OS X, but it didn't catch on because of so many advantages they were taking from developers in the community.   That's as much as I know about, really.

So yes, it is a UNIX system.  No it's not a completely closed one (not the kernel, and many GNU utilities it includes).  And using Mac applications has more to do with libraries and APIs than it has to do with the kernel (and that's some basic commentary, because I'm no programmer) as I understand it.

---

### Post by decoherence on 2009-06-30
> **marcopalla said:**
> Hi,

On desktop side I was an old (10 years ago), Mac user, then passed to Win than to Ubuntu. 
Yesterday to have a flashback ;-) I installed Mac OSX on my laptop, and I see: yup! that's a unix x86 system (=linux), isn't it?

as other have said, it's BSD. Darwin (the "core" of OS X) is based largely on FreeBSD.

BSD and Linux are both referred to as 'UNIX-like' operating systems.

> How is it possible that Apple has taken an opensource OS and has put it in a completly closed one?

This is allowed by the BSD license. The BSD license has given the world many wonderful things like TCP, OpenSSH, various C libraries, and much much more. Some people think that the permissiveness of the license is a bad thing, but can you imagine what would've happened if MS hadn't been able to take this well tested and standardized TCP stack for use in Windows? The internet might be a very different place...

> would not be easier to run mac apps instead of win apps on linux? (I mean why wine Photoshop instead of....)


No, and the reason is that OS X isn't really much of a UNIX system, after all. Most programs for OS X are written using either the Carbon or Cocoa frameworks. Carbon allows for old Mac programs to be easily ported to OS X (Photoshop is a prime example of this.) They're running on OS X, which is techincally a UNIX-like system, but the programs themselves bare more resemblance to OS 9 programs because, in fact, that's what they are.

Cocoa programs offer the best chance for running on Linux. Cocoa is Apple's new name for the OpenStep framework. OpenStep is implemented on Linux by the GNUStep project. Unfortunately, Apple has updated Cocoa such that programs written for it can't be easily ported to GNUStep.

Another limiting factor is that most OS X programs do not use an X11 display server, preferring Apple's own Quartz technology. We'll see a Quartz-compatible Linux display server some time after the cows come home, hell freezes over and monkeys fly out of my butt. Apple is not interested in sharing Quartz, in the least.

---

### Post by marcopalla on 2009-06-30
^^^ very clear thanx!

---

### Post by sydbat on 2009-06-30
<insert picture>monkeys flying out of cows butt in frozen hell</insert picture>

---

### Post by tgalati4 on 2009-06-30
Apple has released X Darwin which runs a standard X server on top of OS X.  It's reasonably fast and you can run a near-complete Gnome desktop.  Fink Commander is a system of open source ports for many packages to run using X Darwin.

BSD license allowed Apple to run with a stable kernel and put all the shiny, proprietary, stuff on top.

---

