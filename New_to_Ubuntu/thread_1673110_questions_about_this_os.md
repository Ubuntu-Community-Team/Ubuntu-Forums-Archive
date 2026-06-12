---
title: "questions about this os"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Unguidedone on 2011-01-21
I'm on windows (plz don't flame)  but im considering changing my os to ubuntu because my anti virus is really slowing down my computer.  A few things I dont understand about this os even after hours on google is :

1. How does it have no viruses?  (do you even need an anti virus program?)
2. Why is this os significantly faster then windows (I do know windows tends to "preload documents ect"

[http://www.youtube.com/watch?v=FEvD9RHlccc](http://www.youtube.com/watch?v=FEvD9RHlccc)

3.  What assembly lanaguge is this made in?

4. does this os support autoit?
[http://www.autoitscript.com/autoit3/index.shtml](http://www.autoitscript.com/autoit3/index.shtml)
(I found nothing on the page about it)




:shock:

---

### Post by dFlyer on 2011-01-21
I'll answer your first question. It's not that there are no virus. It's that a virus for linux is very rare and it can not infect your system other than your home directory as that is the only directory you will have write permission for without being super user. I'm sure there are ways around that but, I've been using linux since the mid 90's and I've never been hacked and never have had a virus. If your worried about virus they do have virus scanners for linux, mainly to protect mail servers that forward mail to window users.

---

### Post by dheerajrav on 2011-01-21
And to answer your last question

U can run autoit using wine

this can be installed by typing this on the command line
```
sudo apt-get install wine
```

---

### Post by Jetso on 2011-01-21
As for why the OS is faster, that would be because... I'm not sure. But the way I figure it, why question it. I have Ubuntu on a year 2000, 256 RAM, 20GB Hard Drive computer and it runs faster than Windows on this laptop, which is fairly new. As for being able to run programs, all you need to use Window's .exe's is Wine, which I or anyone on these forums can help you install or use. Also, about question 3, I'm not sure I get it. But if it helps the default shell is bash, which is very easy to use.

---

### Post by 3rdalbum on 2011-01-21
> **Unguidedone said:**
> I'm on windows (plz don't flame)  but im considering changing my os to ubuntu because my anti virus is really slowing down my computer.  A few things I dont understand about this os even after hours on google is :

1. How does it have no viruses?  (do you even need an anti virus program?)

Well, it doesn't run Windows viruses, because it's a totally different operating system to Windows. There are no Linux viruses (maybe a couple of rootkits and trojans, but these are exceedingly rare) because it's difficult to write them for Linux.

Linux developers are quite concious of security, and design their programs and the operating system to be secure "by design". By contrast, Windows was originally written without much security, and it's been "bolted-on" as an afterthought in recent years. Third-party application developers on Windows haven't been too concerned with security either.

And finally, Linux users tend to run their systems with common-sense, so are less likely to be enticed to run "anna_kornakova.jpg.exe".

> 2. Why is this os significantly faster then windows (I do know windows tends to "preload documents ect"

Sometimes it doesn't; it depends on your exact setup. But in the last couple of years Ubuntu has been putting a lot of focus on improving startup speed.

> 3.  What assembly lanaguge is this made in?

Ubuntu isn't just one product; it's a collection of smaller projects. Some, like the Linux kernel, are written in C. Others are written in C++, or C# (Mono), Perl, or Bash scripting. Much of the Ubuntu-specific parts are written in Python.

There's probably very little assembly language in Ubuntu, because it's not portable across CPU architectures. Ubuntu itself runs on x86, x86_64 (AMD64) and ARM as supported architectures and has been ported to many others.

> 4. does this os support autoit?
[http://www.autoitscript.com/autoit3/index.shtml](http://www.autoitscript.com/autoit3/index.shtml)
(I found nothing on the page about it)

*AutoIt v3 is a freeware BASIC-like scripting language designed for automating the Windows GUI and general scripting*

Ubuntu bears no relation to Windows, so I'd say it's extremely unlikely. Linux doesn't even run Windows programs natively - it's an entirely different operating system. There's a project called Wine that creates a compatibility layer for some Windows programs to work, but it's really just meant as a last resort.

If you want to do general scripting, you should have a look at Bash scripts, or (even better IMHO) Python.

---

### Post by DOSIX on 2011-01-22
Part of the reason why it's faster is because the Linux kernel is optimized to be run on as much hardware as possible. This includes much older hardware. This optimization makes the kernel very lightweight. As opposed to microkernel design, which uses messages passed by various components of the core operating system, Linux uses a modular monolithic kernel. This means that the kernel itself is a single program, however, drivers and the like are added modularly, improving efficiency. It also helps that there are literally tons of people around the world working on the code for the thing all day every day.

---

### Post by dheerajrav on 2011-01-22
[http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

Read this.

---

