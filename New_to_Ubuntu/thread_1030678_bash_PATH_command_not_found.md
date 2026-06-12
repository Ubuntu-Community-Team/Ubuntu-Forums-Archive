---
title: "bash: PATH: command not found"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by ant2ne on 2009-01-04
Every time I start a new terminal
> bash: PATH: command not found
I can not find this offending PATH command. I've looked in /etc/profile, /etc/rc.local, ~/.profile, /etc/init.d/rc, /etc/init.d/rc.local.  Where else could I have put his offending command?  Where is it suggested that I add custom PATH additions? And what is the proper syntax for adding to PATH?

Thanks!

---

### Post by mcduck on 2009-01-04
The error is not trying to tell you that it cant find a command called "path". What it's telling you that you are trying to run some command but a program with that name cannot be found from current directory or any directory that's in your path.

(So the message means that "PATH" is sending you message "no command found".)

Since you get the error every time you start a terminal I suppose either you have added some incorrect command to your bash profile (~/.profile). Or if it only happens with gnome-terminal check it's settings, you may have configured to run some command when the terminal is started

---

### Post by ant2ne on 2009-01-04
```
bash: PATH: command not found
ant2ne@2ne-buntu:~$ cat ~/.profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
# if [ -d ~/bin ] ; then
#   PATH=~/bin:"{$PATH}"
# fi
# export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ant2ne/scr:~/scr
ant2ne@2ne-buntu:~$ 
```(Note, that last line is a wrap around)

CNTL+ALT+F5 creates a non gnome terminal, it too has this error.

---

### Post by albinootje on 2009-01-04
> **ant2ne said:**
> Every time I start a new terminal

I can not find this offending PATH command. I've looked in /etc/profile, /etc/rc.local, ~/.profile, /etc/init.d/rc, /etc/init.d/rc.local.  Where else could I have put his offending command?  Where is it suggested that I add custom PATH additions?


Are you using 8.10 ? If so, can you try the guest session, and open a terminal and see whether the same error occurs ?
If you're not using 8.10, add a new user to test it likewise.
> 
And what is the proper syntax for adding to PATH?


Temporarily :
```

export PATH=$PATH:/usr/local/some-new-app/bin

```

---

### Post by ant2ne on 2009-01-05
Other users dp not get that error

---

### Post by ant2ne on 2009-01-05
> **albinootje said:**
> Are you using 8.10 ? If so, can you try the guest session, and open a terminal and see whether the same error occurs ?
If you're not using 8.10, add a new user to test it likewise.


Temporarily :
```

export PATH=$PATH:/usr/local/some-new-app/bin

```And permanently?

---

### Post by albinootje on 2009-01-05
> **ant2ne said:**
> Other users dp not get that error

OK, good to know that.
The error must come from some file in your home directory then.

---

### Post by albinootje on 2009-01-05
> **ant2ne said:**
> And permanently?

I'm not sure.
In the past it used to be /etc/profile afair, at least in various Linux distributions.

By the way, my ~/.profile has a PATH mentioned, but I'm never sure which of these files bash reads at log in time. 

.profile
.bashrc
.bash_profile

---

### Post by mcduck on 2009-01-05
> **albinootje said:**
> I'm not sure.
In the past it used to be /etc/profile afair, at least in various Linux distributions.

By the way, my ~/.profile has a PATH mentioned, but I'm never sure which of these files bash reads at log in time. 

.profile
.bashrc
.bash_profile

.profile is used for login shells if .bash_profile or .bash_login doesn't exist (which is the case at least on my Ubuntu setup).

.bashrc is used for non-login shells. (although the .profile file seems to include the .bashrc so changes in .bashrc should afect both login and non-login shells)

I recommend adding the path in .bashrc.

---

