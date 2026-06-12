---
title: "How do you lower I/O usage"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by sunrex on 2009-03-13
I'm not a beginner.. but I am at this.

I'm going to colocate soon and I need to know how to lower/minimize I/O usage/requests.

Because I have 2GB ram I can lower the swap quite a bit but not enough.

Right now my current thoughts are this:

80GB HDD SATA 3.0Gbps - OS/Apache2/MySQL/SWAP/PHP5
120 or 160GB HDD - Any other service I want to run. Large file hosting from Apache2. Backup/storage.

I'm still reluctant to use this setup because I think SWAP + OS + other crap = bad.

Any thoughts?.

---

### Post by kidders on 2009-03-15
Hi there,

> **sunrex said:**
> I need to know how to lower/minimize I/O usage/requests.Using a binary distro like Ubuntu limits your ability to do that. For example, you can't easily build unnecessarily I/O-intensive features out of your applications, and other common approaches (like prelinking your system, rewiring or removing base system utilities, and so on) could cause instability ... which is not something you want on a colocated box! Also, being colocated means you can't very well trim down the amount of logging you do, since you'll be completely dependent on system logs to trace problems & evaluate performance.

Imo, your best option would be to forget about reducing I/O, and concentrate on trying to minimise the penalty you pay for it. For example...[LIST]
[*]If you're unhappy with your filesystem performance, you may want to trade recoverability off against I/O overhead ... for example, by using Ext2 on parts of your system. One way or another, you should re-evaluate your filesystem choices, just so you're happy they're the right ones. Those large files you're hosting, for instance, will need to be stored appropriately, to avoid I/O bottlenecks & fragmentation. Also, more obvious things like discarding file access times (where applicable) are worth a mention.
[*]It's a pity you only have 2GB of RAM. Given, say, double that, you could consider storing some of the more frequently-accessed parts of your system there, rather than on disk. Any chance of adding more?
[*]Make sure your MySQL is properly optimised for whatever you're using it for. For example, at the platform level, be sure you're discouraging disk-based caching where possible. At database level, check your indexing.
[*]Ensure the Apache/PHP-based services are cached, where possible (eg using a reverse proxy). Ideally, requests for *exactly* the same web page should trigger no database hits, and no direct filesystem access (ie only via a cache).
[*]Imo, you shouldn't try too hard to curtail swap usage on a server. Should your system ever find itself exposed to something unexpected (eg a runaway app, or an attack), lack of ready access to swap can cause instability. I would recommend allocating plenty of it (on a 2GB system, 4GB seems about reasonable, depending on what you use it for), and either (a) not storing it on an already heavily-loaded physical disk, (b) splitting your swap space up into chunks & storing them all on different disks, or (c) both of the above. Which to choose depends on details that weren't in your o/p, but the point is to try to encourage as much I/O parallelism as possible, within the bounds of what your system is capable of.
[*]If your colocation SP provides a syslog service, you could consider using it. Aside from the saving you'd make in constant (and comparatively high-overhead) writes to /var, remote logging has other advantages too.
[/LIST]

Anyhow, I hope something in there helps. Since you're fairly experienced, you may well know all of the above already, but I didn't see the harm in checking.

---

