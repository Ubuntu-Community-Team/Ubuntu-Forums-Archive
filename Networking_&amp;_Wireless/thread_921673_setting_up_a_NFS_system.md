---
title: "setting up a NFS system"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by perrti-y02 on 2008-09-16
Hello,
I am interested in setting up a NFS system between a Shuttle XPc and an old Time machine. What I am wondering is how i go about this; I don't think i need a really simple walkthrough but what things do i actually need to do?

Also, if I am connecting 2 machines and only 2 machines do i actually need a hub or switch or whatever?(this is going to be a wired connection but a wireless network between Shuttle and this current machine (something custom built running Windoze{the Virus!!!!})will soon exist to give the Shuttle interweb conection)

Many Thanks

---

### Post by nixscripter on 2008-09-17
This should be a start on the NFS part:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

If you are connecting two machines like this:

```

+-----------+         +-----------+            +-----------+
|           |<------->|           |            |           |
| Machine A |         | Machine B |            | Internet  |
|           |         |           |<---------->|           |
+-----------+         +-----------+            +-----------+

```

Then you can do it with an ethernet crossover (A to B) and a regular ethernet cable (B to C) if machine B has two cards (and the routing software to handle them).

Hope this helps.

---

