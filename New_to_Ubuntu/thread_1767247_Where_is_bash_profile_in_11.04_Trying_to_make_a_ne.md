---
title: "Where is bash profile in 11.04? Trying to make a new  PATH."
date: 2011-05-25
forum: New to Ubuntu
---

### Post by xXzero_contentXx on 2011-05-25
omg i had to type this three times because i forgot to add a prefix-Note to whoever programmed this please make it so if i press submit it doesnt erase my message because i forget prefix.  

Im trying to make a new PATH so my directory in home can execute files.  I read that im supposed to edit a .bash_profile file but i dont see it all is see is .bash_history .bash_logout .bashrc 

OS-Ubuntu 11.04
GNU bash, version 4.2.8(1)-release (i686-pc-linux-gnu)

---

### Post by sanderd17 on 2011-05-25
You can use the .bashrc file: just open it and add a command like

```

PATH=$PATH:/path/to/add

```

to it on the end.

---

### Post by matt_symes on 2011-05-25
Hi

The ~/.bash_profile file does not have to exist. If it does it will be sourced (run) by lower scripts.

It does not exist on a Lucid install either unless you create it yourself.

```
matthew@matthew-laptop:~$ ls -l .bash*
-rw------- 1 matthew matthew 41307 2011-05-25 03:14 .bash_history
-rw-r--r-- 1 matthew matthew   220 2011-05-08 22:38 .bash_logout
-rw-r--r-- 1 matthew matthew  3103 2011-05-08 22:38 .bashrc
matthew@matthew-laptop:~$
```From ```
man bash
```> 

When  bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes commands from the file /etc/profile, if that file exists.  **After reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile, in that order, and reads and executes commands from the first one that exists and is readable.**  The --noprofile option may be used when the shell is started to inhibit this behavior.

       When a login shell exits, bash reads and executes commands from the file ~/.bash_logout, if it exists.

       **When  an  interactive  shell  that is not a login shell is started, bash reads and executes commands from /etc/bash.bashrc and ~/.bashrc, if these files exist**.  This may be inhibited by using the --norc option.  The --rcfile file option will force bash to read and execute commands from file instead of /etc/bash.bashrc and ~/.bashrc.

       When bash is started non-interactively, to run a shell script, for example, it looks for the variable BASH_ENV in the environment, expands its value if it appears there,  and  uses  the expanded value as the name of a file to read and execute.  Bash behaves as if the following command were executed:
      if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi
but the value of the PATH variable is not used to search for the file name.Kind regards

---

### Post by xXzero_contentXx on 2011-05-27
i feel like such a noob! thanks to all who replied!! the funniest thing about me learning ubuntu now is i feel like im revisiting my life with computers in the 80's with the terminal and command prompts. As far as weve come with technolgy we still use terminals.  And i love it!!! ahhh im such a nerd :( ahh the memories of DOS commodore pets vic 20's 300 baud modems BBS's lol.

---

