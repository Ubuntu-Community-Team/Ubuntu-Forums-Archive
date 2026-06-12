---
title: "Setting &quot;export PATH=/usr/bin:/bin&quot;  permnently"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by chandu870114 on 2011-07-08
Hi

After opening terminal when I use **ls, sudo..** or any other commonds am getting below errors

**Command 'ls' is available in '/bin/ls'**
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found

**Command 'sudo' is available in '/usr/bin/sudo'**
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
sudo: command not found


But by using below export am able to solve this problem

**export PATH=/usr/bin:/bin ** (I found it in forums)


My problem is when I open new Terminal I have to use above export everytime. 

There is anyway to set it permnently??? 
and what am doing when I use that export???

Regards
chandu

---

### Post by ruffEdgz on 2011-07-08
Its great that the **export PATH=/usr/bin:/bin** worked but you should get more paths in that environment variable. Here are all the paths I have on my 11.04 Ubuntu:
```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
Is there anything you changed recently in any of the file below:
```

/etc/profile
/etc/profile.d/*
~/.profile
~/.bashrc

```
If not, can you type the command below and reply back to this post (this is only helpful if you **haven't** placed in your export command)?:
```

env | grep -i path

```

Cheers!

---

### Post by dcsoldschool53 on 2011-07-08
> **chandu870114 said:**
> Hi

After opening terminal when I use **ls, sudo..** or any other commonds am getting below errors

**Command 'ls' is available in '/bin/ls'**
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found

**Command 'sudo' is available in '/usr/bin/sudo'**
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
sudo: command not found


But by using below export am able to solve this problem

**export PATH=/usr/bin:/bin ** (I found it in forums)


My problem is when I open new Terminal I have to use above export everytime. 

There is anyway to set it permnently??? 
and what am doing when I use that export???

Regards
chandu


Put it in the .bashrc file in your home directory. Then, after you close and save it, type in a terminal```
source ~/.bashrc
```You will not need to reboot before it to take affect using this command.

---

### Post by chandu870114 on 2011-07-08
HI bryan
Thanks for your response

[B] env | grep -i path
[/B]
After executing above command I found below output

[B]TOOLCHAIN_PATH=/home/chandu/CodeSourcery/Sourcery_G++_Lite/
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
PATH=/usr/bin:/bin
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
[/B]

---

### Post by chandu870114 on 2011-07-08
> **dcsoldschool53 said:**
> Put it in the .bashrc file in your home directory. Then, after you close and save it, type in a terminal```
source ~/.bashrc
```You will not need to reboot before it to take affect using this command.

HI
Thanks for your response:popcorn:
But Sorry I don't know how to put the export PATH in .bashrc file. I opened bashrc file by using below command

**pico ~/.bashrc**
Then I found below path at the end of the file
[B]
PATH=/home/chandu/Documents/Old\ system\ files/Downloads/android-sdk-linux_x86/platform-tools/:PATH[/B]

How to put PATH now???

Thanks and Regards
chandu

---

### Post by chandu870114 on 2011-07-08
Hi

I got it... :p   but I don't know is it the correct way or not!!!!

First I opened bashrc file
>  **pico ~/.bashrc** 

At the end of the bashrc file I found my previous PATH.
PATH=/home/chandu/Documents/Old\ system\ files/Downloads/android-sdk-linux_x86/platform-tools/:PATH
Then I added "/usr/bin:/bin" at the end of the PATH
Then my new PATHlook like> **PATH=/home/chandu/Documents/Old\ system\ files/Downloads/android-sdk-linux_x86/platform-tools/:/usr/bin:/bin:PATH**

Next 
> source ~/.bashrc 

:popcorn::popcorn::popcorn:

---

### Post by dcsoldschool53 on 2011-07-08
Does it work for you is the question? If it works, go with it. If it doesn't work, leave it alone and find a new way.

---

### Post by chandu870114 on 2011-07-09
> **dcsoldschool53 said:**
> Does it work for you is the question? If it works, go with it. If it doesn't work, leave it alone and find a new way.
Ya it worked for me

---

### Post by wojox on 2011-07-09
How did you loose those from your environment variables?

```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/wojox/Bin
```

```
 cat /etc/environment 
```

Is were their stored.

---

### Post by chandu870114 on 2011-07-09
> **wojox said:**
> How did you loose those from your environment variables?

```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/wojox/Bin
``````
 cat /etc/environment 
```Is were their stored.

Hi
It is there in  **/etc/environment**
> 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"


But when I use [B]echo $PATH
[/B]Am getting

> /home/chandu/Documents/Old system files/Downloads/android-sdk-linux_x86/platform-tools/:/usr/bin:/bin: PATH

---

### Post by Vaphell on 2011-07-09
i think you missed $ sign before PATH. PATH without $ is a literal string and you have it at the end, while $PATH would take the value of the variable and append it after your custom android sdk directory
/home/chandu/Documents/Old system files/Downloads/android-sdk-linux_x86/platform-tools/:/usr/bin:/bin:**PATH**

example using echo
```
echo /some/dir:**PATH**
/some/dir:**PATH**

echo /some/dir:**$PATH**
/some/dir:**/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games**

```

---

### Post by chandu870114 on 2011-07-09
> **Vaphell said:**
> i think you missed $ sign before PATH. PATH without $ is a literal string and you have it at the end, while $PATH would take the value of the variable and append it after your custom android sdk directory
/home/chandu/Documents/Old system files/Downloads/android-sdk-linux_x86/platform-tools/:/usr/bin:/bin:**PATH**

example using echo
```
echo /some/dir:**PATH**
/some/dir:**PATH**

echo /some/dir:**$PATH**
/some/dir:**/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games**

```

Hi
I appreciate for your help :P.
Thank you very much

In bashrc file I **removed** **/usr/bin:/bin **and **added $ symbol before PATH**
my new PATH in bashrc file
> PATH=/home/chandu/Documents/Old\ system\ files/Downloads/android-sdk-linux_x86/platform-tools/:$PATH

Now it's working and everything perfect...

---

### Post by sedoyksa on 2012-04-05
but for me it doesnt work
my ~/.profile
```
 export ENV=$HOME/.setup  #set and export ENV variable
      export PATH=$PATH:$HOME:  #set and export PATH variable
      export EDITOR=ed          #set and export EDITOR variable
      export PS1='$LOGNAME':'$PWD':' >'
PATH=/bin
PATH=/usr/bin
```

/etc/prolile
```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
for i in /etc/profile.d/*.sh; do
if [ -r $i ]; then
. $i
fi
done
unset i
fi

if [ "$PS1" ]; then
if [ "$BASH" ]; then
PS1='u@h:w$ '
if [ -f /etc/bash.bashrc ]; then
. /etc/bash.bashrc
fi
else
if [ "`id -u`" -eq 0 ]; then
PS1='# '
else
PS1='$ '
fi
fi
fi

umask 022
PATH=/usr/bin
PT5HOME=/opt/pt
export PT5HOME
```

/etc/enviroment
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LANG="ru_RU.utf8"
```

~/.bashrc
```
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
```

its all works if i type in console 
```
export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

BUT if i open new terminal - i have errors

comand 'uname' is in '/bin/uname'
command cannot be found, cause '/bin' is not in PATH variable
uname: command not found
bash: [: =: 
command 'sed' is in '/bin/sed'
command cannot be found, cause '/bin' is not in PATH variable
sed: command not found
Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found

AND

#env | grep -i path
command 'grep' not available in '/bin/grep'
command cannot be found, cause '/bin' not encluded in PATH
grep: command not found

---

### Post by sedoyksa on 2012-04-07
solved

---

