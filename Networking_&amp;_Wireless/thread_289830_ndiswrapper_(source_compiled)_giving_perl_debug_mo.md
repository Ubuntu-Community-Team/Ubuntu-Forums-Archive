---
title: "ndiswrapper (source compiled) giving perl debug mode -- error?"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by nyinge on 2006-10-31
```
$ndiswrapper
```
would always go into a perl debug mode like the following:
```

Loading DB routines from perl5db.pl version 1.28
Editor support available.

Enter h or `h h' for help, or `man perldebug' for more help.

main::(/usr/sbin/ndiswrapper:26):       my $WRAP_PCI_BUS = 5;
  DB<1> 

```

It also happens when I try to install the windows driver as follows:
```

ndiswrapper -i some_window_driver.ini

```

Basically, no matter what I do with ndiswrapper, it will always enter into the debug mode.
P.S.  At least I think it's the perl debug mode.

---

### Post by mavr on 2006-11-01
i had the same trouble with the 1.8 out of sourceforge.

---

### Post by nyinge on 2006-11-01
Did you try the stable version or the testing version?  I got it working with the stable version, but not current stable version - it was a few weeks ago, 1.26 or something.

It seems newer versions are causing this problem.  It may have to do with something the ndiswrapper devs put in some new stuff in the code.  I'm not a programmer, so I have no clue whatsoever.

---

