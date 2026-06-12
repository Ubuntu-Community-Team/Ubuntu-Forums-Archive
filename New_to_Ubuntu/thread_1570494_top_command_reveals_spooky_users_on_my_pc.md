---
title: "top command reveals spooky users on my pc"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by nnjond on 2010-09-08
Hi,

As i understand the term. I am the only user on my pc. However when i 
```

~$ top

```

I get a display that claims my pc has five users! See att. top.png
Can you explain?

Also it seems to reveal i have only one gig of memory when i have a second card with 500mb on it totaling 1.5 gb.?

Thank for your time.

---

### Post by Calash on 2010-09-08
It is not 5 different users but 5 different services started using your account.  Any of the services listed under your name have the same permissions on the system as you do, being limited user.

It is normal on most every operating system to have more than one entry for a user, for system, or other semi-privileged accounts running in the background.

---

### Post by DrMelon on 2010-09-08
You may think you're the only user. In many cases, services have their own user to contain their permissions to certain areas. As far as I can see, two of the five are "root" (the main super-administrator account that is in fact the base of the system) and "nnjond" (which I presume to be you).

---

### Post by philinux on 2010-09-08
> **nnjond said:**
> Hi,

Also it seems to reveal i have only one gig of memory when i have a second card with 500mb on it totaling 1.5 gb.?

Thank for your time.

What does this show.

```
free -m
```

---

### Post by bredman on 2010-09-08
To check your memory usage, use the menu item
System / Administration / System Monitor
and select the tab Resources

---

### Post by nnjond on 2010-09-08
Thanks for your interest.


nnjond@linx-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        963         37          0         45        428
-/+ buffers/cache:        489        511
Swap:         4000          0       3999
nnjond@linx-desktop:~$

---

### Post by philinux on 2010-09-08
> **nnjond said:**
> Thanks for your interest.


```
nnjond@linx-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        963         37          0         45        428
-/+ buffers/cache:        489        511
Swap:         4000          0       3999
nnjond@linx-desktop:~$
```

Yep it's only showing 1gig. Does the bios show 1.5 at startup?

You only needed 2 gig swap max by the way. In fact see this re swap.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by bredman on 2010-09-08
It certainly looks like you have 1GB of memory.

Are you sure that the two banks of memory are compatible? If they are not compatible, only the first memory bank will be available.

---

### Post by TNT1 on 2010-09-08
Sorry for the question, but why do people use top, when system monitor will give you the same info?

---

### Post by philinux on 2010-09-08
> **TNT1 said:**
> Sorry for the question, but why do people use top, when system monitor will give you the same info?

Simply because system monitor can be a bit heavy on resource usage. Top is extremely light.

I think SM is better than it used to be.

---

### Post by Rubi1200 on 2010-09-08
You can also run this in the terminal to see users:
```
w
```

---

### Post by nnjond on 2010-09-08
Thanks for your comments. I am nnjond and the superuser. I can't think what you mean when you say their are others, (services), other than my isp, which have access to my pc?

---

### Post by philinux on 2010-09-08
> **nnjond said:**
> Thanks for your comments. I am nnjond and the superuser. I can't think what you mean when you say their are others, (services), other than my isp, which have access to my pc?

This is normal. Open system monitor on the processes tab. 

View>show all processes. And Edit>prefs>Processes. Tick user and then look down the processes.

You'll see things like ntp and haldaemon in the user column.

---

### Post by TNT1 on 2010-09-08
> **philinux said:**
> Simply because system monitor can be a bit heavy on resource usage. Top is extremely light.

I think SM is better than it used to be.


Fair. I guess my current daily machine spoils me... It has more resources than I need...

---

### Post by undecim on 2010-09-08
> **nnjond said:**
> Thanks for your comments. I am nnjond and the superuser. I can't think what you mean when you say their are others, (services), other than my isp, which have access to my pc?

A user doesn't always mean a physical person using the computer. "root" for example is the username used by the system. Since all files and processes have to be owned by someone, there is a user for many services. For example there is a user called "origami" on my computer that manages my processes for F@H.

This division of ownership is great for security. Imagine if someone found a flaw in F@H that allowed them to take control of the process on my computer over the network. It would give them the ability to run code as the origami user. Since the origami user is not a privileged user, it cannot install software and cannot access my personal files.

Many system processes are owned by the "root" user. The root user has absolute privilege over the system. It can do anything and everything that is computationally possible with a computer, including reading any files that are on the computer, changing any settings, and installing any software.

Also, I'd like to point out that you aren't the super-user. The user nnjond has no more direct privileges than any other user, with one exception. Using sudo (or gksu, which gives you the graphical password box, like when you install software from the software center) you (or any process that you own) can run another process as the root user, provided you have your password. This way, if someone takes over a process you own, they still need your password to get total access to the system.

---

### Post by anewguy on 2010-09-08
FYI - may not be the case with system monitor, as I don't know where it hooks in, but most system monitoring tools hook in to the OS at levels such that the monitor process itself takes a ton of resources.  Something like "top" is much lighter.

Dave

---

