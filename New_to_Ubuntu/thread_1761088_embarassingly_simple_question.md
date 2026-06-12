---
title: "embarassingly simple question"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by asfoiudf on 2011-05-17
i recently installed 2 Linux kernels: 1 to serve as my base, 1 to hack. for the one that i'm hacking, i have all the source, did the config, compilation, installation, etc, etc. i have both kernels fully running.

now i want to do the world's simplest kernel hack, so i can recompile & prove to myself that i've been able to successfully compile my own edits. i don't want to do anything complex, like hacking the file system, i literally just want to do something really, really simple to ensure the re-compile worked.

i tried editing some of the error msgs in net/9p/error.c (such as "No such file or directory"), then recompiled & reinstalled the new code, then tried causing the errors, but i didn't see my re-written error msgs, so i think i may have edited the wrong file.

anyway, can someone pls tell me the world's simplest hack that i can make, so i can then recompile to verify i'm actually correctly hacking the kernel! pls be specific re: which kernel file i should edit, & which function in there to edit, since there's so many!

(to be clear, i don't need instructions on re-compiling the kernel, i think (i hope!) i'm doing that correctly. i just need some basic newbie hack that i can make to test my ability to correctly recompile the kernel). thanks in advance!

---

### Post by gsmanners on 2011-05-17
Sounds like a question for [http://kernelnewbies.org/](http://kernelnewbies.org/) , but I personally think you'd be better off trying to get a generic "Hello World" into the syslog. Don't ask me how to do that, though.

---

