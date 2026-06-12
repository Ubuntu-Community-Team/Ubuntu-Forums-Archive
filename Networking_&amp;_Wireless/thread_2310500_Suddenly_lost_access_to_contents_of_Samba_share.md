---
title: "Suddenly lost access to contents of Samba share"
date: 2016-01-19
forum: Networking &amp; Wireless
---

### Post by pderocco on 2016-01-19
I'm using Ubuntu 14.04 LTS 64-bit on a wired network, with several Win7Pro boxes and a Mac.

I have a file share set up on the Ubuntu machine that has worked fine since I got the machine a few years ago (using an earlier Ubuntu, obviously). I was accessing the share earlier today from two of the Win7 machines with no problems. I went over to the Ubuntu machine and saw that a lot of updates were available, so I installed them, after which it restarted. Now, all of a sudden, I've lost access to the contents of the share.

Let me be clear: I can open the machine in Windows using the [\\servername]("file://\\servername") syntax, and it lists my share. But I can also open the share, and it shows the first level contents of that share, subdirectories and data files. But I can no longer access those files: I get an error like "Windows cannot access \\servername\sharename\dirname". I get this on all three of my Windows machines, and a similar error on my Mac. So I believe this is a Linux credentials issue, not a Samba issue. I use the same username and password on all my machines.

I've rebooted everything, even my router (just waving a dead chicken over it, I know). How do I solve this? Or at least diagnose it further?

---

### Post by pderocco on 2016-01-31
Since I was sharing the root, someone on the Samba list suggested it is probably this bug:

[https://bugzilla.samba.org/show_bug.cgi?id=11647](https://bugzilla.samba.org/show_bug.cgi?id=11647)

Is there somewhere special to report this to Ubuntu? Or should I simply assume it will naturally get incorporated reasonably promptly?

---

### Post by bab1 on 2016-01-31
> **pderocco said:**
> Since I was sharing the root, someone on the Samba list suggested it is probably this bug:

[https://bugzilla.samba.org/show_bug.cgi?id=11647](https://bugzilla.samba.org/show_bug.cgi?id=11647)

Is there somewhere special to report this to Ubuntu? Or should I simply assume it will naturally get incorporated reasonably promptly?
This has already has been reported to Samba.org.  They maintain all of Samba.  Ubuntu is just uses the downstream package (from Debian).

---

