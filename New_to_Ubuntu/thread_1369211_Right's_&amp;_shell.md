---
title: "Right's &amp; shell"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by 0863947 on 2009-12-31
Welcome,
1- how can do i add anew shell?
2- how can do i change the shell?
3- how can do i control or change the right's of user's?
 
Thank you very much;

---

### Post by minsf on 2009-12-31
you probably want to look at your SHELL environment variable, either by 
```
echo $SHELL
```
or by viewing all the variables:
```
env
```
on a default ubuntu installation, /bin/sh is a simlink to /bin/dash. you can change it to simlink to /bin/bash, but i would not recommend it, since it will slow down you boot time.

in most situations, when you open a terminal, your SHELL variable is set to bash. but if you added a user via useradd, rather than debian's adduser, than you  may need to change to bash with:
```
export SHELL=/bin/bash
```
and you can put this line in the new user's .bashrc file so it will happen "automatically" whenever she logs in.

1) not sure what you meant by adding a new shell. do you want to compile it from scratch? if you just want to open another tab in the terminal with a different shell, try ctrl+shift+t and then do the "export SHELL=***" as suggested above.

2) as suggested above, to change your shell to, say, bash, try:
```
export SHELL=/bin/bash
```

3) you should look in the file /etc/sudoers. try
```
man sudoers
```

---

### Post by durand on 2009-12-31
What shell do you want to change to? There are usually installation instructions.

---

