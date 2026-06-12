---
title: "PATH Question"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by mike628 on 2010-07-06
Hello,
 
My bash_profile:
 
export PATH=\
/bin:\
/sbin:\
/usr/bin:\
/usr/sbin:\
/usr/bin/X11:\
/usr/local/bin:\
/mnt/ext/opt/mysql/bin
umask 022
if [ -f ~/.bashrc ]; then
source ~/.bashrc
fi
 
 
 
BUT MY echo PATH gives me this:
 
[/mnt/ext/opt/mysql/bin] # echo $PATH
/bin:/sbin:/usr/bin:/usr/sbin:/usr/bin/X11:/usr/local/sbin
[/mnt/ext/opt/mysql/bin] #
How come?
I'd like the mysql folder to be a PATH variable

---

### Post by amauk on 2010-07-06
the hash on the prompt indicates you're root

are you editing root's bash_profile, or your own user's bash_profile?

*edit*
btw, it's always a good idea to add custom stuff into .bashrc
as this will be preserved across upgrades / changes to the base bash_profile

---

### Post by mike628 on 2010-07-06
I'm new at this so...It doesnt matter if I am in ~ or / I get the same PATH and the same info in the file when I run vi, they both have the mysql folder in the PATH. I am logging in as admin...Did I mention I was new at this?

---

### Post by amauk on 2010-07-06
take out your changes out of bash_profile
and put them into .bashrc

Now, changes have been made to the config files, but your system does not (yet) know about the changes

You need to tell bash to re-read the config files, so at the terminal, do
```
source ~/.bashrc
```

---

### Post by Darkness Des on 2010-07-06
Rule 1: Don't login as root. Just be a normal user and type in your password now and again to sudo something and have root privileges just for the one command. It makes it MUCH safer.

~ and / are directories. Your bash_profile is a big ol' list of commands to execute every time you start BASH or anything that uses it. So it won't matter where you are at on your system, that will always be active. Judging by what you have up there, you know this already, but a backslash (in BASH) means to ignore the next character when executing. In your case, it's the newline character. What exactly do you want to happen here?

---

### Post by mike628 on 2010-07-06
I'm trying to get /mnt/ext/opt/mysql/bin to be part of the PATH so that I can run mysql from any directory I'm in. 
source ~/.bashrc works, but I shouldnt have to run that each time I want to use mysql.

---

### Post by amauk on 2010-07-06
> **mike628 said:**
> source ~/.bashrc works, but I shouldnt have to run that each time I want to use mysql.
No, it's only a way to get the currently running system to re-read the config files

The config files are read on each boot

---

