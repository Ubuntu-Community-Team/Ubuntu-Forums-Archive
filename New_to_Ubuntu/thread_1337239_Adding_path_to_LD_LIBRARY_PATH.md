---
title: "Adding path to LD_LIBRARY_PATH"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by newport_j on 2009-11-25
What is the command to add a path to LD_LIBRARY_PATH. I want to put an additional path in there indefinitely, not just for a session and have it revert back to the old LD_LIBRARY_PATH when I close the session.  

Newport_j

---

### Post by bodhi.zazen on 2009-11-25
Add your path to ~/.bashrc

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:you_additional_path/here
```

---

### Post by newport_j on 2009-11-25
I see that it can be done that way. But will it remain after you logoff for the day (and shut down the computer). Will it be there tomorrow or do you have to do this command all over again?  I thought that there was something that you can do with the conf file that would make that path additional path permanent.change to the LD_LIBRARY_PATH. 

Newport_j

---

### Post by avidday on 2009-11-25
> **newport_j said:**
> I see that it can be done that way. But will it remain after you logoff for the day (and shut down the computer). Will it be there tomorrow or do you have to do this command all over again?  I thought that there was something that you can do with the conf file that would make that path additional path permanent.change to the LD_LIBRARY_PATH. 

It will. You could also edit the system wide bashrc (although it would have the same effect).

There is another way to get the PATH you are looking for to the dynamic link loader, and that is to edit the link loader cache file (man ld.so to read more). But you probably don't want to do that in this situation, because having non-standard paths (this is for NVIDIA CUDA, I take it) in the link loader cache path can cause some very hard to diagnose library and symbol conflicts that are way out of the "absolute beginner" league.

---

### Post by brij on 2009-11-26
the path you export with LD_LIBRARY_PATH should go when you log out. If you want it there permanently you need to put that command in your bashrc file under home directory

---

### Post by bodhi.zazen on 2009-11-26
> **brij said:**
> the path you export with LD_LIBRARY_PATH should go when you log out. If you want it there permanently you need to put that command in your bashrc file under home directory

My post advised :

> Add your path to ~/.bashrc

---

### Post by ilil on 2009-11-26
I think the file ~/.profile is more preferable for such tasks

---

### Post by avidday on 2009-11-26
> **ilil said:**
> I think the file ~/.profile is more preferable for such tasks
You would think wrong. The standard Ubuntu .profile include .bashrc anyway, plus .profile is only read by login shells, which means any other shell won't pick up any environment settings you specify in .profile.

---

### Post by ilil on 2009-11-26
> **avidday said:**
> You would think wrong. The standard Ubuntu .profile include .bashrc anyway, plus .profile is only read by login shells, which means any other shell won't pick up any environment settings you specify in .profile.

What other shell do you speak about? I use .profile to set up all vars like PATH, MANPATH, PKG_CONFIG_PATH, whatever and it just works. .bashrc is overkill here

---

### Post by avidday on 2009-11-26
> **ilil said:**
> What other shell do you speak about? I use .profile to set up all vars like PATH, MANPATH, PKG_CONFIG_PATH, whatever and it just works. .bashrc is overkill here

To repeat myself, .profile is only read by shells that are started by the login process. So login from the text console, or via ssh, telnet, etc and it will be read and environment variables set. Any other interactive shell (inside a terminal in X11 or an interactive shell forked by any process other than login) and only .bashrc is read. Not .profile.

Consider this .profile file to which I have added a new variable:
```

avid@cuda:~$ cat .profile 
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

DUMBASS=1
```If I then **login** to the box with this .profile, I see my new variable:
```

avid@cuda:~$ ssh localhost
Linux cuda 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

57 packages can be updated.
65 updates are security updates.

Last login: Thu Nov 26 20:49:49 2009 from localhost
avid@cuda:~$ echo $DUMBASS
1

```but if I now start a new shell, it doesn't exist, because .profile isn't read:
```
Last login: Thu Nov 26 20:49:49 2009 from localhost
avid@cuda:~$ echo $DUMBASS
1
avid@cuda:~$ bash
avid@cuda:~$ echo $DUMBASS

avid@cuda:~$ 

```If you start X11, login, and then open a terminal or xterm you **will not see any enivroment settings from .profile. **It is clearly explained in the manpage for bash.

---

### Post by ilil on 2009-11-26
> **avidday said:**
> but if I now start a new shell, it doesn't exist, because .profile isn't read:
```
Last login: Thu Nov 26 20:49:49 2009 from localhost
avid@cuda:~$ echo $DUMBASS
1
david@cuda:~$ bash
david@cuda:~$ echo $DUMBASS

david@cuda:~$ 

```If you start X11, login, and then open a terminal or xterm you **will not see any enivroment settings from .profile. **It is clearly explained in the manpage for bash.

You are wrong. Set up DUMBASS in .profile as "export DUMBASS=1", not just "DUMBASS=1" and repeat your experiment. 
And ... why are you so evil?

---

