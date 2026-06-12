---
title: "Connecting to AFP share"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by leo6 on 2013-09-21
I'm looking to connect to a mac via AFP for work, which also means I can't change any settings on the mac end. 

I've been able to connect occasionally in files but often it just ends up freezing, so I'm looking for a client for this.

I installed netatalk only to find out that it's for creating servers rather than a client, but I found [afpfs-ng]("https://sites.google.com/site/alexthepuffin/home") and I think it's what I'm looking for here.

I've installed all the packages it asks for, libfuse-dev, libgcrypt-dev, libgmp3-dev etc.

But when trying to compile it's now returning an error - I'm really not great here, as in I avoid compiling from source as I always forget how.

This is the error given after [I]make
[/I]
```
make[2]: Entering directory `/home/ar/Downloads/afpfs-ng-0.8.1/cmdline'gcc -DHAVE_CONFIG_H -I. -I..    -I../include -D_FILE_OFFSET_BITS=64 -g -O2  -g -O2 -MT afpcmd-cmdline_main.o -MD -MP -MF .deps/afpcmd-cmdline_main.Tpo -c -o afpcmd-cmdline_main.o `test -f 'cmdline_main.c' || echo './'`cmdline_main.c
cmdline_main.c:15:31: fatal error: readline/readline.h: No such file or directory
compilation terminated.
make[2]: *** [afpcmd-cmdline_main.o] Error 1
make[2]: Leaving directory `/home/ar/Downloads/afpfs-ng-0.8.1/cmdline'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ar/Downloads/afpfs-ng-0.8.1'
make: *** [all] Error 2



```

I'm wondering if there's a simpler way to connect AFP that I'm missing, none of this is well documented and a good deal of threads on it are broken - surely more people have had to connect to shared macs from linux?
If not, how can I get afpfs-ng to work?

Thanks.

---

### Post by Lars Noodén on 2013-09-22
Have you tried adding afpfs-ng from the repository yet?  I see it listed there.

---

