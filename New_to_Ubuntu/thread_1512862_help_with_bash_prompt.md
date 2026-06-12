---
title: "help with bash prompt"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Genomefreak on 2010-06-18
i found this really awesome PS1 and want to copy some into my .bashrc but whatever i do it just keeps coming up with the commented lines above it and then the old prompt

---

### Post by nhasian on 2010-06-18
can you tell us exactly what steps you are doing?
what do you expect should happen?
what is really happening?

---

### Post by inversecow on 2010-06-18
> **Genomefreak said:**
> i found this really awesome PS1 and want to copy some into my .bashrc but whatever i do it just keeps coming up with the commented lines above it and then the old prompt

Here's an article from IBM that might help:
[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/]("http://www.ibm.com/developerworks/linux/library/l-tip-prompt/")

NOTE: Run the below to "test" your changes (reloads your .bashrc without having to "kill"/"restart" the shell.
```

source ~/.bashrc

```

---

### Post by Genomefreak on 2010-06-18
sorry for being inexact, 
when i put the code for the prompt right under the color prompt comment it says : #Commented out, don't overwrite xterm -T title -n icon title by default.genomefreak@rlrmdrfreak
or the exact line under it , then the regular prompt.

i dont know where to stick the value for the PS1 because it seems no place will stick.

---

### Post by Zeike on 2010-06-18
> **Genomefreak said:**
> sorry for being inexact, 
when i put the code for the prompt right under the color prompt comment it says : #Commented out, don't overwrite xterm -T title -n icon title by default.genomefreak@rlrmdrfreak
or the exact line under it , then the regular prompt.

i dont know where to stick the value for the PS1 because it seems no place will stick.

It would probably be helpful if you posted your .bashrc, with the modified PS1 that you added.

---

### Post by Genomefreak on 2010-06-20
Here goes nothing

```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. see bash (1) for more options
export HISTCONTROL=ignoredumps
export HISTFILESIZE=300000    # save 300000 commands
export HISTSIZE=100000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1="\[\033[0;33m\][\!]\`if [[ \$? = "0" ]]; then echo "\\[\\033[32m\\]"; else echo "\\[\\033[31m\\]"; fi\`[\u.\h: \`if [[ `pwd|wc -c|tr -d " "` > 18 ]]; then echo "\\W"; else echo "\\w"; fi\`]\$\[\033[0m\] "; echo -ne "\033]0;`hostname -s`:`pwd`\007"'

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm-color)
#    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
#*)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#esac
# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found -o -x /usr/share/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
                elif [ -x /usr/share/command-not-found ]; then
		   /usr/bin/python /usr/share/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi
# mkdir, cd into it
mkcd () {
mkdir -p "$*"
cd "$*"
}

#My Alii
# For safety
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'

# convenience redefinitions
alias ..='cd ..'
alias ...='cd ...'
alias df="df -h"
alias h=history

## Keeping things organized
alias ls='ls --color=auto'
alias ll='ls -l'
alias la='ls -A'
alias mkdir='mkdir -p -v'
alias df='df -h'
alias du='du -h -c'

## Sudo fixes
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias removea='sudo apt-get autoremove'
alias orphand='sudo deborphan | xargs sudo apt-get -y remove --purge'
alias cleanup='sudo apt-get autoclean && sudo apt-get autoremove && sudo apt-get clean && sudo apt-get remove && orphand'
alias upgrade='sudo apt-get upgrade'
alias updatedb='sudo updatedb'

```

---

