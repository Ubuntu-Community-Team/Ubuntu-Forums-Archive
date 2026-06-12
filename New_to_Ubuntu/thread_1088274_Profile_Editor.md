---
title: "Profile Editor"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-05
Hi,
I was wondering where to install or find if already installed a profile editor in Ubuntu 8.10. I am going to follow someone's instruction:
enable the 'Run command as a login shell' option in the 'Title and command' tab of the profile editor ('Edit' --> 'Current profile...').
Thanks!

---

### Post by x33a on 2009-03-05
take a look at

system -> administration -> users and groups.

---

### Post by flylehe on 2009-03-05
I have, but I couldn't fine a place to enable the 'Run command as a login shell' option

---

### Post by x33a on 2009-03-05
sorry i didn't read the question properly.

open gnome-terminal, 

click on edit -> profile preferences -> title and command. 

check run command as a login shell.

by the way, why do you need this option? it can have serious repercussion if you run a wrong command. you should always use sudo instead of root sudo.

take a look here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by flylehe on 2009-03-05
Thanks!
I am doing this, because I need to add my own executable's path to PATH. While .bashrc is a place to go, I need to run my bash script under bashdb in emacs, which does not invoke a shell, so I always get the "command not found" error. I want to add the PATH adjustment in .bash_profile, but it's weird this file is not invoked during login in Ubuntu. To make sure the .bash_profile is read when login, I have to enable the 'Run command as a login shell' option. Even so, PATH is still not including the executable path under bashdb in emacs. Anyway to make sure .bash_profile would be read at login?

What's serious repercussion if you run a wrong command? If it is really a bad idea, what's the better way to get PATH modified?

---

### Post by x33a on 2009-03-06
yes, you need to enable run command as a login shell for .bash_profile to be read at startup. but since you say that even this option is not working, i am out of ideas.

as for the risks involved around running a root shell, take a look at the link i posted before.

---

