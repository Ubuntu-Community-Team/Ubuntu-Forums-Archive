---
title: "Ubuntu 10.04 Update Manager Problems with 3G"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2010-10-12
Hiya Everyone,

I am using a Vodafone K3565 - V2 3G Modem

My update manager is refusing to install "libc" updates, "xulrunner" and "erlang" updates (download speed becomes "unknown" and doesn't respond) all others it has accepted ok (I had to force some using deb package downloads)

When i tried to install the "Libc" updates my update manager hung and download speed changes to "Unknown" (I have tried to install it manually via deb but I get "Breaks existing dependancy errors).

Can anyone help out with this?

---

### Post by Nightstrike2009 on 2010-10-12
I think this maybe just packages that have bugs can anyone else confirm having this problem too?

---

### Post by Nightstrike2009 on 2010-10-13
Sometimes I dont know why I bother posting :-(

Ive got "xulrunner" installed via deb package, the other two seem to have dependancy issues. :-(

Thanks again for leaving me to it and all the none existant suggestions, hope the info I provided helps others out. :-)

---

### Post by Nightstrike2009 on 2010-10-13
Can anyone else help even if this is unresolved it needs to reporting to devs if we all suffer this problem?

---

### Post by prshah on 2010-10-13
Just a thought which may or may not be right: Are you running Linux Chrome, with the Google custom PPA?

I faced similar issues with erlang and libc6, but when I realized the dependencies were for Chrome (and saw a whole huge other list of dependencies) I was spooked enough to remove Chrome and it's PPA. (Why does Google Chrome browser need erlang - a programming language- dependency?)

May or may not be right, YMMV, don't knock it, etc.

---

### Post by CharlesA on 2010-10-13
Have you tried a different form of network connection? Hardwired instead of wireless?

It sounds like a network connectivity problem tbh, or a mirror is having problems.

I have libc6 installed on Lucid, but I'm not running any custom PPAs:

```
charles@atlantis:~$ dpkg -l | grep libc6
ii  libc6                           2.11.1-0ubuntu7.2                 Embedded GNU C Library: Shared libraries
```

---

### Post by Nightstrike2009 on 2010-10-14
Hello prshah,

Chromium browser had been installed and removed on 10.04, I prefer Firefox.

Also to CharlesA, I am sorry my friend 3G is my only connection to the internet I have no hardwired option. I am running Medibuntu PPA but thats the only one.

Phosphorror told me it maybe a 3g problem and maybe down to the networks reluctance to roll out 4G (Part of the same social off forum Ubuntu users as myself and among the two I have helped converted to ubuntu one directly and one in-directly). Its a shame Ubuntus tech cannot be altered to overcome this as we speak, maybe a update manager that downloads in sections maybe more successfull.

---

