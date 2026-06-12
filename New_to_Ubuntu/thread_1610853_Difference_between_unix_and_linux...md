---
title: "Difference between unix and linux.."
date: 2010-11-01
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-01
I was confused between unix and linux..What is unix and what is linux..?Is ubuntu linux or unix..?

---

### Post by sky_ceiling on 2010-11-01
Ubuntu is based on Linux
 
Linux is a Free/Open-Source clone of UNIX (UNIX was originally neither). In original philosophy it is similar to what the ReactOS project does with Windows. Only more successful :P

---

### Post by TeoBigusGeekus on 2010-11-01
[http://www.ibm.com/developerworks/aix/library/au-unix-difflinux.html]("http://www.ibm.com/developerworks/aix/library/au-unix-difflinux.html")

---

### Post by Megaptera on 2010-11-01
Useful guide here:

[http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/](http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/)

---

### Post by ronnielsen1 on 2010-11-01
[http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/](http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/)

> To quote from Official Linux kernel README file: [INDENT]Linux is a Unix clone written from scratch by Linus  Torvalds with   assistance from a loosely-knit team of hackers across  the Net. It aims towards POSIX compliance.
[/INDENT]
Don't think I like that description

[http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/](http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/)

[QUOTE][Unix and linux both are multiuser operating system. Unix operating based  on CUI(Character User Interface) and does not support pointing device,  where as in linux opearating system; adding  new features XWindows in   Unix operating system and it is based on GUI(Graphical User Interface)  i.e., it is like as DOS and Windows/QUOTE]

---

### Post by ronnielsen1 on 2010-11-01
You clicked faster than I did Megaptera

---

### Post by Megaptera on 2010-11-01
Probably only 'cos I use one of these!

[http://www.turnpoint.net/wireless/cantennahowto.html](http://www.turnpoint.net/wireless/cantennahowto.html)

---

### Post by JKyleOKC on 2010-11-01
In the last half of the 1960s, researchers at MIT were working on Project MAC. MAC was translated variously as "Machine Aided Cognition" and "Man And Computer" but the idea was to find ways of making the computer available to everyone. The research was supported by a joint effort of the General Electric Company and Bell Telephone Labs. At that time, computers were huge things that required special environments and cost millions of dollars each; no average person could afford one of their own. The project concentrated on ways to provide that access, through remote connection using Teletype machines (the video terminal was just being invented in 1965).

While Project MAC produced a number of innovations that we today take for granted, it became a money pit for its corporate sponsors. Around 1970, BTL pulled out of it and left the commercial rights for G-E, which at that point sold its Computer Division to Honeywell. Commercial development continued under the name MULTICS.

Two BTL employees missed the capabilities that Project MAC had provided for them. They found an unused minicomputer and implemented a miniature version of MULTICS on it. Since it was a single-user system, Brian Kernighan suggested a play on the MULTICS name and called it UNICS. The system had much more capability than the standard computer systems of the day, and the skunk-works project got official blessing. The spelling of the name changed slightly, to UNIX, and multi-user capability was added.

BTL made the system available to universities at low cost but jealously guarded the commercial rights to it. Meanwhile, Honeywell attempted to market MULTICS but it went nowhere in a hurry and eventually was abandoned. I'm one of a very few people who actually wrote programs on the MULTICS system, to help me write the service manuals for early video terminals.

The capabilities of Unix became widely known, but access to it was rather limited. That's when Linus, as a university student, decided to try to create a clone of its kernel and published his work to the world via UseNet, the predecessor of the Internet. We know the rest of the story well.

Originally, Linux was a very limited kernel and lacked most of the features we now take for granted. Other people developed a graphic interface, which we know as the X server, that permitted point-and-click operation. Dozens of groups developed "distributions" which bundled the common kernel with the X server and other programs, making it more attractive to casual users -- but retaining the freedom to customize everything.

Other efforts to create Unix clones existed: Minix may have been the first, and has been acknowledged by Linux as an inspiration for his effort; the GNU project had another that hasn't yet gained wide acceptance, and there could well be more I havn't heard about since the whole idea of free software is its freedom to modify things...

This is probably more than you wanted to know about the differences, but the earlier post that compared it to DOS and Windows was pretty close. Unix still exists as a commercial package but its users are far outnumbered by the many flavors of Linux in use worldwide.

---

### Post by Old_Man_Unix on 2010-11-01
Officially, Linux is  GNU/Linux, but we will stick to the common name and just call it Linux. 

From the user point of view, UNIX and Linux are pretty much the same.  If you are used to programming in one of the UNIX shells, you will have no trouble translating your experience to the Linux shell, and vice versa.

Under the hood, there are some differences in the respective system level operations - most notably in the areas of disk I/O and  virtual memory- but only a few people will ever see them.  One that you might encounter if you work at the shell level is that there are differences in the way devices are described and this gets reflected in the device names. Of course, if you need to work at the system level,  you will need to be aware of all of these differences.   

GUIs are ... well.. GUIs.  If someone takes the trouble to port an open-source GUI such as GNOME to one of the various flavors  of UNIX, it will look pretty much the same as it does on Linux.  In fact, it's been done and that is precisely the end result.  It is not likely, however,  that anyone will port one of the UNIX GUIs to Linux.

And that last sentence highlights the major difference.  There is only one Linux (kernel) and it is open source.  It is licensed in  such a way that it *must* *always ** be open source*.  In other words, no one can take the existing Linux kernel and write a closed-source version of it - even if they want to use it on special purpose hardware.

UNIX started off as "free/gratis" when it was developed at Bell Labs,  but it was never licensed to keep it "free/libre".  Very soon after UNIX was out,  commercial (closed) versions of it started to appear.  Even the version from Bell was eventually turned into a commercial product. In the 80's and 90's these began to proliferate and take over to the extent that today almost all flavors of UNIX are proprietary.  And as GUIs started to appear,  these were proprietary as well.  In general, these flavors of UNIX were and are  targeted to specific proprietary hardware and were not meant to be ported to different platforms.  The IBM paper referenced above was written by one of those proprietary vendors and obviously reflects that viewpoint. 

There is a high-level specification for UNIX known as POSIX, but most of the commercial flavors of UNIX   extend that specification considerably. 

There are "free/libre"  UNIX  OSs around, the most prominent one being FreeBSD.  They must fork at the last "free" version of UNIX so that over time they have become different in the details as much as Linux has.  

To get into the details of UNIX vs. Linux will be difficult because of all the flavors of UNIX that are around today and their proprietary nature.   However, there have been numerous articles comparing FreeBSD to Linux and a simple web search will find these.

---

### Post by Soul-Sing on 2010-11-01
Linux and the basic core or design decisions of the kernel was/were based on MINIX, a BSD like op. system which was devel. and used by Andrew Tannenbaum. Torvalds did use MINIX as a core platform.
Later on Torvalds decided not to use the microkernel which Tannenbaum used for his system, but a monolithic kernel.
The monolithic kernel was the start of Linux.

---

### Post by HermanAB on 2010-11-01
UNIX is a trade mark held by The Open Group.

So, we can say that UNIX is a kind of Linux, but we are not allowed to say that Linux is a kind of UNIX.

---

### Post by Mark Phelps on 2010-11-01
We sometimes hear whining today about all the different "flavors" of Linux, especially when folks get nostalgic and think of UNIX as a single "flavor", but back in the mid-80's, I worked at a company that was experimenting with building a product for different flavors of Unix and we had a version for each of the following:
[LIST]
[*]BSD
[*]SunOS
[*]AIX
[*]SCO Xenix
[*]System V
[*]HP/UX
[/LIST]

Not quite as bad as the hundreds of flavors of Linux, but still, certainly not ONE.

---

### Post by balloooza on 2010-11-01
@getyourkarthick my friend, you just asked the best of all the questions.

It is like the question the kid in the back corner of physics asks, while all his friends wonder about what they need to know for the test, if gravity was inversly proportional to the square of the distances between the objects centers or centers of gravity, the kid asks: Why do we study physics, couldn't humanity just get by without learning all this stuff.

When I saw this question I just was so excited I felt like my insides would explode at the sight of such a humble and beautiful question

For all intensive purposes, unix and linux are the same, this brings up so much to talk about, what is linux accualy, how did it start was it based on unix, how linux itself is not an operating system, rather Linux, GNU Tools, many configuration files, independently developed software, a compiler to build it all make up what you use (the different combinations of the things I mentioned differentiate Ubuntu, from, say, Red Hat, and somtimes simple branding changes make the difference eg. Red Hat and CentOS)

---

