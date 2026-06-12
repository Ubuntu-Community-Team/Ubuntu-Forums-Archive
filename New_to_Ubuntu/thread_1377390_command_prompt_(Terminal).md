---
title: "command prompt (Terminal)"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by ancianoman on 2010-01-10
Does anyone know where I could find a list of the commands and their
purposes.[http://start.ubuntu.com/9.10/](http://start.ubuntu.com/9.10/)

---

### Post by Eisenwinter on 2010-01-10
Here's a good website:

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Iowan on 2010-01-10
[Here]("https://help.ubuntu.com/9.04/basic-commands/C/") is another one.

---

### Post by dmillerct on 2010-01-10
Check the attached wallpaper. I have seen users set this as the desktop background to help out.

---

### Post by yakkeh on 2010-01-10
try the following:

echo $PATH (in a "command prompt", or a shell like i call it)

You'll see a list of directories divided by colons (:).
All the directories you see contain binaries (programs) that you can use. Note that for all "sbin" directories, you will need to use the sudo command, as they're more system administration tools than the normal user command from the "bin" directories.

examples you'll find in "bin" directories:
cat, vi, emacs, head, tail, gzip, more, less, cp, mv, rm, ... 
examples you'll find in "sbin" directories:
mkfs.ext3, fdisk, mkswap, reboot, wpa_supplicant, fschk, ...

When you list those directories, you will find a whole lot of files. Some will make sense at first glance, others probably seem very cryptic.
Every command has a built in help file, a manual. Simply type
man <command name>

Even with the manual, it can sometimes be too technical for non-geeks, so that's why there's still the internet. Search for examples of a command, look at how people write scripts, which options and values people give to a command.
Some commands can do pretty different things, depending on what options you give.
Don't be fooled in thinking every linux guru knows all these things by heart. It's just so much information, and that's why there are forums, blogs, etc where you can always take a peek ;-)

It is a good idea to go through those linux command pages previously mentioned though. It'll get you started somewhere and give you maybe a bit of a better structure than to list the binary directories on your system. 

Besides getting to know what commands are available to you, it is wise to spend a bit of time studying the file structure of a linux system.
Some directories that you will find on most distributions are:
/boot
/dev
/etc
/home
/lib
/proc
/root
/tmp
/usr/local
/usr/share
/var
and more...

Just like you know your programs have a designated place in Windows (\Program Files\), you'll have designated placeS on a linux system where you can find them. It is wise to know where your log files are (/var/log) but also your configuration files (/etc). In the virtual directory /proc you have your hardware variables at your fingers, try e.g. "cat /proc/cpuinfo"

I know it's all a bit overwhelming in the beginning, but if you spend a little time on it, you see that it all makes a lot of sense ;)

---

