---
title: "Old ieee80211 references"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by patronus on 2007-11-20
Hi,

I've an Intel Pro/Wireless Network Card and I'm running Gutsy; The card worked fine but i decided to update the driver.

Downloaded the ieee80211-1.2.18 and run:

```

root@Reversi:/home/patronus/ieee80211-1.2.18# . remove-old
Checking in /lib/modules/2.6.22-14-generic for ieee80211 components...
root@Reversi:/home/patronus/ieee80211-1.2.18# 

```

Everything fine so far; But when i run make:

```

root@Reversi:/home/patronus/ieee80211-1.2.18# make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
/bin/sh: Can't open /home/patronus/
Old ieee80211 references found.  In order to build the ieee80211
subsystem, prior versions must first be removed.  You can perform
this task by running this makefile as root via:

    % sudo make check_old

and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Error 1
root@Reversi:/home/patronus/ieee80211-1.2.18# 

```

Then I run make check_old that returns exactly the same!

I then find and deleted the files manually with:

sudo find /lib/modules/2.6.22-14-generic/ -name 'ieee80211*'
sudo find /lib/modules/2.6.22-14-generic/ -name 'ipw*'

And, again, run make, but the problem remains!

I dunno what else to do!!!

BTW: uname -r returns: 2.6.22-14-generic ;)

I found many other posts with this problem but found no answer, so I think there are many people out there waiting for a solution...

---

### Post by patronus on 2007-11-20
I solved the problem!

Just re-download the [ieee80211 file]("http://ieee80211.sourceforge.net/#downloads"), untar and run make.

Everything worked fine this time... I still don't understand why it return that error before.

---

