---
title: "Permission dialog box before deletion"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by babaikaushik on 2011-05-08
Hello Forum,

When I am deleting any file it gets deleted instantly without asking whether I really want to purge the file .

How can I configure the system so that it asks me whether I want to delete through a dialog box and once I confirm the same then only the file is deleted.

Cheers
Kaushik

---

### Post by JKyleOKC on 2011-05-08
If you're working at the command line and using "rm" to do the deleting, create an alias for it: the command is "alias rm=rm -i" and it should be added to your .bashrc file in your home directory.

This will force the "mother may I?" prompt each time you issue the "rm" command.

If you're working from a graphical file manager, most of them don't actually delete files but rather move them to your "trash bin" where you can have second thoughts.

Does this help? If you need more detailed instructions on creating the alias so it will be there each time you power up just let us know and we'll provide step-by-step instructions. The ability to create aliases for commands is one of the most powerful tools you have to customize your system to work YOUR way.

---

### Post by babaikaushik on 2011-05-09
Thanks for your advice .

May I request to please share the procedure for creating the alias ?

Thanks for your help 

Cheers 
Kaushik

---

### Post by doas777 on 2011-05-09
> **babaikaushik said:**
> Thanks for your advice .

May I request to please share the procedure for creating the alias ?

Thanks for your help 

Cheers 
Kaushik
as JKyle said:
```
alias rm=rm -i
```

---

### Post by babaikaushik on 2011-05-09
Hello,

I executed the following command through terminal. 

pico .profile
alias rm='rm -i'

Looks like I made some mistake as it is still not giving me any prompt before deleting :(

Cheers 
Kaushik

---

### Post by bodhi.zazen on 2011-05-09
> **babaikaushik said:**
> Hello,

I executed the following command through terminal. 

pico .profile
alias rm='rm -i'

Looks like I made some mistake as it is still not giving me any prompt before deleting :(

Cheers 
Kaushik

You have to log off and back in for the changes to take effect and you probably want to use ~/.bashrc and not ~/.profile 

That ^^ is a minor point, but, .bashrc is IMHO better for configuration of interactive shells and .profile for environmental variables and non-interactive shells (scripts).

---

### Post by babaikaushik on 2011-05-09
Thanks for your reply.

In which iine should I write the alias ? When I execute pico .bashrc it shows the following lines

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
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
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

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

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

---

### Post by compmodder26 on 2011-05-09
If you are wanting to keep it organized then add that line right below the last alias definition.  Otherwise, just place it at the bottom of the file.

And another option is to what it says here:

> # Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
. ~/.bash_aliases
fi

---

### Post by babaikaushik on 2011-05-09
Success ... Thanks experts for enlightening me. 

One last question on aliases

If I maintain one alias as Install ='Sudo apt-get install' then from the next time can I install with the command  'Install application/package name'

Cheers
Kaushik

---

### Post by JKyleOKC on 2011-05-09
Almost, but remember that all Linux systems are case-sensitive and the command is "sudo" rather than "Sudo" so unless you correct that, you'll get an error that the command does not exist.

When you use this alias, you'll still be prompted for your password, but it will definitely save some typing.

Here's another useful one: ```
alias mv=mv -i
```This will add the prompt to the "mv" command just as the first one does for "rm" and these two can save lots of frustration by helping keep you from doing things to the wrong files.

Oops! I initially failed to notice another critical flaw in your proposed "install" alias: leave off those quote marks! You want the arguments to the command to be recognized as such. With the quote marks in place, the whole string would be treated as the command -- and no such command exists. The general rule is that everything to the right of the "=" sign must be exactly as you would type it on the command line, since the alias action is simply to replace what you typed with an exact copy of the right-side string.

EDIT: Ignore that previous paragraph!!! The single quotes are essential to the way things work, as I just discovered when testing. It must have been a senior moment or something...

---

