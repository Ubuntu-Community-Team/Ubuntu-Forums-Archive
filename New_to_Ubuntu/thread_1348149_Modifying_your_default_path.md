---
title: "Modifying your default path?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2009-12-06
So if I wanted to add a directory to my path's that are automatically searched for programs and scripts and all that whenever I type something in the terminal, how do I do it?  I imagine it's something quite easy, in fact I used to know how to do it a long time go, but it's been so many years since my unix class (which was taught on red hat) I just can't remember how.

Also, if I want to alias something, how do I make it so that it will be persistent beyond me closing the terminal?

---

### Post by Ocxic on 2009-12-06
create a file called .bash_profile in your home directory ( don't forget the . at the begining) and past this in it
```

#The default .bash_profile looks like this:
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/Software/bin ] ; then
    PATH=~/Software/bin:"${PATH}"
fi

```edit
 if [ -d ~/Software/bin ] ; then
    PATH=~/Software/bin:"${PATH}"
to suit your needs.

For this to work you'll also have to set gnome-terminal to run as a login shell in your preferences.

---

### Post by scared0o0rabbit on 2009-12-07
And if I do that it will still keep the default paths already set in ubuntu?

---

### Post by Ocxic on 2009-12-07
yes it will just append to what is already there.

---

### Post by Bradj47 on 2009-12-07
> **Ocxic said:**
> yes it will just append to what is already there.

Yes, but remember if you have two programs by the same name in different paths then the system will run the program of that name in the first path listed.

---

### Post by Locke_99GS on 2009-12-07
Another option is to either move executable scripts to /usr/bin or /usr/local/bin, or create symlinks in one of those directories pointing to the actual file.

---

### Post by spiderbatdad on 2009-12-07
another option is to create a directory named bin in your home directory and place your programs in it...~/bin should already be in $PATH once the directory is created.

This is performed by the file ~/.profile on my default Karmic installation.

---

### Post by scared0o0rabbit on 2009-12-08
Thanks for the tips.  I was essentially looking for a way to have a bunch of scripts that ran things, so this will do it!

---

