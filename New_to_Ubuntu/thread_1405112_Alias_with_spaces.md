---
title: "Alias with spaces"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by Rayve on 2010-02-12
I keep finding myself coming back here for some of the most basic commands I thought I had licked... ah, well!

I'm trying to make the following alias:
```

# alias for wow to start, as of 11 Feb, with opengl enabled
alias wow='wine ~/.wine/dosdevices/c:/Program\ Files/World\ of\ Warcraft/Wow.exe -opengl'

```But I get the error:
```

candice@candice-desktop:~$ wow
bash: /home/candice/.wine/dosdevices/c:/Program: No such file or directory

```Clearly, my efforts at escaping the spaces have failed.  What am I missing?

EDIT: I ran ```
 source ~/.bashrc 
``` after closing out my gedit window of .bashrc and now it works!  I guess it didn't like having the window open or something.  :)

I love it when I answer my own question.  Sorry for any inconvenience.

---

### Post by Rayve on 2010-03-25
Actually, I ran into a similar problem, so I thought I'd open this thread back up.

Here is what I'm trying to input:

```
 # alias to killall java
# alias killjava='kill -9 `ps -ef|grep java|grep -v grep|awk \'{print $2}\'`'

```

I did the \ escapes myself, so the actual code (which works) is ```
 kill -9 `ps -ef|grep java|grep -v grep|awk '{print $2}'` 
```

And with or without being commented, I get the following error(s):
```

candice@candice-desktop:~$ killjava
> 
> bash: unexpected EOF while looking for matching ``'
bash: syntax error: unexpected end of file
candice@candice-desktop:~$ gedit /home/candice/.bashrc
candice@candice-desktop:~$ source ~/.bashrc           
candice@candice-desktop:~$ killjava                   
> bash: unexpected EOF while looking for matching ``'
bash: syntax error: unexpected end of file
candice@candice-desktop:~$ gedit /home/candice/.bashrc
candice@candice-desktop:~$ source ~/.bashrc
bash: /home/candice/.bashrc: line 108: unexpected EOF while looking for matching ``'
bash: /home/candice/.bashrc: line 110: syntax error: unexpected end of file

```

So you can see it first thinks I have a prompt (the ">" lines) and then it gives an EOF error.

Any ideas?  There's no way I'll remember this command without an alias, and while I can look it up every time, I'd love to be able to use an alias the next time my java process goes haywire.

---

### Post by gmargo on 2010-03-25
As soon as an alias becomes too complex, ditch it and use a function.  Here's your two aliases as functions:
```

wow()
{
    local wowexe="$HOME/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe"
    wine "$wowexe" -opengl
}

killjava()
{
    local javapid=$(ps -ef | grep java | grep -v grep | awk '{print $2}')
    if [ "x$javapid" != "x" ]; then
        kill -9 $javapid
    else
        echo "Java process not found"
    fi
}


```

---

### Post by Rayve on 2010-03-25
Thanks, gmargo, I'll give those a try. :)

I put them into my .bashrc as normal?

---

### Post by Rayve on 2010-06-04
The killjava function works perfectly, but I'm getting an error with the other:

```

candice@candice-desktop:~$ source /home/candice/.bashrc
bash: /home/candice/.bashrc: line 104: syntax error near unexpected token `('
bash: /home/candice/.bashrc: line 104: `wow()'

```

Thanks!

---

### Post by gmargo on 2010-06-04
Something in your .bashrc, just before line 104, is incorrect.  The wow() function is fine.  Post your .bashrc file.

---

### Post by Rayve on 2010-06-04
In its entirety:

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

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
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

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

# alias for wow to start, as of 11 Feb, with opengl enabled
# alias wow='wine ~/.wine/dosdevices/c:/Program\ Files/World\ of\ Warcraft/Wow.exe -opengl'
# created as a function by gmargo on ubuntuforums.org, along with killjava
wow()
{
    local wowexe="$HOME/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe"
    wine "$wowexe" -opengl
}

# for rm to be interactive each time (safe!)
alias rm='rm -i'

# alias to killall java
# alias killjava='kill -9 `ps -ef|grep java|grep -v grep|awk \'{print $2}\'`'
killjava()
{
    local javapid=$(ps -ef | grep java | grep -v grep | awk '{print $2}')
    if [ "x$javapid" != "x" ]; then
        kill -9 $javapid
    else
        echo "Java process not found"
    fi
}
```

---

### Post by gmargo on 2010-06-04
I don't see any problem with that .bashrc.  I sourced it and did not receive any syntax errors.

---

### Post by Rayve on 2010-06-05
I copied/pasted it back into my own .bashrc and still get the line 104 syntax error.

```

candice@candice-desktop:~$ source /home/candice/.bashrc
bash: /home/candice/.bashrc: line 104: syntax error near unexpected token `('
bash: /home/candice/.bashrc: line 104: `wow()'

```

Ah, well.  I commented out the function and uncommented the wow alias I had before and it sources now.

Thanks for the help!

---

### Post by gmargo on 2010-06-05
I can't really explain that.  Maybe there's a stray uni-something code character in there?  I would try typing it in, without copy/pasting.  Build it up from a blank function.

---

