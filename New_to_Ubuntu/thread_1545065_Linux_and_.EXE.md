---
title: "Linux and .EXE"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Zacinfinite on 2010-08-03
General architecture in any computer system is: Software <-> Kernel <-> Hardware

My question here is, Can't linux kernel be reprogrammed to run .exe files ""rather than using application like wine to run them""?



Any possibilities?

---

### Post by uRock on 2010-08-03
No. exe files are for Windows. What program are you looking to run, maybe there is a Linux equivalent.

---

### Post by cgroza on 2010-08-03
ReactOS is trying to do that. It is based on NT, not Linux and some programs work! Well its not impossible, who knows. But i doubt someone wants to start rebuilding the kernel from scratch to achieve this. It would take a lot of hard work, money and years to accomplish this!

---

### Post by uRock on 2010-08-03
> **cgroza said:**
> ReactOS is trying to do that. It is based on NT, not Linux and some programs work! Well its not impossible, who knows. But i doubt someone wants to start rebuilding the kernel from scratch to achieve this. It would take a lot of hard work, money and years to accomplish this!
Not to mention the possibility of MS suing for copyright infringement.

---

### Post by jerenept on 2010-08-03
and inviting all those nasty viruses for dinner.

If we rewrite the Linux Kernel to support Win32 and Win64 programs, not only do we lose the stability and security of Linux, it would take years of reverse-engineering the Windows operating system to make it even nearly as good as WINE is now.

---

### Post by jmszr on 2010-08-03
Not to mention the resulting ability to run .exe viruses and malware.

---

### Post by Mark Phelps on 2010-08-03
> **Zacinfinite said:**
> My question here is, Can't linux kernel be reprogrammed to run .exe files ""rather than using application like wine to run them""?Any possibilities?

An MS Windows .exe file is basically a collection of realtime libary calls (to oversimplify it a bit!) MS Windows apps make calls to runtime libraries (usually .DLL files), which in turn, make calls to the OS.  

Wine works because they replaced some of the MS Windows DLL files with their own that make runtime calls to Linux functions instead of MS Windows OS functions.

So, it's not a "kernel" problem, it's a problem with runtime libraries.

---

### Post by QIII on 2010-08-03
Why don't we just invite DirectX, ActiveX and IE in, too?  Then we'd have all four of the Horsemen.

To be honest, you can get .NET to work in Linux through Mono.  Don't know what I think about that yet.

---

### Post by Zacinfinite on 2010-08-03
-So if it is problem of runtime libraries and not the kernel, then can something be done?
-Im not sure how long wine will go cause there are some performance issues. 
-What do you think? 
-Will there be a day when u put a high graphic game Cd and install it right-away and start playing without compromising the performance using WINE?

-And concerning Viruses and malware I guess its not the .EXE problem, It the fault of MS windows system policy. Linux policies are very awesome thats y it is so secured with no virus threat even if u make one.

---

### Post by mcduck on 2010-08-03
Of course something can be done, and that something *is* Wine.

The day when you can plug in a decent graphics card and play any game you buy without using Wine is the day when graphics card manufacturers start providing decent drivers for their hardware and the game developers start making their games to run natively on Linux (some are already doing that).

You need to remember that the target is not to be able to run Windows apps easily, that's what Windows is for. It's getting good native applications for Linux.

If you wanted to make Linux run Windows apps just like Windows does, you'd pretty much end trying to replicate what Windows itself, including all the good *and* the bad things. While some people (ReactOS, for example) try to do that, Linux is heading to be as good operating system as it can and that isn't something you can achieve by trying to replicate what others are doing.

---

### Post by Keen101 on 2010-08-03
haha. hmm.. you must be a recent windows convert, or someone whos used windows for a long time. Dont worry many of us used to be in the same boat.

..I suppose you could create a new kernel and library from scratch to emulate windows, and if you want that, then yeah take a look at ReactOS.

If not, the best way to run windows programs on linux in my opinion is Virtualbox. I havent tried Wine in a very long time, but it never was up to par in my opinion, and i eventually lost interest in windows programs all together.

My advice would be to support game companies that release games for Linux. Try Penumbra Overture, Lugaru, Gish, Uplink, Defcon, and other games....

---

### Post by spydeyrch on 2010-08-03
> **mcduck said:**
> Of course something can be done, and that something *is* Wine.

The day when you can plug in a decent graphics card and play any game you buy without using Wine is the day when graphics card manufacturers start providing decent drivers for their hardware and the game developers start making their games to run natively on Linux (some are already doing that).

You need to remember that the target is not to be able to run Windows apps easily, that's what Windows is for. It's getting good native applications for Linux.

If you wanted to make Linux run Windows apps just like Windows does, you'd pretty much end trying to replicate what Windows itself, including all the good *and* the bad things. While some people (ReactOS, for example) try to do that, Linux is heading to be as good operating system as it can and that isn't something you can achieve by trying to replicate what others are doing.


I couldn't have said it better my self!  It is almost poetic in nature.  ;)

...... But I would agree. The goal shouldn't be to force the OS to bend to the will of the software but it should be that the software conform to the will of the OS.  

We shouldn't try to get windows programs onto linux, that is what windows is for. If one wants a windows program, then why run linux? The goal should be to get the companies, engineers, & developers to write native software/drivers for linux. You would get rid of the performance issues that you mentioned you have with wine, you wouldn't have to re-write the kernel, and you would still be running linux, plus you would have the programs that you want/need ...... and all native to linux!!!! :D

Plus, the windows way of doing things honestly, in my opinion, is very inefficient. But that is for everyone to make their own opinion about.

-Spydey :KS

---

