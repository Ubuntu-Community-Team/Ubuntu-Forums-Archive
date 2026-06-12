---
title: "How to set an argument with which a command will always be run"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by beeny on 2010-07-26
Hi guys. I was wondering is there any way in which to set a particular argument for a command, so that every time some other application runs that command, the command gets started with that argument. (apart from the arguments that the calling application might generate in order to run the other one)

What I'm trying to do is have qemu always start like "qemu -nographic" regardless of what calls qemu(In my case a dynagen.py script, which in turn calls a qemuwrapper.py script)

Now, I've already tried modifying the code for these two files, and I actually managed getting things to work under ubuntu, but under Debian the changes I've made don't seem to make a difference.

So, I'm trying to figure out some other way of doing things, because my Python programming is as bad as it is. 

Thank you very much!

-Todor

---

### Post by P4man on 2010-07-26
sounds like a bad solution; but why not use an alias?

---

### Post by beeny on 2010-07-26
Actually, changing the qemu startup path in both files involved WAS working on debian as well, but I had forgotten to save one of them after changing the path, which made it seem as if stuff wasn't working at the time I opened the thread.

If you have time, could you please elaborate a bit more on what do you mean by "bad solution" ?
I just googled the alias command and I see that it would have done the trick as well. Perhaps you mean that this will pose a restriction on all other processes which might call this one because of the aliased stuff?

---

### Post by beeny on 2010-07-26
Dear admins, if you're out there, please remove my ridiculous thread. Thank you.

---

