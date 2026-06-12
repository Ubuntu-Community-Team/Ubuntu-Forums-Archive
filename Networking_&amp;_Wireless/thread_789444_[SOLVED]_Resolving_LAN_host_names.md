---
title: "[SOLVED] Resolving LAN host names"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by FooSoft on 2008-05-10
Hi guys, I'm running into a bit of a problem with Xubuntu 8.04. I can't seem to be able to resolve the host names for my other machines on the network. I have no problem resolving external hosts (like ubuntuforums.org), or pinging the local machines directly by IP address, but resolving by name doesn't work:

foosoft@tsundere:~$ ping wintermute
ping: unknown host wintermute
foosoft@tsundere:~$ ping wintermute.local
ping: unknown host wintermute.local

Any ideas what could be up? I know it's not a hardware problem because this works when I'm in Windows.

---

### Post by Iowan on 2008-05-11
What's in your **/etc/resolv.conf** file?

---

### Post by FooSoft on 2008-05-11
Here we go:

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5213
#
### END INFO

search hsd1.wa.comcast.net.


nameserver 192.168.0.1

192.168.0.1 being the IP of my router, Comcast being my ISP of course

---

### Post by Iowan on 2008-05-11
The **.local** sparked a memory - see if [this ]("http://ubuntuforums.org/showthread.php?t=773851")link helps - very first item looks like your problem.

---

### Post by FooSoft on 2008-05-11
That's not it unfortunately, nothing apparent wrong with my hosts file.

---

### Post by FooSoft on 2008-05-11
I found a solution that allows me to ping the Windows comps! I installed the packages samba, smbfs, smbclient, winbind and edited /etc/nsswitch.conf to include "wins" under the "hosts:" line. I can resolve all my LAN comps now :)

---

### Post by Iowan on 2008-05-12
Glad you found it... I keep forgetting about installing **smbfs**. I sometimes remember the **winbind** package, but then forget about editing **/etc/nsswitch.conf**.
 A little knowledge is, indeed, a dangerous thing.

---

