---
title: "I want to learn Bash"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by luckydeveloper on 2010-01-24
I was doing this some months back but didn't quite stick to it. I had to format my system recently and I lost all my ebooks.

I am thinking of doing all of my jobs in terminal , those which I am doing now with Gnome GUI.  I know basic navigation commands. But I dont know the advanced commands set in bash like changing permissions for files, user permissions, configs, moving files around in the file system, etc

I want to learn **"bash"** completely. For that I am looking for a solid **ubuntu/debian** book/resource for reference. Please point me towards a right book or resource for that.

---

### Post by corncob on 2010-01-24
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Mornedhel on 2010-01-24
The man page will give you all the gory details:

```
man bash
```

However, it is not a very good reference if you're trying to learn to write bash scripts. For that, you might want to install the Advanced Bash-Scripting guide, which is in the abs-guide package:

```
sudo apt-get install abs-guide
firefox /usr/share/doc/abs-guide/html/index.html
```

Finally, to get information on how to do various tasks, man and apropos are your friends. Let's say you want to know about permissions:

```
$ apropos permissions
access (2)           - check real user's permissions for a file
chmod (2)            - change permissions of a file
dh_fixperms (1)      - fix permissions of files in package build directories
eaccess (3)          - check effective user's permissions for a file
euidaccess (3)       - check effective user's permissions for a file
faccessat (2)        - check user's permissions of a file relative to a directory file descriptor
faked (1)            - daemon that remembers fake ownership/permissions of files manipulated by fakeroot processes.
faked-sysv (1)       - daemon that remembers fake ownership/permissions of files manipulated by fakeroot processes.
faked-tcp (1)        - daemon that remembers fake ownership/permissions of files manipulated by fakeroot processes.
fchmod (2)           - change permissions of a file
fchmodat (2)         - change permissions of a file relative to a directory file descriptor
ioperm (2)           - set port input/output permissions
WWW::RobotRules (3pm) - database of robots.txt-derived permissions
XF86VidModeGetPermissions (3) - Extension library for the XFree86-VidMode X extension
```

"Hey, chmod looks interesting."

```
man chmod
```

---

### Post by cprofitt on 2010-01-24
I happen to like these two books if you are inclined to own paper books.


[LIST]
[*][Linux Command Line and Shell Scripting Bible]("http://www.amazon.com/Linux-Command-Shell-Scripting-Bible/dp/047025128X/ref=pd_ys_iyr34")
[*][Linux in a Nutshell]("http://www.amazon.com/Linux-Nutshell-Ellen-Siever/dp/0596154488/ref=sr_1_1?ie=UTF8&s=books&qid=1264349367&sr=8-1")
[/LIST]
Both of these books are good.

---

