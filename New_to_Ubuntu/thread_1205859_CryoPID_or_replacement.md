---
title: "CryoPID or replacement"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by protargol on 2009-07-06
I want a tool that can freeze a process so I can reboot and resume the process later.  CryoPID supposedly can do that, but I'm running Jaunty so it's not in the package database and I'm having trouble with "make" to compile it.  That gives me:```
make: arch: Command not found
make: arch: Command not found
make: arch: Command not found
make: arch: Command not found
make: arch: Command not found
! test -h arch && rm -f arch && ln -s arch- arch || true
make -C arch 'CFLAGS+=-DUSE_TCPCP -fno-stack-protector'
make: *** arch: No such file or directory.  Stop.
make: *** [arch] Error 2

```

Is their a replacement or substitute for CryoPID?  Thanks

---

### Post by scottopoly on 2009-07-28
Bump.

Same thing happens for me. Server ubnutu 9.04 amd64.

---

### Post by xcthulhu on 2009-07-28
I had this trouble too.  What I can tell you that arch is deprecated that you're supposed to use "uname -m".  However, I stumbled on later parts of the compilation, which involved linux header files...

Fortunately, googling "cryopid jaunty" gives this discussion, and also this page:

[https://launchpad.net/ubuntu/jaunty/+package/cryopid](https://launchpad.net/ubuntu/jaunty/+package/cryopid)

...which has links to .deb files for ia64 and x86 :P

Cheers,
xct

---

### Post by scottopoly on 2009-07-29
Are you saying you actually got it working? I didn't see any dep packages at the link you gave. I eventually found

[http://en.wikipedia.org/wiki/Application_checkpointing](http://en.wikipedia.org/wiki/Application_checkpointing)

and looked at cryopid2. I worked with its installation script and still had several build errors. I worked out some of them, it was looking in the wrong location for the linux headers for example, but no dice.

---

### Post by scottopoly on 2009-07-29
Alas, the links were on the right!

And it works! (mostly)

- Only works as root (both saving and restarting, must be root)
- The new process seems to think it's the old process, signals it sends get sent to the old process if it's still running, probably lost otherwise. New process thinks its pid is the old process's pid. (found this out using the "testers" in the cryopid source)

Thanks.

---

### Post by karya0 on 2009-12-06
You might also want to try DMTCP. It can checkpoint/restart user processes without any root privileges and it support a whole bunch of operating system features. For more information, visit their homepage:
[http://dmtcp.sourceforge.net]("http://dmtcp.sourceforge.net/")

DMTCP also provides the .deb packages along with the source code and can be downloaded from its Sourceforge projects page:
[https://sourceforge.net/projects/dmtcp/](https://sourceforge.net/projects/dmtcp/)

Thanks.

---

