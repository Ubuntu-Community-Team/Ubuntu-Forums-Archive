---
title: "Which one: /etc/network/options or /etc/sysctl.conf"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by ralic on 2007-09-17
I'm setting up a dapper box as a gateway and I know that in order to do packet forwarding, I need a '**1**' in **/proc/sys/net/ipv4/ip_forward** and it needs to be permanent.

Being new to ubuntu, but old to slackware, I was wondering how best to achieve this in ubuntu land. Searching through the threads in this forum, I stumbled across a reference to the **/etc/network/options** file and that it should contain **ip_forward=yes** to achieve the desired result.

So I set up the file with that option, but after rebooting, /proc/sys/net/ipv4/ip_forward was still '0'.

A quick google later and I came across an article in a mailing list that seemed to indicate /etc/network/options is deprecated and **/etc/sysctl.conf** should be used.

Fine, I used that file with its ip_forward option and it worked. However at the very top of /etc/sysctl.conf is the following comment:
```
# Be warned that /etc/init.d/procps is executed to set the following
# variables.  However, after that, /etc/init.d/networking sets some
# network options with builtin values.  These values may be overridden
# using /etc/network/options.
```

And if I read this right, this implies that /etc/network/options may override builtins in /etc/init.d/networking which in turn can override /etc/sysctl.conf and as such, it probably isn't deprecated.

Could anyone advise if indeed /etc/network/options is deprecated?
Or if not, any ideas why it wouldn't work for me?

Distro is ubuntu dapper server 6.06.1 with all updates installed.
Kernel is 2.6.15-29-server

```
:~$ ls -l /etc/network/options
-rw-r--r-- 1 root root 15 2007-09-17 14:48 /etc/network/options

:~$ cat /etc/network/options
ip_forward=yes
```

TIA for your patience.

---

### Post by robert_pectol on 2007-09-17
Ignore that message at the top of /etc/sysctl.conf on Dapper.  I suspect the reason that note is still there is that it was an oversight.  Later releases of Ubuntu no longer have the note.  /etc/sysctl.conf is the correct place to enable IP forwarding.

---

### Post by ralic on 2007-09-17
Thanks Robert

For anyone else that might find this post in future.
**/etc/network/options** really is **deprecated**.

Save yourself some effort and use **/etc/sysctl.conf**

---

### Post by steve.horsley on 2007-10-01
I would also add that (in Feisty - don't know about the others), /etc/sysctl.conf contains this note:
> # Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

but uncommenting the line doesn't work. I guess the other similar lines in the file are equally garbage.

The line you need to add is this (the spaces round the = are optional):
> net.ipv4.ip_forward = 1

---

