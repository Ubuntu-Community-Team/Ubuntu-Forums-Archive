---
title: "How to erase terminal memory"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-05-09
In the terminal, pressing the up arrow will access all the previous commands.  How do I erase these for security reasons?

Thanks in advance.

---

### Post by Pjotrovitz on 2009-05-09
Delete the .bash_history in your home directory.

---

### Post by freak42 on 2009-05-09
fyi: if you really want security you might better make sure that no one else can access your console, ever, instead of erasing your console history.

---

### Post by kerry_s on 2009-05-09
the command is> **history -c**
you should alias it, i have it set to "ch".

```
alias !='sudo'
alias u='! apt-get update;! apt-get upgrade'
alias s='apt-cache search'
alias i='! apt-get install'
alias r='! apt-get remove --purge'
alias c='! apt-get clean'
alias ch='history -c;clear'
alias q='exit'

```

---

### Post by jarekadam on 2009-05-09
export HISTSIZE=0

---

### Post by cjv8888 on 2009-05-09
It is just that I typed the admin password into there as a command by mistake and it is stuck there in the memory.

So if I delete the .bash history will subsequent command still be recorded? which is ok as long as that password one has been deleted.

I do use the up arrow quite often to access previous commands so I don't have to retype it.  Just laziness! :(

---

### Post by cjv8888 on 2009-05-09
> **kerry_s said:**
> the command is> **history -c**
you should alias it, i have it set to "ch".

```
alias !='sudo'
alias u='! apt-get update;! apt-get upgrade'
alias s='apt-cache search'
alias i='! apt-get install'
alias r='! apt-get remove --purge'
alias c='! apt-get clean'
alias ch='history -c;clear'
alias q='exit'

```

What is aliasing?

---

### Post by cjv8888 on 2009-05-09
> **Pjotrovitz said:**
> Delete the .bash_history in your home directory.

Thanks.  Found the file and deleted the particular line containing the password.

Problem solved.:)

---

### Post by kerry_s on 2009-05-09
> **cjv8888 said:**
> What is aliasing?

aliasing is so you can set shortcuts for things.

for example instead of typing out> history -c
i would just type> ch
and it would do the same thing.

you can put the commands in ~/.bashrc or you can uncomment a section and and use a separate file(~/.bash_aliases) just for alias's.
i use a separate file.

---

### Post by cjv8888 on 2009-05-09
Thanks!

That should come in handy.

---

