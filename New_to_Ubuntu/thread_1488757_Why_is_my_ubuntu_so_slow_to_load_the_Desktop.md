---
title: "Why is my ubuntu so slow to load the Desktop?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by marciomendonsa on 2010-05-20
Why is my ubuntu so slow to load the Desktop?


Okay. The system initialization is fast. But what happens **after the login**, there is a delay of about 37 secs, so the Desktop is available. Why is that?!

**This only happens on the first login.** If I logout and login as another user nally, the desktop loads fast.

I'm using Lucid Lynx 64bits  on a PC with 4GB of RAM and a 2.8GHz AMD processor.

---

### Post by Kevanx on 2010-05-20
I'm not an expert about boot times, but I do know that the more applications that need to start up in the background, the slower it tends to take, particularly graphics-intensive processes.

Your best bet, to start with is to go to System > Preferences > Startup Applications, and seeing if there is anything that you don't need running automatically.

If that doesn't make much of a difference, consider disabling graphics-intensive eyecandy like Compiz, to see if that does anything.

Finally, there are methods by which you can log your boot, but I've never done it. A quick search of the forums should turn up tons of howtos.

---

### Post by philinux on 2010-05-20
> **marciomendonsa said:**
> Why is my ubuntu so slow to load the Desktop?


Okay. The system initialization is fast. But what happens **after the login**, there is a delay of about 37 secs, so the Desktop is available. Why is that?!

**This only happens on the first login.** If I logout and login as another user nally, the desktop loads fast.

I'm using Lucid Lynx 64bits  on a PC with 4GB of RAM and a 2.8GHz AMD processor.

This is a known lucid bug.  [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712)

If you have no floppy try disabling it in your bios.

---

### Post by marciomendonsa on 2010-05-20
> **Kevanx said:**
> 
Your best bet, to start with is to go to System > Preferences > Startup Applications, and seeing if there is anything that you don't need running automatically.

I already did. Remained the same.   :(

> 
If that doesn't make much of a difference, consider disabling graphics-intensive eyecandy like Compiz, to see if that does anything.

Before I enable eyecandy, this problem has existed

---

### Post by laidback on 2010-05-20
There's a program called bootchart for the 32 bit version...it's in the repository. Can't say I fully understand the output but you will probably have a better idea.

---

### Post by marciomendonsa on 2010-05-20
> **laidback said:**
> There's a program called bootchart for the 32 bit version...it's in the repository. Can't say I fully understand the output but you will probably have a better idea.

The problem isn't in the boot, but after login.

---

### Post by philinux on 2010-05-20
Post #3

---

### Post by marciomendonsa on 2010-05-20
> **philinux said:**
> Post #3

When I get home, I'll try that.

Thank you.    :)

---

### Post by Excedio on 2010-05-20
> **philinux said:**
> This is a known lucid bug.  [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712)

If you have no floppy try disabling it in your bios.

AWESOME! This fixed it for me. :-D

---

