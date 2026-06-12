---
title: "First CPU doing most work, over-performing"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by dEXm on 2010-11-23
Hello

I installed Ubuntu 10.10 today (inside Windows 7 using Wubi). I'm really loving it so far. The only thing bothering me at the moment is how noisy my laptop has gotten; it sounds as if it's running a really intensive program. When running Windows 7 my laptop never gets this 'active' unless I'm playing games and such. I checked the system monitor and it seems that my first CPU is doing almost all the work instead of distributing the load. 

Here's an image of what's happening:
[http://img3.imageshack.us/img3/4227/screenshot2nph.png]("http://img3.imageshack.us/img3/4227/screenshot2nph.png")

I updated my Nvidia drivers as suggested by the software center and updated all other available drivers. Still the problem persists.

I've got an Intel i7 720QM @ 1,6 GHz processor and Nvidia FX880M videocard. I don't know of anything else that could be relevant at the moment.

If you'd like some additional information, I'll be glad to post more.

Win7 performance:
[http://img839.imageshack.us/img839/7149/cpuperfwin7.png]("http://img839.imageshack.us/img839/7149/cpuperfwin7.png")

Thanks in advance!

---

### Post by marshmallow1304 on 2010-11-24
Is there a single process that's using a lot of CPU?  Flash maybe?

---

### Post by dEXm on 2010-11-24
Nope, the computer behaves this way even when no other program is launched/has been launched.

edit:

this is how it runs on Win7
[http://img839.imageshack.us/img839/7149/cpuperfwin7.png]("http://img839.imageshack.us/img839/7149/cpuperfwin7.png")
As you can see it's much more balanced.

---

### Post by Decatf on 2010-11-24
gnome system monitor itself can eat up CPU. It's better to monitor CPU usage in a terminal with **top**.

---

### Post by kroq-gar78 on 2010-11-24
> **Decatf said:**
> gnome system monitor itself can eat up CPU. It's better to monitor CPU usage in a terminal with **top**.
top can monitor individual CPUs?

---

### Post by Decatf on 2010-11-24
> **kroq-gar78 said:**
> top can monitor individual CPUs?
Press **1** to toggle the individual display.

---

### Post by dEXm on 2010-11-24
Why is Windows managing my CPUs differently though? You'd think that since it's an installation inside of Windows the same drivers would apply.
I remember there being an issue with multi core processors in Windows where you'd have to change system settings for each individual drive to behave in line with the rest, allocating CPU processes more efficiently. Is there such an application for Ubuntu?
Even my battery life has been cut in half because of this mismanagement.

---

### Post by mcduck on 2010-11-24
Wubi install is just inside the Windows filesystem, it's not running inside Windows (that's what a virtual machine would do). Wehn you are running Ubuntu, you are *only* running Ubuntu. It just needs to access it's files through two filesystems instead of one.

Anyway, the behavior you see is normal, not all computing tasks can be effectively broken into multiple threads, and a single-thread application will only use one CPU core. On the the other hand it *isn't* normal to have any singe task using that much CPU when the system should be idle. And *that's* what you actual problem probably is.

Forget about the pretty graphs, and instead check the processes-tab to see what process is using the CPU.

---

### Post by dEXm on 2010-11-24
> **mcduck said:**
> Wubi install is just inside the Windows filesystem, it's not running inside Windows (that's what a virtual machine would do). Wehn you are running Ubuntu, you are *only* running Ubuntu. It just needs to access it's files through two filesystems instead of one.

Anyway, the behavior you see is normal, not all computing tasks can be effectively broken into multiple threads, and a single-thread application will only use one CPU core. On the the other hand it *isn't* normal to have any singe task using that much CPU when the system should be idle. And *that's* what you actual problem probably is.

Forget about the pretty graphs, and instead check the processes-tab to see what process is using the CPU.

I checked those before. Nothing that could be causing this.

I posted the graph to illustrate my problem, which a long process list wouldn't do as well.

It was suggested to check top and so I did. *It seems that a process named 'kacpid' is the evildoer, taking up as much as 95% of my CPU.* Here's an image of the top scan:

[http://img221.imageshack.us/img221/7074/screenshot1wy.png]("http://img221.imageshack.us/img221/7074/screenshot1wy.png")

Any ideas on how to fix this?

---

