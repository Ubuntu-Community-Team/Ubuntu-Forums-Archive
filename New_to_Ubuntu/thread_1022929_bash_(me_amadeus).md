---
title: "bash (me amadeus?)"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by joejoe148 on 2008-12-27
I am diligently working toward enlightenment.  I have loaded hardy on my computer and am working through an online tutorial ([http://www.linuxcommand.org/)on](http://www.linuxcommand.org/)on) bash.  so far things have been pretty straightforward but I think i have reached the point where the ubuntu terminal is not bash.  

the section is scripts and aliases.  I noted that there isnt a .bash_profile file and now I am beginning do question wtf i am doing.

so...do i need to load bash? use a different terminal program?  I want to learn this right the first time.

---

### Post by taurus on 2008-12-27
If you don't have ~/.bash_profile, create one.

```
touch ~/.bash_profile
```
/bin/bash is not a terminal program.  It's a shell.  There are others that you can use like ksh, zsh, csh, tcsh, etc.

---

### Post by evilkastel on 2008-12-27
if you are interested in scripting you might want to try zsh. offcourse you'll need a custom .zshrc file, since the one created by default is empty.

---

### Post by joejoe148 on 2008-12-27
um, what am i doing when I select applications-accessories-terminal?

um #2, I am not interested in learning scripting yet, I am interested in learning linux and decided that the shell (thanks for the correction) is important in that pursuit

---

### Post by taurus on 2008-12-27
You are just opening a terminal with bash as your shell (default).

```
finger -l
```

---

### Post by joejoe148 on 2008-12-27
ok last question for a while i promise...

so its all bash? are there different flavors? or versions?

---

### Post by taurus on 2008-12-27
Maybe this page is what you need.

[http://www.linuxcommand.org/lts0010.php](http://www.linuxcommand.org/lts0010.php)

---

### Post by joejoe148 on 2008-12-27
actually that is what led me astray when I didnt find the .bash_profile.  I was certain that i was NOT where i imagined and things went downhill from there.  I have moved further along in the tutorial and found the .bashrc and with your help all has become clearer.

---

