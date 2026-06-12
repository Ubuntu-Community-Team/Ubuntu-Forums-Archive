---
title: "Top command shows huge numbers for &quot;init&quot; -- OK?"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by watchpocket on 2011-01-28
Running the "top" command shows this:

 ```
PID USER   PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
1 root     20   0 19460 1892 1208 S    0  0.0   0:00.89 init
```What does the "init" refer to, and are those numbers OK?

"Top" also shows this:
```
Tasks: 179 total, 1 running, 176 sleeping, 1 stopped,   1 zombie
```How can I determine what the zombie process is (and what its PID is) so that I can kill it?

---

### Post by NightwishFan on 2011-01-28
It looks ok to me. :)

[QUOTE="Wikipedia"]On Unix and Unix-like computer operating systems, a zombie process or defunct process is a process that has completed execution but still has an entry in the process table. This entry is still needed to allow the process that started the (now zombie) process to read its exit status. The term zombie process derives from the common definition of zombie—an undead person. In the term's colorful metaphor, the child process has died but has not yet been reaped. Also, unlike normal processes, the kill command has no effect on a zombie process.[/QUOTE]


Edit here is mine:
```
    1 root      20   0 23872 1976 1248 S    0  0.1   0:01.03 init
```

---

### Post by watchpocket on 2011-01-28
.

---

### Post by HiImTye on 2011-01-28
to find the zombie,

```
ps -el | grep Z
```the parent process will be the PPID of the zombie process
if it is 1 it is an orphan not a zombie in which case, kill the process itself by killing its PID

when killing try to use the nicer ones first.
```
kill -3 12345
kill -1 12345
kill -9 12345
```where 12345 is the PID/PPID
-9 is the meanest one, use the last

it doesn't always work either, in which case you will need to reboot to get rid of it

never kill init or bad things will happen

---

