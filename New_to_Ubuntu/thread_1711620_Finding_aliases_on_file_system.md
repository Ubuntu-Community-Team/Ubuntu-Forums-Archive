---
title: "Finding aliases on file system"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by fejimush on 2011-03-21
Hello,

A program installed from a website has automatically aliased a few basic tools, such as grep, to a nonstandard /bin directory.

Earlier post:
[http://ubuntuforums.org/showthread.php?t=1711486]("http://ubuntuforums.org/showthread.php?t=1711486")
I suspect there is a way to pipe the find, type, and grep commands to scour my file-system for these modified aliases.  

Or better a method to set all aliases back to the Ubuntu 10.04 default.

I am a little out of my element here.

Thanks,
graham

---

### Post by CharlesA on 2011-03-21
What is the output of this:

```
alias
```
```
echo $PATH
```

That should tell you where the file is.

---

### Post by asmoore82 on 2011-03-21
I'm guessing he means "linked" or "symlinked" instead of "aliased" &#8230;

Here's the world's cheapest symlink finder along with my results:
```
**$ ls -l /bin/ | grep '\->'**
lrwxrwxrwx 1 root root       6 2010-10-11 20:31 bzcmp -> bzdiff
lrwxrwxrwx 1 root root       6 2010-10-11 20:31 bzegrep -> bzgrep
lrwxrwxrwx 1 root root       6 2010-10-11 20:31 bzfgrep -> bzgrep
lrwxrwxrwx 1 root root       6 2010-10-11 20:31 bzless -> bzmore
lrwxrwxrwx 1 root root       8 2010-08-06 12:48 lessfile -> lesspipe
lrwxrwxrwx 1 root root      20 2010-08-06 12:48 mt -> /etc/alternatives/mt
lrwxrwxrwx 1 root root      20 2010-08-06 12:48 nc -> /etc/alternatives/nc
lrwxrwxrwx 1 root root      24 2010-08-06 12:48 netcat -> /etc/alternatives/netcat
lrwxrwxrwx 1 root root       6 2010-08-06 12:48 open -> openvt
lrwxrwxrwx 1 root root      14 2010-08-06 12:48 pidof -> /sbin/killall5
lrwxrwxrwx 1 root root       4 2010-08-06 12:48 rbash -> bash
lrwxrwxrwx 1 root root       4 2010-08-06 12:48 rnano -> nano
lrwxrwxrwx 1 root root       4 2010-08-06 12:48 sh -> dash
lrwxrwxrwx 1 root root       4 2010-08-06 12:48 sh.distrib -> bash
lrwxrwxrwx 1 root root       7 2010-08-06 12:48 static-sh -> busybox
```

---

### Post by SeijiSensei on 2011-03-21
Typing just "alias" at the command prompt shows a list of all the bash aliases in use.  To remove an alias use "unalias aliasname".

Usually aliases are defined in $HOME/.bashrc.  Perhaps that application stuck the annoying aliases in there.  If you want to reset your .bashrc to the default, just copy /etc/skel/.bashrc to your home directory.

---

