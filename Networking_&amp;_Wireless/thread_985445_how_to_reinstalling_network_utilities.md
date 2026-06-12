---
title: "how to reinstalling network utilities?"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by kakyoism on 2008-11-17
I mean the entire network-related packages.
I recently encountered two problems, which received little attention here:
[http://ubuntuforums.org/showthread.php?p=5820846#post5820846]("http://ubuntuforums.org/showthread.php?p=5820846#post5820846")
[http://ubuntuforums.org/showthread.php?t=985407]("http://ubuntuforums.org/showthread.php?t=985407")

As an attempt to fix them, I'd like to reinstall the networking packages.
Any suggestions?
Thanks.

---

### Post by cariboo on 2008-11-17
You need to reinstall:

```
network-manager-gnome
network manager

```

If you are running intrepid. 

Make sure you completely remove the installed versions first, or else you will end up using the configuration files that are giving you a problem.

Jim

---

