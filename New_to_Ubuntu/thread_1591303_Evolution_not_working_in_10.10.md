---
title: "Evolution not working in 10.10"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by paddymacmahon on 2010-10-09
I've been (happily) using ubuntu 10.04 for a while, and though I'd give 10.10 a whirl.  I updated from the upgrade manager (which I'm now slightly regretting, but what the hell), and everything seems OK, **except** that Evolution has given up communicating with my work's Microsoft Exchange server.

I've tried deleting the account details and re-entering them.  It seems it knows what folders are on my account (I can see names and sizes in 'account editor'), but it won't load any messages or my calendar/tasks.  If I click on the triangle next to the account name in the left hand section it briefly drops down to 'loading' for less than 0.5s and then just shows the account name.  No folders or messages downloaded.

Any ideas?

---

### Post by evijayanathan@gmail.com on 2010-10-11
Same Issue, for me also.

---

### Post by FizzBuzz on 2010-10-12
Same issue here.  This is day number 2 that I've been experiencing this problem.  The temporary workaround is to start evolution from the command line with the disable-eplugin flag:

evolution --disable-eplugin

You will want to make a backup of your settings at the end of the day, just in case.  When I fired up my evolution client this morning, it started from the setup screens as if I had never been using it!

Hopefully there will be a patch soon.

---

### Post by Raugturi on 2010-10-12
Lots of info on this bug here: [https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/631395]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/631395")

I was able to use the workaround suggested in that, which is to replace /usr/lib/evolution/2.30/plugins/liborg-gnome-exchange-operations.so with the one from the appropriate Debian package ([32bit]("http://packages.debian.org/sid/i386/evolution-exchange/download") - [64bit]("http://packages.debian.org/sid/amd64/evolution-exchange/download")).

---

### Post by broomie on 2010-10-13
This workaround (for 64 bit) worked for me - copying the .so file

Thanks very much

---

### Post by sorrro on 2010-10-27
They released fix in Maverick :guitar:

---

