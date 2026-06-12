---
title: "Defferences between Startup and Init Bash files"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by phoda on 2009-10-21
I'm confused about the differences between the Bash startup and initialization files. Could you help me understand these differences?

What I already know?

I know that Bash looks for startup files system-wide settings in the /etc/profile and for personal settings, in the .bash_profile, .bash_login and .profile files, inside the home directory;

And I know that Bash looks for initialization files system-wide settings in the /etc/bash.bashrc and for personal settings, in the .bashrc file, inside the home directory.

But why the keywords "startup" and "initialization" are used to different things? Aren't these words symnonimous? Could you light me? :confused:

---

### Post by martrn on 2009-10-21
There are many different CLI (command line interfaces) that you could use if you needed a CLI (for example on a server with no gui).  You could use csh or bash or something else.  This is just about an order or precedence.

Loading ksh CLI:
================
1. Kernel looks at /etc/profile to see what permissions or environment the shell can run in.
2.  [----- Load/fetch/execute ksh (shell) ------]
3.  Ksh shell looks at /etc/ksh.kshrc and for personal settings and shell initilisation tasks.


Loading bash CLI:
================
1. Kernel looks at /etc/profile to see what permissions or environment the shell can run in.
2.  [----- Load/fetch/execute bash (shell) ------]
3.  bash shell looks at /etc/bash.bashrc and for personal settings, and shell initilisation tasks.

I think here "initialisation" is refering to the initilisation of the individual shell which could be diffrent to the initilisation of a diffrent shell as gnu/linux has more than one command language interpreter or shell.

---

### Post by phoda on 2009-10-21
Thanks!

---

