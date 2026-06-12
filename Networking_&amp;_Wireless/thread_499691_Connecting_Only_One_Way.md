---
title: "Connecting Only One Way"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by sparkshaha on 2007-07-12
Hello, my Ubuntu PC can connect fine to my Windows XP laptop via wired Lynksys switch.  However, even though I can see the Ubuntu PC by name from the Windows XP laptop, I enter my ID and PASSWORD to connect but I am continuously prompted for my ID and PASSWORD after that.  I've confirmed I am typing in my id and password in correctly.  Why won't it authenticate and map to the Ubuntu PC hard drive?

Note that my Windows XP laptop is named "sparky1" and my Ubuntu PC is named "robdesktop"

My username on both is "rob"

I've also made sure I created a share on the Ubuntu PC as samba-enabled, not unix.

Please help.  Thank you.

---

### Post by jhofmann on 2007-07-12
I'm going to take a shot at this, even though my situation is somewhat different.  I have had this situation between two linux boxes several times.  After some frustration, I discovered that the ssh server must be running on the host you are trying to log in to.  

In a standard install, only the ssh client software gets installed.  As root, try

# aptitude install openssh-server

from a command line.  Possibly Windows is trying ssh on a box which has no server, and responding correctly to a box which does have the client software.

I hope this helps.

Jim

---

