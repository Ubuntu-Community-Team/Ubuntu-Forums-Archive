---
title: "NFS eats up CPU usage"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by nebc on 2008-04-19
Setup:
I'm running an NFS/NIC server with 8 clients.  Each of the client computers mounts /home via nfs and uses the /etc/passwd file on the server for authentication.  The server is running Desktop Ubuntu 6.06 and the client's are running Desktop 7.10

Symptoms/Problem:
After the clients are on for an extended period of time, certain things start to slow down and the CPU usage on the computer (as reported by htop & top) increases sharply.  htop reports that the CPU is being taken up by kernel activity.  tcpdump shows that a *huge* number of getattr calls are being made.

This post: [http://ubuntuforums.org/showthread.php?t=360393](http://ubuntuforums.org/showthread.php?t=360393) reports the same problem, but it's a few months old and no one responded with any advice.

Workarounds:
I find that restarting the client machines helps, as after the client is back online the number of getattr calls is significantly reduced.  However, over time these calls just increase making this a really terrible solution.

I'm desperate for advice.  Please let me know of any solutions/whether this is a known bug/anything else that may be useful.

---

### Post by nebc on 2008-04-21
Well the problem has to do with caching.  

I found this to be a useful website: [http://docs.hp.com/en/B1031-90043/ch02s03.html](http://docs.hp.com/en/B1031-90043/ch02s03.html)

It has a lot of information about NFS mounting options and what they should be depending on how your system is set up.  tcpdump has been a great way to see what's causing all of the trouble.

---

