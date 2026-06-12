---
title: "gedit fails when using root"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by hmo on 2009-06-26
Hi, I have ubuntu jaunty. When I tried to use gedit as a root I get this error:

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Error getting the connection with the session: Failed to connect to socket /tmp/dbus-8P4DrQGPCy)

---

### Post by clonne4crw on 2009-06-26
From what you posted, I can't really tell what you're trying to do, and what's happening.

By using root, do you mean running as root:

$ sudo gedit
or
$su
#gedit
?

---

### Post by hmo on 2009-06-27
Hi, well when I try to do:

sudo gedit or

1-  su bash
2- gedit


I get the same problem, so I think this problem is related with the use of gedit (in root/super user)

---

### Post by mcduck on 2009-06-27
Try with "gksudo gedit".

"sudo" isn't made for running graphical applications and doesn't work correctly if you use it to launch them. You should always use "gksudo" for GUI apps.

---

### Post by t0p on 2009-06-27
> **mcduck said:**
> Try with "gksudo gedit".

"sudo" isn't made for running graphical applications and doesn't work correctly if you use it to launch them. You should always use "gksudo" for GUI apps.

It's certainly true that you should use 'gksudo' when you want to run a graphical app as root.  But I think the OP's issue lies deeper than that.  I can open gedit as root with the command 'sudo gedit'.  So the question is: why can't the OP do that?

---

### Post by hmo on 2009-06-28
Thanks gksudo works just fine for me.

---

