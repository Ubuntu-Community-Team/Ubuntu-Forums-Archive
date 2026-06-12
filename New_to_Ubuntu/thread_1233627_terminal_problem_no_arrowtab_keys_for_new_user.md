---
title: "terminal problem: no arrow/tab keys for new user"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by minsf on 2009-08-06
i created a new user with 
> sudo useradd -d /home/new -m new
and set a passwd for him. 
PROBLEM: when i log as user "new", my terminal has neither tab-completion nor arrow-key history. 
how do i fix this?

---

### Post by 123456789123456789123456 on 2009-08-07
There are other commands that are needed on command line to create users than just useradd command, and passwd commands.
that may be the problem there.
suggest that you log out of new, go to your account, and check new's user settings through GUI, change, add anything that is needed, see if that fixes the problem, if not, remove user, and re-add, suggest using the GUI, it is easier than using command prompt
if you would still like using command prompt, you may want to study up on every user command used in the creation of accounts.  Including setting permissions.

---

### Post by minsf on 2009-08-07
SOLVED but in a different (and better?) way.
my first guess was that there is a problem with $TERM, but both old and new user had it set to "xterm". 
so i dug deeper and actually compared all the other environmental variables for the old and new users.
it turned out that the WINDOWPATH was 7 instead of 7:7, DISPLAY was 0 instead of 0:0, SHELL was /bin/sh instead of /bin/bash, and the new user did not have the variables HISTCONTROL, SHLVL, LESSCLOSE, LESSOPEN, COLORTERM, DBUS_something and LS_COLOR_something. plus there was some difference in the XAuthority variable.
Fortunately, just changing the shell variable to bash automatically fixed the other variables and created the missing ones!
hence, _**the solution is**_ (in the new user's terminal):
```
SHELL=/bin/bash
env $SHELL
```
[COLOR="Red"]finally, if someone can explain the meaning of some of these env variables, i'd be really glad :)[/COLOR]

---

### Post by xinfin on 2011-03-07
Thanx man, that worked for me like a charm :)

---

### Post by chiragjain on 2012-03-21
Thanks a lot. It only works for that session. How to set it permanently

---

### Post by codemaniac on 2012-03-21
Put the below line in your ~/.bashrc file to amke the change permanently .
```
export SHELL=/bin/bash
```

if ~/.bashrc does not exist , you need to create one .

---

