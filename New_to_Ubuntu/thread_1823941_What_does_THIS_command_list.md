---
title: "What does THIS command list?"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by sunrex on 2011-08-12
/bin/ps -p{process id} -o pcpu,pmem

Does this list working memory and virtual memory (Combined) or does it only list working memory?

How does the above command calculate the memory consumption of a process? ;)

---

### Post by The Cog on 2011-08-13
It is described in the manual for ps. Use the command **man ps**. Use cursor keys to navigate, and **Q** to quit. Here's an extract:>        %cpu       %CPU    cpu utilization of the process in "##.#" format. Currently, it is the CPU time used divided by the time the process has been running (cputime/realtime ratio), expressed as a
                          percentage. It will not add up to 100% unless you are lucky. (alias pcpu).

       %mem       %MEM    ratio of the process's resident set size  to the physical memory on the machine, expressed as a percentage. (alias pmem).

---

