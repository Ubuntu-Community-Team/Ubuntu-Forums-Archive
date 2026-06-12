---
title: "Linux and OSX?"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by allenbradley on 2009-07-16
Apologies if I sound like an idiot. OSX is based on UNIX while ubuntu is based on Linux, a unix/minix clone right? So shouldn't programs written for a mac work seamlessly on linux? What really differentiates the OSX from ubuntu?

---

### Post by toupeiro on 2009-07-16
> **allenbradley said:**
> Apologies if I sound like an idiot. OSX is based on UNIX while ubuntu is based on Linux, a unix/minix clone right? So shouldn't programs written for a mac work seamlessly on linux? What really differentiates the OSX from ubuntu?

Installing OSX on anything but MAC hardware is illegal.  You can put ubuntu on just about anything with a CPU.

Linux is not a clone.  What you see as ubuntu today started as the merging of two separate but symbiont projects.  Linux: a kernel, and GNU: an operating system. Hence, GNU/Linux, which almost every major distribution is based off of today.  In order to do this legally, all the UNIX programs were completely recoded, not simply ported.  Its all pretty technical, but simply put, there are great differences between UNIX, Linux, and OSX, even if they appear very similar in some aspects.

---

### Post by allenbradley on 2009-07-16
@toupeiro Thanks for the clarification. Let me just probe a little deeper. I'm looking at apps like, say, evernote that are written for a mac. How easy/difficult would it be to port it into Linux? Would it be easier than, say, porting a Windows app into linux, due to the basic difference in the filesystem and such?

---

### Post by OutOfReach on 2009-07-16
> **allenbradley said:**
> @toupeiro Thanks for the clarification. Let me just probe a little deeper. I'm looking at apps like, say, evernote that are written for a mac. How easy/difficult would it be to port it into Linux? Would it be easier than, say, porting a Windows app into linux, due to the basic difference in the filesystem and such?
Well if it is a GUI app, and if it is written for Cocoa GUI toolkit then it would be a bit harder to port to another operating system (since the Cocoa toolkit is only for Mac)

---

### Post by toupeiro on 2009-07-16
> **allenbradley said:**
> @toupeiro Thanks for the clarification. Let me just probe a little deeper. I'm looking at apps like, say, evernote that are written for a mac. How easy/difficult would it be to port it into Linux? Would it be easier than, say, porting a Windows app into linux, due to the basic difference in the filesystem and such?

The difficulty likely not be in the porting of the application.  Speaking technically only, it would probably just need to be run on a compiler in linux sans any proprietary languages MAC may be using.  Evernote, however, may have a license which forbids doing such an action.  In fact, it may have a license forbidding you to even have the source code to attempt something like this.  Most linux applications are Open source, meaning if you have the source code, and a compiler on <insert OS name here> there is a very good chance you can port it, and a 100% chance you aren't breaking any laws doing so.

The filesystem wouldn't be the biggest challenge, the the programming language might.  For example, a .NET program may not port well (or at all) from windows to linux, but a C, python, or java program would because there are compilers on both OSes and they are far less proprietary.

---

### Post by scorp123 on 2009-07-16
> **allenbradley said:**
>  So shouldn't programs written for a mac work seamlessly on linux? Not at all. While there are superficial similarities the differences are deep down in the core of the OS. What might work --and others have explained that already-- is to port an application between the two if you have the source code. This is exactly the reason why you will find the same set of (open-) source programs and tools for all the Unix variations out there. It doesn't matter if you use HP-UX, AIX, Sun Solaris, Mac OS X, GNU/Linux, FreeBSD ... chances are that all these operating systems ship with more or less the same basic tools such as "ping", "bash" and "vi", just to name a few. And why is that? Because these tools are freely available as source code, and there is a C compiler on all these platforms ... So it's no problem to take the same source code and have it compiled.

But as soon as programs make use of proprietary libraries and extensions or specific functions that only exist in a specific OS, then porting programs becomes highly complex if not impossible altogether.

Take Compiz as an example: It exists for Linux, FreeBSD and Sun Solaris and OpenSolaris ... but not for Windows or MacOS X. So downloading the newest and the latest Compiz effect from their source code repository and compiling it so you get a useable binary is no problem on Linux, FreeBSD, Sun Solaris and OpenSolaris. All the framework is there, you just need the compiler and its tools to produce a working binary. Or you wait until someone does this for you and puts the ready-to-use and ready-to-run binaries in a package repository from where you can download it via your package manager.

But Windows? Mac OS X? Compiz and all its framework (libraries and what not) don't exist there. While both Windows Vista and Mac OS X do have some GUI effects of their own that stuff is not identical or compatible with Compiz. So even if you obtain the source code for the latest and greatest Compiz effect and even if you find a suitable compiler ... it will not be possible to get that effect (or anything else from Compiz) working on those platforms.


> **allenbradley said:**
> What really differentiates the OSX from ubuntu? What differentiates diesel from gasoline? Both are fossile fuels, right? Both are used in combustion engines, right?

So they are exchangeable, right?  (No they are not ... don't try this at home! You risk severe engine damage!)

See what I mean? Both diesel and gasoline are fuels. They burn, produce gas, move pistons .. and voila: the vehicle in question is moving. That's the basic idea.

But that's about it as far as their similarities go.

Same with OS X, Linux, FreeBSD, Solaris and all the other Unix-like OS: Yes, on the surface they all look very similar. But that's about it. What they have in common is the basic "Unix idea" behind them.

---

### Post by 3rdalbum on 2009-07-16
There are some basic concepts that are similar between Mac OS X and Linux (like permissions and users, sockets and pipes) but little else. The kernel is different, all the APIs are completely different, the filesystem layout is completely different, the executable format is completely different, the GUI toolkit is completely different, and the preferred language for programming in OS X is not really a common language in Linux.

There is a small amount that is similar - for instance, the basic FreeBSD userspace is similar to Linux, and Mac OS X does have pipes, locks and the like - but Mac OS X native programs don't use any of that stuff. They use OS X-specific APIs. And although we talk about the FreeBSD userspace, it's more of a pick-and-mix with actual FreeBSD tools and strange Apple daemons ("Hey, let's implement users and permissions as a daemon!"). Even the open-source tools included in OS X have been heavily patched by Apple, even if just to remove features.

We can talk about the Mac OS X API - but that fails to acknowledge that there are two OS X APIs - Cocoa, which is fully-native, and Carbon which was the bridging gap between the classic Mac OS and OS X. Some important programs still use some Carbon calls!

So, basically, we'd have to reimplement an entire operating system with two different APIs, and support two different CPU architectures. The task would be bigger than implementing Windows via Wine. I don't think the little "Unix" in OS X would even make the job easier, as there really is so little in common between the two systems.

---

### Post by allenbradley on 2009-07-16
@3rdalbum and scorp : Thanks SO much for the clarification. Now I can argue with a certain degree of confidence. Now I finally understand why GNU's Not Unix! :)

---

### Post by sdlynx on 2009-07-17
I just realized what GNU/Linux is versus Linux.  Thanks a lot guys!

---

