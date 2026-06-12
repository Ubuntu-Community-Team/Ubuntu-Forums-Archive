---
title: "Many problems at once!"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by rachidas on 2008-12-05
Hi everybody, I'm new here (it's my first post) so please excuse my ignorance as well as my poor english...:oops:
I had the Ubuntu 8.04LTS then I upgraded to the 8.10, and it went perfectly well... but then I installed some packages, including java6 and other (restricted or not recommended or wathever the message called it...) ignoring the warning message... then I rebooted...
and then lots of things went wrong beggining by compiz desktop effects, firefox won't start (XPCOM problem), and synaptic...
with synaptic I get this message:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so I did what it said when I got this (as root and everything...)
```
Setting up libc6 (2.8~20080505-0ubuntu7) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Aborted
dpkg: subprocess post-installation script returned error exit status 134

```

I searched for the solution to this in the forum and found few posts that didn't solve my problem including
[this one]("http://ubuntuforums.org/showthread.php?t=982090&highlight=dpkg%3A+subprocess+post-installation+script+returned+error+exit+status+134") and [this one]("http://ubuntuforums.org/showthread.php?t=906314&highlight=dpkg%3A+subprocess+post-installation+script+returned+error+exit+status+134")
thanks in advance for your help :p

---

### Post by Liunx on 2008-12-05
Hello, 
  I also met this problem when i install the java with ubuntu teak's recommend,
but be relax, you can uninstall the java, and install icetea java runtime-- a open version, i am sure it'll be fine.
:popcorn:

---

### Post by hyper_ch on 2008-12-05
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by rachidas on 2008-12-05
Thanks Liunx for the answer, but unfortunately I can't install or uninstall anything since this dpkg error message keeps showing :(
And I'll try to edit my post following your recommandations hyper_ch :)

---

### Post by handydan918 on 2008-12-05
A little googling shows...

> Exit code 134: The job is killed with an abort signal, and you probably got core dumped. Often this is caused either by an assert() or an ErrMsg(fatal) being hit in your job. There may be a run-time bug in your code. Use a debugger like gdb or dbx to find out what's wrong.

Maybe a bug report is needed?

---

### Post by rachidas on 2008-12-05
I don't know how to do that :( 
can you please explain more the process? :)

---

### Post by rachidas on 2008-12-05
Okay I did that I found the bug reporting tutorial...
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/305496](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/305496)

---

