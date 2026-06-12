---
title: "Another Synaptic Package Manager problem"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by shoelar on 2009-02-12
when i log into the  Synaptic Package Manager this error message pops up:

[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]

I have tried running 'dpkg --configure -a' in terminal and it has said:

[COLOR="Red"]*****@********-laptop:~$ sudo dpkg --configure -a
[sudo] password for ********: 
Setting up ufw (0.23.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up cups (1.3.9-2ubuntu6.1) ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd                           [ OK ] 

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
[/COLOR]

What do i do now?:confused:

---

### Post by wolfen69 on 2009-02-12
do:

```
 *sudo* dpkg --configure -a
```

---

### Post by kestrel1 on 2009-02-12
> **wolfen69 said:**
> do:

```
 *sudo* dpkg --configure -a
```

If you look the OP has already used sudo.

---

### Post by shoelar on 2009-02-12
i found an other thread on the subject

[http://ubuntuforums.org/showthread.php?t=1065925]("http://ubuntuforums.org/showthread.php?t=1065925")

im updating and upgrading right now

---

### Post by shoelar on 2009-02-12
I got it to work!!!
Thanks for trying to help...

---

### Post by jerome1232 on 2009-02-12
> **shoelar said:**
> I got it to work!!!
Thanks for trying to help...

It would be great if you could describe how you got it to work, was the solution in that other thread you linked?

I was actually following this thread but had no idea how to help you get it to work :)

---

