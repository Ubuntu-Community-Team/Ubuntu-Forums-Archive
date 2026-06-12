---
title: "help with commands?"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by wizardraghnall on 2010-12-16
Greetings,

I am new to Linux and Ubuntu... I am trying to learn the commands and how to do basic things in the Terminal.  Can anyone tell me what the -l command is for?  Example below:

user@myname-PC:~#  su -l

What does the -l command mean?  I can't find anything online about this.  Any help is very appreciated.:KS

---

### Post by Wtower on 2010-12-16
-l is not a command but rather an option for a command. For that particular command (su), -l does the following (from man page):

> 
-l
--login

     Make the shell a login shell.  This means the following.  Unset all
     environment variables except `TERM', `HOME', and `SHELL' (which
     are set as described above), and `USER' and `LOGNAME' (which are
     set, even for the super-user, as described above), and set `PATH'
     to a compiled-in default value.  Change to USER's home directory.
     Prepend `-' to the shell's name, intended to make it read its
     login startup file(s).

What exactly are you trying to do. Check this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards

---

### Post by Verbeck on 2010-12-16
-l is an option for a command
for more info type *man* *commandname* in a terminal window
in this case
*man su*

---

### Post by Sneil on 2010-12-16
As you can see in the manpages, there are a lot of different uses of the su (sudo) command. Don't go experimenting with all of them. Su is a very powerfull command if you don't know what to do. It can mess up the system.

---

### Post by Dutch70 on 2010-12-16
I've found this link to be very helpful...

[_*[COLOR="Red"]Learn Linux Commands[/COLOR]*_]("http://www.linuxcommand.org/index.php")

---

### Post by alphacrucis2 on 2010-12-16
> **Sneil said:**
> As you can see in the manpages, there are a lot of different uses of the su (sudo) command. Don't go experimenting with all of them. Su is a very powerfull command if you don't know what to do. It can mess up the system.


su and sudo are different. su allows you to change your session login to any different user. sudo is for executing a single command as a different user. root is the default different user in each case.

---

### Post by wizardraghnall on 2010-12-16
Thanks everyone... can anyone tell me what else -l can do?  I've seen it in other command lines...  Thanks and I will check out the links that people posted. :)

---

### Post by Wtower on 2010-12-16
It depends on the command before the option.

---

