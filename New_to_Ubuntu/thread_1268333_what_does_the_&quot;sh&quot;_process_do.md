---
title: "what does the &quot;sh&quot; process do?"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by thomz92 on 2009-09-16
i was looking at my process in system monitor and i saw one that i never say before: "sh". what does it do? why did it suddenly appear?

---

### Post by zeroseven0183 on 2009-09-16
sh stands for **shell**, the standard command language interpreter

Quoting from [Open Group]("http://www.opengroup.org/onlinepubs/000095399/utilities/sh.html")

> The *sh* utility is a command language interpreter that shall execute commands read from a command line string, the standard input, or a specified file. The application shall ensure that the commands to be executed are expressed in the language described in [*Shell Command Language*]("http://www.opengroup.org/onlinepubs/000095399/utilities/xcu_chap02.html#tag_02").

Some kinda technical term

---

### Post by thomz92 on 2009-09-16
what does it do? its a process that shows up in my system monitor...

---

### Post by zeroseven0183 on 2009-09-16
Actually, I really don't know exactly what it does. It also shows in my System Monitor and pointing to it, it shows /bin/sh -c /usr/bin/compiz-decorator

---

### Post by j.bell730 on 2009-09-16
```
man sh
```

[QUOTE=man sh]**dash** is the standard command interpreter for the system.  The current version of dash is in the process of being changed to conform with the POSIX
     1003.2 and 1003.2a specifications for the shell.  This version has many features which make it appear similar in some respects to the Korn shell, but
     it is not a Korn shell clone (see ksh(1)).  Only features designated by POSIX, plus a few Berkeley extensions, are being incorporated into this shell.
     This man page is not intended to be a tutorial or a complete specification of the shell.[/QUOTE]

---

### Post by thomz92 on 2009-09-16
why did i never see it before? for mem usage it says n/a... almost like its doing nothing...

---

### Post by slower on 2009-09-16
Perhaps a more helpful snippet from the man page is this:
> The shell is a command that reads lines from either a file or the terminal, interprets them, and generally executes other commands.  It is the program that is running when a user logs into the system...

If you really want to know what that particular shell process is doing, you might try using `lsof` against the process ID.
```
sudo lsof -p PID
```

---

### Post by thomz92 on 2009-09-16
maybe i just never noticed it before... speaking of processes, what does "zombie mode" mean?

---

### Post by phrostbyte on 2009-09-16
> **thomz92 said:**
> maybe i just never noticed it before... speaking of processes, what does "zombie mode" mean?

A process which is done executing but is still in the process table because it's caller hasn't requested it be removed.

The UNIX process model is very different from the Windows one for example. Processes are logically arranged in a tree like structure. The root of the tree is called "init", it's the only process directly called by the kernel itself. 

All processes then are forked from init, usually including the login manager process. The login manager then forks a login shell (called "sh"). Sh can fork more processes and so forth. Other processes can call other processes. When "sh" is killed, so any processes it forked are also killed. 

Fundamentally the model is a tree, not a list.

---

