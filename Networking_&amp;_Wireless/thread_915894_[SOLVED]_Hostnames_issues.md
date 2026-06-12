---
title: "[SOLVED] Hostnames issues"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by Stunts on 2008-09-10
Hi everyone, I'm having the following issues:

I'm in a network, that is full of computers. I used to be able to browse around them using nautilus to access the shared folders. 
But now something is changed. I can still browse normally and view whatever is shared in each computer, but when I double click a shared folder to browse it, I am asked for a login and the Nautilus just stops (as in crashes) there. The folder shows up as mounted in my desktop, but it won't open.
The computer name is "bolseiros" and it's IP address is 10.101.134.114. This is just an example, the same happens with many others - both running XP and Ubuntu+Samba.
If I type the path like: smb://bolseiros, I get the same result.
If I type the path like: smb://10.101.134.114 - It works. I get prompted for a login and I can browse the folder like normally.

Anyone have any idea what could be causing this?
Also:
if I type in a terminal:
ping bolseiros - I get a timeout.

ping 10.101.134.114 - It pings fine.

I can ping a few computers using the hostname, but it seems somewhat random...
This only started happening a short time ago - like last week.
I've done some browsing and I can't seem to find this problem, much less a solution.

Thanks in advance!

---

### Post by wdaniels on 2008-09-10
Make sure that you have winbind installed:

```
sudo apt-get install winbind
```

And also check that "wins" is listed in the hosts line of the file /etc/nsswitch.conf (post the contents if unsure):

```
cat /etc/nsswitch.conf
```

---

### Post by Stunts on 2008-09-10
Hi and thanks for your reply!

Yes, winbind is installed, and my /etc/nsswitch.conf has wins in the hosts line:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

I had been to that route before, but maybe your more skilled eyes can find something worth changing in this file...

Thanks again.

---

### Post by Stunts on 2008-09-11
Hi!

Just wanted to let you know I have solved my problem. I found the solution on this thread:
[http://ubuntuforums.org/showthread.php?t=909020](http://ubuntuforums.org/showthread.php?t=909020)

I now can ping all computers using hostname and use samba connections with nautilus just like before.

I don't know what went wrong here, tough.

Anyway, thanks for your help!

Edit: It was the part about editing /etc/samba/smb.conf that made it work.

---

