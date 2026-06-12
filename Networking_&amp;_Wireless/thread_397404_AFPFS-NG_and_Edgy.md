---
title: "AFPFS-NG and Edgy"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by jevolution on 2007-03-30
I'm trying to install and use afpfs-ng-0.4

When I try to do "make install" I get the following output. Any idea what I can do to get this to work?

> jason@plantivore:~/Desktop/afpfs-ng-0.4$ sudo make install
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-fuse_int.o -MD -MP -MF ".deps/afpfsd-fuse_int.Tpo" -c -o afpfsd-fuse_int.o `test -f 'fuse_int.c' || echo './'`fuse_int.c; \
        then mv -f ".deps/afpfsd-fuse_int.Tpo" ".deps/afpfsd-fuse_int.Po"; else rm -f ".deps/afpfsd-fuse_int.Tpo"; exit 1; fi
fuse_int.c: In function ‘afp_getattr’:
fuse_int.c:206: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_rmdir’:
fuse_int.c:434: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_unlink’:
fuse_int.c:494: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_readdir’:
fuse_int.c:560: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_mknod’:
fuse_int.c:678: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_release’:
fuse_int.c:748: warning: cast to pointer from integer of different size
fuse_int.c:767: warning: cast to pointer from integer of different size
fuse_int.c:796: warning: cast to pointer from integer of different size
fuse_int.c: In function ‘afp_open’:
fuse_int.c:823: warning: assignment makes integer from pointer without a cast
fuse_int.c:837: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_write’:
fuse_int.c:1065: warning: cast to pointer from integer of different size
fuse_int.c:1086: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c:1090: warning: implicit declaration of function ‘volinfo_write’
fuse_int.c: In function ‘afp_read’:
fuse_int.c:1282: warning: cast to pointer from integer of different size
fuse_int.c:1290: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_truncate’:
fuse_int.c:1466: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c:1478: warning: cast to pointer from integer of different size
fuse_int.c: At top level:
fuse_int.c:2033: warning: initialization from incompatible pointer type
fuse_int.c:2045:61: error: macro "fuse_main" passed 4 arguments, but takes just 3
fuse_int.c: In function ‘afp_register_fuse’:
fuse_int.c:2045: error: ‘fuse_main’ undeclared (first use in this function)
fuse_int.c:2045: error: (Each undeclared identifier is reported only once
fuse_int.c:2045: error: for each function it appears in.)
make: *** [afpfsd-fuse_int.o] Error 1


---

### Post by jevolution on 2007-04-02
Still looking for any help. Thanks.

---

### Post by jevolution on 2007-04-17
Any guidance where I can go for help?

---

### Post by ericcartman on 2007-06-01
Hi,

perhaps you don't have the fuse-development package installed? (fuse_int.c:2045: error: ‘fuse_main’ undeclared (first use in this function)->makes me think this could be the problem).

=> ```
aptitude install libfuse-dev
```

greetings ericcartman

---

### Post by jevolution on 2007-06-05
Thanks, but it says I have the newest version already installed.

---

### Post by alexthepuffin on 2007-08-01
> **jevolution said:**
> Thanks, but it says I have the newest version already installed.

I'm the author of afpfs-ng.  If you can retry this with afpfs-ng 0.4.1, I'll have a look at it. 

What version of fuse are in edgy?

- A

---

### Post by HS-L on 2007-08-20
```
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-commands.o -MD -MP -MF ".deps/afpfsd-commands.Tpo" -c -o afpfsd-commands.o `test -f 'commands.c' || echo './'`commands.c; \
        then mv -f ".deps/afpfsd-commands.Tpo" ".deps/afpfsd-commands.Po"; else rm -f ".deps/afpfsd-commands.Tpo"; exit 1; fi
commands.c:9:27: error: fuse/fuse_opt.h: No such file or directory
In file included from commands.c:25:
afp.h:11:1: warning: "FUSE_USE_VERSION" redefined
In file included from /usr/include/fuse/fuse.h:19,
                 from /usr/include/fuse.h:9,
                 from commands.c:8:
/usr/include/fuse/fuse_common.h:17:1: warning: this is the location of the previous definition
commands.c: In function ‘start_fuse_thread’:
commands.c:145: warning: implicit declaration of function ‘get_debug_mode’
commands.c:160: warning: passing argument 2 of ‘afp_register_fuse’ from incompatible pointer type
commands.c: In function ‘process_mount’:
commands.c:635: warning: passing argument 3 of ‘new_server’ from incompatible pointer type
make: *** [afpfsd-commands.o] Error 1

```

:/

any clue what went wrong?
got the error on a dapper server when i entered make install

---

### Post by jevolution on 2007-09-04
Thanks. It worked with the newer version. Now to just give it a try...

---

