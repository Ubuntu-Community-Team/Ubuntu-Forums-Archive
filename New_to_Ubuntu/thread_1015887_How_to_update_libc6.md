---
title: "How to update libc6"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by ScEngMan on 2008-12-19
Hello,

I tried to install TuxPaint in my Ubuntu 7.10 but the installer says it can't because my libc6 version is old.

The libc6 version installed in my system is 2.5, but TuxPaint requires 2.6.

I tried to update libc6 using Synaptic but there is no update option for it.

A few weeks ago I had a similar problem with libglib and I updated it (I don't remember how, maybe just download, build and install) and Ubuntu just died (it's still dead... I guess I'll ask in another thread how to bring it back to life)... So this time I don't want to kill my new Ubuntu, so how can I update this library?

Thank you,
Diego

---

### Post by sdennie on 2008-12-19
What version of Ubuntu are you running?  In Hardy the libc is 2.7 and in Gutsy it is 2.6 so, it sounds like you may be running an unsupported version of Ubuntu (anything before Gutsy is now unsupported).  I would recommend upgrading or you may face a lot of these sorts of problems.

---

### Post by ScEngMan on 2008-12-19
I'm running 7.10.
I tried to install 8.04 in that pc but it hangs on start-up.
Thanks,
Diego

---

### Post by sdennie on 2008-12-19
You shouldn't have these problems if you are running 7.10.  In a 7.10 VM I get the following:

```

sdennie@ubuntu-clean-vm:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
sdennie@ubuntu-clean-vm:~$ ls -l /lib/libc-*
-rwxr-xr-x 1 root root 1249520 2007-10-24 19:03 /lib/libc-2.6.1.so

```

---

### Post by ScEngMan on 2008-12-19
Sorry, I was wrong... I installed 7.04... Feisty Fawn.
Is there an update option without reinstalling the thing?
Thank you
Diego

---

