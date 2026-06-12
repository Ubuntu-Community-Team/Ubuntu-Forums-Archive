---
title: "[SOLVED] Monitor Process/Thread Network Usage?"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by dvase on 2008-04-08
Hello,
Is there a method of determining which processes/threads are using the network interface? 

I occasionally see traffic across my network interface and I'm not sure which processes are responsible for the traffic.

---

### Post by ibutho on 2008-04-08
Something like ntop or wirehsark may help.

---

### Post by dvase on 2008-04-08
> **ibutho said:**
> Something like ntop or wirehsark may help.
Thanks for the suggestions.  ntop looks like it might do the job, unfortunately it doesn't appear to be as easy to use as top.

---

### Post by jetsam on 2008-04-08
Nethogs is in the repositories and breaks net usage down by process.  

It's very easy to use, but it isn't perfect.  It doesn't track all forms of traffic, and it hasn't  been updated for a while.  I've had it fall down before when suggesting it in threads where people were trying to track down mystery traffic.  It's worth a try, though.  It may work for your needs.  If not, there's the more complex options above.

---

### Post by dvase on 2008-04-08
> **jetsam said:**
> Nethogs is in the repositories and breaks net usage down by process. 

Thanks for suggestion, this is exactly what I am looking for.  Once I figured out that you have to give nethogs a network interface name at the command line(eg. "$ sudo nethogs eth0"), everything went great.

---

