---
title: "[SOLVED] installing pctel modem drivers in 8.04"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by shssta on 2008-09-26
Hi guys and gals,

This isnt my first rodeo trying to get these things to work, but I am having an issue. I am running a triple boot setup with 6.10, 8.04, and windows 2000. The reason I never updated from 6.10 was because of how hard it was to get the modem working the first time. To be honest I don't know exactly how I did it. 

But anyway, I went and downloaded the latest pctel modem driver for my chip, pct789. Same one as the one that im using right now in 6.10 that works, just updated for the newer Kernel, which is 2.6.24. 

I then unpackaged it as usual, went into the folder and the instruction say to run ./setup, here is what i get
```

shasta@shasta-desktop:~/Desktop/pctel-0.9.7-9-rht-9$ ./setup
checking for running kernel version...2.6.24
checking for ptserial...ptserial-2.6.c
checking for gcc...4.2.3
checking for kernel gcc version...4.2.3
searching for kernel includes...found at /lib/modules/2.6.24-19-generic/build/include
checking for autoconf.h.../lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in utsrelease.h...t.c:1:19: error: stdio.h: No such file or directory
t.c: In function ‘main’:
t.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
./configure: line 477: ./t: No such file or directory
rm: cannot remove `./t': No such file or directory
** error
could not determine a proper UTS_RELEASE
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.
```

anybody know if there is anything i can do to get this working? Ill come back with the make.log info as soon as i can reboot and find it.

---

### Post by shssta on 2008-09-26
this is all the make.log shows

```
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by shssta on 2008-09-26
*double post, sorry

---

### Post by shssta on 2008-09-26
ok realized i have an issue with build-essential, apprently my drive wont read all the files through synaptic, so im going to try downloading them and installing them from teh hard drive, I will let you all know how it goes.

---

### Post by shssta on 2008-09-26
figured it out, had to swap out my cd drive...

... also on a side note to the creators of the modem driver, in the readme file you need to make it a little more clear that you have to be root, maybe add "sudo" to the part that tells users to type ./setup in terminal. That was my problem last time and I forgot to do it this time too.

---

