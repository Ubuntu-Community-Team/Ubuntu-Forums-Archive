---
title: "Network ports as files"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2008-01-22
Hi!!!


   If an application is listening on some port, does that port show up as a file somewhere?? Maybe in /dev or /proc or someplace like that??

  Any help would be greatly appreciated.

Thank You.

---

### Post by lloyd_b on 2008-01-22
> **jsvidyad said:**
> Hi!!!


   If an application is listening on some port, does that port show up as a file somewhere?? Maybe in /dev or /proc or someplace like that??

  Any help would be greatly appreciated.

Thank You.

The base info can by found in "/proc/net" - "tcp" for TCP connections, and "udp" for UDP connections.  But this info is formatted to make it easy for programs to parse, not for easy readability by humans, so I'd suggest using the "netstat" command (in a terminal window).  For example "netstat -pl" will give you a list of listening sockets, and identify which program is listening on them (though you may need to "sudo netstat -pl" to get *every* listening socket on the system). 

Type "man netstat" in a terminal window for a full list of its many options.

Note: If you don't have "netstat" on your machine, install the "net-tools" package - I can't remember if it's installed by default or not.

Lloyd B.

---

