---
title: "I did something stupid with my PATH"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by bdevine on 2010-12-30
Hi guys,

I installed a new 10.04 on a virtual box.  I was following instructions on how to install a particular piece of software that went in the bin file (and why not), and I mindlessly started following their instructions for setting the path.  The problem was that they assumed a csh shell, not bash.  After futilely creating a .cshrc and a non-working path variable in it, I finally got it straightened out in the .bash_profile instead.

But now every time my terminal starts up, it issues this error message, before anything else:

.cshrc: command not found

It's kind of driving me nuts.  I went back and checked all the places I screwed around with and everything looks clean.  I've restarted (the vm).  What am I missing?

Thanks for any help,

Brandon

---

### Post by matt_symes on 2010-12-30
Hi
> 
I was following instructions on how to install a particular piece of  software that went in the bin file (and why not), and I mindlessly  started following their instructions for setting the pathCan you post a link to the instructions so we can see what you have done?

Also, open at terminal and type

```
cat  ~/.bash_profile
```

and also 

```
cat  ~/.bashrc
```

and post the results of both back here.

Kind regards

---

### Post by bdevine on 2010-12-30
Thanks for the reply.  As far as the instructions go, it was from an html file on a cd, but I will copy:
> 
...(E)ntering the command
echo $path
should show something terminating in ~/bin or /home/myname/bin in its output (different Linux installations may store the user home directories in different locations).  

If the ~/bin directory does not show up in your path, we need to put it there. When the xterm application starts, it looks for a file called .cshrc (the dot is part of the name) in your home directory. Check first if you have such a file by doing ls ~/.cshrc. If the file exists, bring it up in a text editor and add the line
set path = (~/bin $path)
and save the .cshrc file. If the file does not yet exist, type the following three lines
cat > ~/.cshrc
set path = (~/bin $path)
^D
where ^D stands for control-D. You now have a ~/.cshrc file that adds ~/bin to your path in every newly launched xterm application.

To verify that everything is OK,  enter the command
source ~/.cshrc


And now for my info:
```

brandon@VB-Ubuntu:~$ cat ~/.bash_profile
export PATH=$PATH:/usr/bin

brandon@VB-Ubuntu:~$ cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
.cshrc creating bin    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi


```

I no longer have a .cshrc file - and now that I look at those instructions again, issuing echo $path still doesn't return anything, but issuing which <program> confirms it's in /usr/bin, and I can start it up with no problems. 

Thanks again for the response and any help!

Brandon

---

### Post by matt_symes on 2010-12-30
Hi

In you .bashrc file change

```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
**.cshrc creating bin**    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```

to 

```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```

Kind regards

---

### Post by bdevine on 2010-12-30
THANK YOU!  That was really driving me to distraction!  I will know to look more closely the next time some small thing like this comes up.  I appreciate it!

---

