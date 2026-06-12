---
title: "pin virtualbox to one core?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by chilimac02 on 2008-12-06
I am running ubuntu intrepid on my dual core laptop. I want to pin sun virtualbox to one core. I'm running xp through virtualbox and I'd rather just use the one core.

Any command that I can use?

---

### Post by Duck2006 on 2008-12-06
I may be wrong but, i don't think it can be set to one core on a dual core system.

---

### Post by chilimac02 on 2008-12-06
dang

---

### Post by scorp123 on 2008-12-06
> **chilimac02 said:**
> I am running ubuntu intrepid on my dual core laptop. I want to pin sun virtualbox to one core. This is not needed. :D

The Linux kernel will automagically decide which core does what depending on the workload at hand. You really don't have to bother about that :D

Make sure you don't give your virtual machines more than one CPU. Those "CPU's" are simulated anyway. Giving a virtual machine more than one virtual CPU is only good if you are testing software (e.g. how it would behave in 1 CPU scenarios vs. multiple CPU scenarios) but other than that only adds overhead and in fact slows the performance down.

As for "CPU affinity" (because that's the term for what you asked: nail a specific task to a specific CPU) and if you really really insist on doing that, please read this:
[http://www-128.ibm.com/developerworks/linux/library/l-affinity.html?ca=dgr-lnxw09Affinity](http://www-128.ibm.com/developerworks/linux/library/l-affinity.html?ca=dgr-lnxw09Affinity)
[http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html](http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html)
[http://www.linuxjournal.com/article/6799](http://www.linuxjournal.com/article/6799)

... but again: This is not needed!!  The Linux kernel will handle this automatically and you should not have to mess with this.

---

### Post by dasajed on 2008-12-21
Actually, I'm not entirely sure what its benefits are, but when I was installing VirtualBox, [one of the pages]("https://help.ubuntu.com/community/VirtualBox") I encountered said how to do it.

> 
If you have a multi-core CPU and experience high CPU usage even when the guest OS is almost no using CPU, you can force Virtual Box to execute in just one of your cores by launching it through taskset.
```

sudo apt-get install util-linux
taskset -c 1 virtualbox

```


---

