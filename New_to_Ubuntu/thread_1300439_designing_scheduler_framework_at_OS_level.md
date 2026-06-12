---
title: "designing scheduler framework at OS level"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by atulchavan on 2009-10-25
respected sir,
i am student of computer science, i am trying to design new scheduler for scheduling the task on multi-core platform (like dual-core, quad-core,etc..).Some of the applications are not making best usage of multi-core architecture i.e., application using only one core and other core remains idle. so i have decided to design new thread scheduler for OS.
this work is completely at the OS level, can any one guide me how should i solve this problem.
i have planned to use linux (ubuntu) as a platform.

waiting for reply.

---

### Post by kushal.kumaran on 2009-10-31
Hey Atul,

You'll find things like process scheduling are independent of what distribution you are using.  In an ubuntu system, you are using the linux kernel.  Task scheduling is the kernel's job.  You'll first need to become familiar with what capabilities linux already has.  [http://kernelnewbies.org/](http://kernelnewbies.org/) is a site meant for people starting out understanding the linux kernel.  I should be a good starting point for you as well.  lwn.net often has articles about new schedulers going into the linux kernel.

---

