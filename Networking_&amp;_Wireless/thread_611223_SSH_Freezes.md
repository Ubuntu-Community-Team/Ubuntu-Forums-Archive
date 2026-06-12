---
title: "SSH Freezes"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by 40esp on 2007-11-12
Whenever I login to my server 7.10 via SSH from a local machine, it is really laggy, and if I run a huge job through ssh it freezed the console.

Is this a misconfig?

if so how do i fix it?

---

### Post by R00t3rMan on 2007-11-12
SSH is laggy?  Are you SSHing from another Linux box?  Have you tried running the same routines locally and monitoring your system?

---

### Post by 40esp on 2007-11-13
> **R00t3rMan said:**
> SSH is laggy?  Are you SSHing from another Linux box?  Have you tried running the same routines locally and monitoring your system?

SSH is lagging and so is the whole friggen server. I migrated from CentOS to Ubuntu 7.10 Server
CentOS - No Problems
Ubuntu 7.10 - Slow Response


Its not just SSH the connection closes unexpectedly.

I've even disabled IPV6 but that didnt help.

---

### Post by R00t3rMan on 2007-11-13
You're still not saying much other than "my Toyota was fast but my new Nissan is slow."

The recommendation is to use your system monitor, determine what the resource hog is, and disable it.  

Did you load the server version or are you trying to use the workstation version as a server?

How much RAM do you have?  Is your swap space sized correctly?  How much CPU utilization are you seeing?

---

### Post by jspin72 on 2007-12-19
Hello,

I'm having a similar issue so I'll try and provide more info than "my Toyota was fast but my new Nissan is slow."

I'm on 7.10 and using gnome-terminal with OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007

I can ssh to other machines on the local network and the session never freezes.  It ONLY happens when going thru a router/switch and over the internet.  I'm having the same issue both at home and at work (2 different boxes both running 7.10) so that _should_ rule out an issue with my network setup.  It happens in both single and multiple tabbed gnome-terminals.  It nearly always happens during the output of some text dumping type command, for example while less'ing a text file or ls -l or query results when logged into the mysql prompt (yes, small query responses also).  It almost NEVER happens while typing and sometimes happens after being idle.

In the menu bar, I've tried Terminal->Reset but it doesn't help.  I end up killing that specific ssh process and re-logging in.

let me know if you need any other info

---

