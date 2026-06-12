---
title: "Ubuntu website access"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by SteelCore on 2009-02-21
In the past few days I've noticed that accessing the Ubuntu website takes much longer than usual.  Logging on to the forums and brainstorm is exceptionally difficult and downloading the updates is very slow. Is there anybody else experiencing this?

---

### Post by taurus on 2009-02-21
Switch to another server if you've experienced slowness in updating your machine.

System -> Administration -> Software Sources

---

### Post by mlissner on 2009-02-21
Any easy way to do this via command line, like on a server? I know I can edit /etc/apt/sources.list, but what do I edit it to?

---

### Post by kellemes on 2009-02-21
> **mlissner said:**
> Any easy way to do this via command line, like on a server? I know I can edit /etc/apt/sources.list, but what do I edit it to?

All info about changing mirrors using the CLI.
[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

You only need to replace the URL with one of the URL's from the following mirrorlists..

[https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive]("https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive")
[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

Just to be on the safe side, first make a backup of your sources.list
```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

---

### Post by mlissner on 2009-02-21
Nice, that really helps, but can you use these for the security.ubuntu.com repos? I get the feeling you probably cannot. For some reason the feisty ones have been bouncing for me since yesterday.

---

### Post by mlissner on 2009-02-21
Huh. Scratch that. Apparently they are the same according to this thread: [http://ubuntuforums.org/showthread.php?t=127549](http://ubuntuforums.org/showthread.php?t=127549)

---

