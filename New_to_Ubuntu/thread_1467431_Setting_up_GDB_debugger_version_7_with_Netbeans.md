---
title: "Setting up GDB debugger version 7 with Netbeans"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Remagen on 2010-04-30
This has really annoyed me.

Netbeans, even though I installed the C/C++ plugin correctly ignores breakpoints when I set them and run in 'debug' mode.

If I set the output terminal type to output terminal (from default or external), as some forums suggest, I get the following output:

"warning: GDB: Failed to set controlling terminal: Operation not permitted\n

Under project properties->Build->Make->Build Command I have:
$(MAKE) -f Makefile

I'm not sure if it's compiling with the necessary -g debugging symbols switch.
I've also tried running netbeans as root, as implicated by the warning message, but that didn't work.

So, how do you set up gdb for netbeans?

---

### Post by v.cecchetto on 2010-05-04
I don't remember exactly which one is the solution (try):

1. Select the project > Click Dx > Properties > Profile > Show profiling indicators during run (uncheck)

2. Select the project > Click Dx > Properties > Run > Console Type > External Terminal

and read

[http://forums.netbeans.org/topic15797.html](http://forums.netbeans.org/topic15797.html)

[https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/469005](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/469005)

---

