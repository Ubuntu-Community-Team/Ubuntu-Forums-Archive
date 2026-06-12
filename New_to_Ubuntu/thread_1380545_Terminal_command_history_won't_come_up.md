---
title: "Terminal command history won't come up"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2010-01-13
So my terminal command history will not show up for any user except root.  Every other user just gives me ^[[A  whenever I hit the up key.

Every other user on the system was migrated from a slackware system, so that might have something to do with it.

Using server 8.04.

thanks.

---

### Post by CryptiniteDemon on 2010-01-13
I guess I should also mention that no user except root will show the current working directory before the $ in the terminal.

---

### Post by x33a on 2010-01-13
post your .bashrc and also see if the home directory contains .bash_history.

---

### Post by llamabr on 2010-01-13
My guess is that those users are not using bash at all, but some other shell.

You can load bash by just typing

```
bash
```

at the prompt, then your history should work.  You can change the default shell for a user with

```
chsh
```

---

### Post by CryptiniteDemon on 2010-01-14
The bashrc and bash history files that the users are using are the same ones from /etc/skel.  I copied those into the home directories but still get the same results

---

### Post by nothingspecial on 2010-01-14
May sound like a silly question, but

Do the users own their own .bashrc?

---

### Post by CryptiniteDemon on 2010-01-14
The permissions on the files are all set so that the owner and group of the file is the user's group.

---

### Post by CryptiniteDemon on 2010-01-15
Any other ideas?

---

### Post by CryptiniteDemon on 2010-01-15
So I've noticed that it won't execute the bash file whenever I log in.  If I run "exec bash" everything works fine and I have my command history and everything.  But I can't figure out why my .bashrc file isn't executed upon login.

Here are my .bashrc and .bash_profile files:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```


```
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
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

---

### Post by CryptiniteDemon on 2010-01-15
Well I'm an idiot.  I didn't notice that when I migrated the /etc/passwd file over to ubuntu that none of the users I migrated included a path to /bin/bash.

put it in and now it works like a charm.

---

### Post by nothingspecial on 2010-01-15
It`s good linux, isn`t it ;)

---

