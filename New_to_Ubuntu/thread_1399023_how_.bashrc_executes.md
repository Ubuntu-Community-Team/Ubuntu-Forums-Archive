---
title: "how .bashrc executes?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Macinbomzh on 2010-02-05
I have to know how .bashrc executes, does ubuntu wait for the script to complete and then
continues the loading, or is it allowing .bashrc to run parallel to the loading?
Is there a way to run a command as root when logging into a user?

---

### Post by cong06 on 2010-02-05
Maybe you mis understand the "~/.bashrc" file?

This file (as most that end with 'rc') is a configuration files, and helps to configure the bash prompt.
Some of the lines of code here set up variables, some set up aliases, some set up coloring.

If you make a change to the '.bashrc' file, you want to re-load it. This happens automatically when you open a terminal, but to save you the 'opening and closing' just type:
```

. .bashrc

```

Maybe this will help: [http://tldp.org/LDP/abs/html/sample-bashrc.html](http://tldp.org/LDP/abs/html/sample-bashrc.html)

---

### Post by Macinbomzh on 2010-02-05
ok, so is there a way to execute a command as a superuser after login?
basically my problem is that powernowd, a cpu freq control daemon, is switching the governor to performance after 7 seconds of login
because ondemand is not working; so I wrote a program that waits for the switch to performance and
after that it switches it back to userspace but I need to execute it at login

---

### Post by cong06 on 2010-02-06
It sounds like you want to execute it in the 'rc.local' file?

Either that or:
System > Preferences > Startup

Probably what you were confusing it with is the ".bash_profile" but I'm pretty sure that doesn't run until you open up a terminal.

[http://hacktux.com/bash/bashrc/bash_profile](http://hacktux.com/bash/bashrc/bash_profile)

---

