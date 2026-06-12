---
title: "Ubuntu 10.04: Compile Error Help"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by SexySara on 2011-02-23
What am I missing? What do I need to fix the errors?
```

~/Desktop/iwar-0.07$ make
make  all-am
make[1]: Entering directory `/home/soultravel369/Desktop/iwar-0.07'
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -D_POSIX -g -O2 -MT iwar-engine.o -MD -MP -MF ".deps/iwar-engine.Tpo" -c -o iwar-engine.o iwar-engine.c; \
    then mv -f ".deps/iwar-engine.Tpo" ".deps/iwar-engine.Po"; else rm -f ".deps/iwar-engine.Tpo"; exit 1; fi
iwar-engine.c: In function ‘sendmodem’:
iwar-engine.c:281: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
iwar-engine.c:288: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
iwar-engine.c:297: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
iwar-engine.c: In function ‘main’:
iwar-engine.c:1696: error: ‘AUDIO_INTERNAL_PA’ undeclared (first use in this function)
iwar-engine.c:1696: error: (Each undeclared identifier is reported only once
iwar-engine.c:1696: error: for each function it appears in.)
iwar-engine.c:1696: error: too many arguments to function ‘iaxc_initialize’
iwar-engine.c:1692: warning: ignoring return value of ‘freopen’, declared with attribute warn_unused_result
make[1]: *** [iwar-engine.o] Error 1
make[1]: Leaving directory `/home/soultravel369/Desktop/iwar-0.07'
make: *** [all] Error 2
~/Desktop/iwar-0.07$ 

```

---

### Post by deconstrained on 2011-02-23
Did you dowload and install all the software's dependencies? For most software libraries there is a supplementary development package (whose name ends in -dev) that provides header files necessary for compiling programs that depend on that library.

---

### Post by komputes on 2011-02-23
The iWar documentation says it was tested on Gentoo/Slackware. I looked up the build error on the iWar mailing list and found this:

> The iaxc_initialize() function in iaxclient was changed.   They
removed an argument around iaxclient-2.0.1 (or so).   With iWar/CVS,  you'll 
want to use the latest/greatest iaxclient (iaxclient-2.1beta3) from 
[http://iaxclient.sf.net]("http://iaxclient.sf.net/"). 
Source: [http://www.mail-archive.com/iwar@mailman.softwink.com/msg00067.html](http://www.mail-archive.com/iwar@mailman.softwink.com/msg00067.html)

Hope that helps. If not, you can always try the iwar mailing list at [http://bundy.vistech.net/mailman/listinfo/iwar](http://bundy.vistech.net/mailman/listinfo/iwar)

---

### Post by SexySara on 2011-02-23
> **deconstrained said:**
> Did you dowload and install all the software's dependencies? For most software libraries there is a supplementary development package (whose name ends in -dev) that provides header files necessary for compiling programs that depend on that library.Yah I sure did, I read the Read Me txt and then when I ran the configure command it told me what I needed and I installed them all.

> **komputes said:**
> The iWar documentation says it was tested on Gentoo/Slackware. I looked up the build error on the iWar mailing list and found this:

Source: [http://www.mail-archive.com/iwar@mailman.softwink.com/msg00067.html](http://www.mail-archive.com/iwar@mailman.softwink.com/msg00067.html)

Hope that helps. If not, you can always try the iwar mailing list at [http://bundy.vistech.net/mailman/listinfo/iwar](http://bundy.vistech.net/mailman/listinfo/iwar)Thanks for the info, I will give that a shot!

---

