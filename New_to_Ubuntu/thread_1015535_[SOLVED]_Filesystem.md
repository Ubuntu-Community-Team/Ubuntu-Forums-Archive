---
title: "[SOLVED] Filesystem?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Fireblazer on 2008-12-18
Hey,
I installed Ubuntu the other day because Windows made me extremely mad.
I was wondering if someone could explain to me the file system.
I got that "/home" is like Docs and Settings on windows but what about "/usr" and "/etc" and all the other folders.

Please 'spalin soon,
Fireblazer

---

### Post by Bölvaður on 2008-12-18
[Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

It is used in most modern OSes. When I think of it... some version of it is used in all except one.

*added*
/home is used for user files, which include personal data and config files from programs you use, and even whole programs that that user uses.
You can see all the hidden config and data files from all sort of programs you are using by pressing ctrl+H in the file manager (Nautilus).

---

### Post by anim on 2008-12-18
```
The Linux system contains thousand of files located within many directories. All directories are organized in a tree-structure like manner.

    * The 'trunk' of the tree is the root directory.
    * The root directory is simply identified as a "/".
    * All other directories 'branch' off from the trunk.

The following lists the most common directories and their intended contents.

    * / - root directory
    * /home - where directories are contained for each user, example:
    * /usr - pronounced 'user' and contains Linux commands and utilities
          o /bin - binary executable programs
          o /lib - program libraries, similar to Windows 'dll' files
          o /sbin - more executable programs and Linux utilities for administrative purposes
          o /doc - documentation
          o /src - source code to programs
    * /tmp - temporary work files
    * /etc - configuration files
          o /rc.d - scripts used during boot and shutdown process
          o /sysconfig - default configuration files
          o /sysconfig/network-scripts - network scripts
          o /sysconfig/daemons - special programs that run in background, such as print spooling
    * /bin - binary executable programs that all users need
    * /dev - device files that control drives, terminals and any equipment attached to the server
    * /var - user specific files
          o /log - log files containing system usage and errors
          o /spool - where spooled files are stored during print spooling process
          o /mail - where Email files are stored until retrieved by client Email program
    * /proc - system files
    * /root - root's home directory
    * /opt - other options
    * /sbin - more executable programs and utilities
```

Source: [http://www.ahinc.com/linux101/structure.htm](http://www.ahinc.com/linux101/structure.htm)

---

### Post by anim on 2008-12-18
> **Bölvaður said:**
> [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

It is used in most modern OSes. When I think of it... some version of it is used in all except one.

That is because most "Modern OSes" (linux, mac OS, and BSD) are built upon UNIX and use most of UNIX's conventions.

Windows was written as a new and unique (well, supposedly) way of doing things, which is why its way of managing file systems are different. I'm no windows apologist but thats sorta an apples to oranges comparison.

---

