---
title: "Network Settings does not accept DNS servers"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by Dennis Fisher on 2008-02-27
I am running Ubuntu 7.10 with VMWare on an Apple Mac Pro.  I have set up a static IP address successfully and I can ping / telnet / ftp successfully within my local network.  If I use DNS tab on the Network Settings GUI to add a DNS server, I can also communicate to the outside world.  After I enter the DNS server, the file /etc/resolv.conf shows the desired changes.

The problem occurs when I reboot: resolv.conf is overwritten and the DNS servers are lost.  I can fix the problem either by editing resolv.conf or re-entering the values in the GUI.  How do I prevent resolv.conf from losing these settings?

If necessary, I assume that I can disable DHCP since I am not using it.  If this is the solution, please advise how to do so.

If possible, I would appreciate copies of any replies to my personal email address - [email]fisher@plessthan.com[/email].  Thanks in advance.

Dennis

---

### Post by Mr. C. on 2008-02-27
How have you setup the static IP ?

---

### Post by Iowan on 2008-02-27
There IS a way to disable DHCP client - I remember a thread... but don't remember where it is.

---

