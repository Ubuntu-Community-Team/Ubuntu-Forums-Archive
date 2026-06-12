---
title: "How to Set Aliases in Ubuntu 8.04?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2010-01-25
Ey guys, kind of a noob question, but I have been trying and have had no luck. I added the following to my ~/.bashrc file:
```

#CUSTOM ALIASES
edit_aliases='vim ~/.bash_aliases'
vi='vim'

```

And no go. I even uncommented the following:
```

# if [ -f ~/.bash_aliases ]; then
# . ~/.bash_aliases
# fi

```

And placed the previously pasted text into a new file ".bash_aliases". What am I doing wrong here? And thanks for any help!

---

### Post by StunnerAlpha on 2010-01-27
Bump... anyone?

---

### Post by Mornedhel on 2010-01-27
You're using the syntax for setting variables.

The correct syntax for aliases is

```
alias newname=oldname
```

Do not forget the "alias" command.

---

### Post by StunnerAlpha on 2010-01-27
Ey, thanks for the response. I have changed it to:
```

#Custom aliases:
alias 'edit_aliases'='vim ~/.bash_aliases'
alias vi='vim'

```

And even tried this:

```

#Custom aliases:
alias edit_aliases='vim ~/.bash_aliases'
alias vi='vim'

```

Still no go... Should I omit the quotations?

---

### Post by sisco311 on 2010-01-27
> **StunnerAlpha said:**
> 

```

#Custom aliases:
alias edit_aliases='vim ~/.bash_aliases'
alias vi='vim'

```


this should work. Did you source the bashrc file:
```
. ~/.bashrc
```?

---

### Post by Mornedhel on 2010-01-27
I can confirm that it works for me. Have you tried it in a new terminal, one that you opened *after* saving your modifications ?

---

### Post by StunnerAlpha on 2010-01-27
What do you mean by "source the bashrc file"? Here is my .bash_aliases file:
```

#Custom aliases:
alias edit_aliases='vim ~/.bash_aliases'
alias vi='vim'

```
And here is my .bashrc file:
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
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

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
#force_colored_prompt=yes

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

#UNCOMMENTED THE BELOW 3 LINES
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

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

#CUSTOM ALIASES
#edit_aliases='vim ~/.bash_aliases'
#vi='vim'


```
Thanks for the help!

---

### Post by StunnerAlpha on 2010-01-27
> **Mornedhel said:**
> I can confirm that it works for me. Have you tried it in a new terminal, one that you opened *after* saving your modifications ?

Woah, that did it thanks! I was sshed into my Ubuntu machine and I had to exit and reconnect for it to work. It works with the files I posted in my previous post. Thanks again fellas! :)

---

### Post by sisco311 on 2010-01-27
> **StunnerAlpha said:**
> What do you mean by "source the bashrc file"?

When  an  interactive  shell that is not a login shell is started, bash reads and executes commands from  /etc/bash.bashrc  and  ~/.bashrc,  if these  files  exist.

If you change the content of the ~/.bashrc file, you have to start a new shell or (re)read and execute the commands from the file:
```
source ~/.bashrc
```
or
```
. ~/.bashrc
```

For details see:
```
man bash | less +/^INVOCATION

```
and
```
man bash | less +/"source filename "
```

---

### Post by StunnerAlpha on 2010-01-27
Alright, thanks for the explanation.

---

### Post by sisco311 on 2010-01-27
> **StunnerAlpha said:**
> Alright, thanks for the explanation.

You're welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

