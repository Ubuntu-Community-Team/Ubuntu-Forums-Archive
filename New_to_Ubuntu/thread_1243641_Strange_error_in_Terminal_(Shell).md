---
title: "Strange error in Terminal (Shell)"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-08-18
I'm using the standard shell in ubuntu 9.04 and something wierd has happend, when I type 'exit' wont the command close the terminal the print I get is.

```

linux@ubuntu$:exit
exit

```

---

### Post by Bachstelze on 2009-08-18
Is that exactly what you're seeing? Your prompt looks weird.

---

### Post by SpinningAround on 2009-08-18
> **HymnToLife said:**
> Is that exactly what you're seeing? Your prompt looks weird.

this is exact

```

linux@linux-laptop:~$ exit
exit


```
Then will the shell continue to be open while I can not close it

---

### Post by kayvortex on 2009-08-18
What does
```
type exit
```
print?

Is there any output from:
```
locate -r 'bin.*exit'
```

Does pressing Ctrl-d cause the terminal to exit?

Also, can you tell me some more info about your system: did you make any changes to the shell or any config files (like .bashrc, .profile, /etc/bash.bashrc etc.)? Do you go to Applications -> Accessories -> Terminal to start a terminal? Does anything odd happen when you start a terminal, and do you do anything interesting between then and trying to exit?

---

### Post by SpinningAround on 2009-08-19
```

linux@linux-laptop:~$ type exit
exit is a shell builtin
linux@linux-laptop:~$ locate -r 'bin.*exit'
linux@linux-laptop:~$

```

I tried to use 'ctrl + d' and the only thing that happend was that 'exit' was auto typed then same as before. My system isn't anything special I haven't edited in config files or so, my computer is a Asus X51R

---

### Post by credobyte on 2009-08-19
```
sudo -i
exit

```

Does exit switch you back to the normal mode ( your username, not root ) ?

---

### Post by kayvortex on 2009-08-19
What does
```
echo $-
```
print out?

Could you also post the contents of the following files: "/etc/bash.bashrc", "/etc/profile", "~/.bashrc", and "~/.profile".

Can you log into a virtual console? Press Ctrl-Alt-F2 and try logging in and then enter "exit" to logout. (Press Ctrl-Alt-F7 to get back to your GUI at any time, even if you can't logout of a virtual console.)

What happens when you call bash itself within a bash session? Just type
```
bash
```
and see if you can exit from that.

---

### Post by SpinningAround on 2009-08-19
```

linux@linux-laptop:~$ sudo -i
root@linux-laptop:~# exit
logout
linux@linux-laptop:~$ exit
exit

```


```
linux@linux-laptop:~$ echo $-
himBH
linux@linux-laptop:~$ 

```

**"/etc/bash.bashrc"**
```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
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
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi
```
**"/etc/profile"**
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
    PS1='\u@\h:\w\$ '
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
```
**"~/.bashrc"**
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
export HISTCONTROL=ignoreboth

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

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

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

**"~/.profile"**
```
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
```

bash made things a bit wierd
```
linux@linux-laptop:~$ bash
linux@linux-laptop:~$ exit
exit
linux@linux-laptop:~$ 

```

I tested without GUI and when I then used exit was i logged out from my account so it looks like it's working there but not in gnome-terminal since it don't close and exit the shell

---

### Post by credobyte on 2009-08-19
Can you close it by pressing *Ctrl+D* ?

---

### Post by kayvortex on 2009-08-19
> bash made things a bit wierd
```

linux@linux-laptop:~$ bash
linux@linux-laptop:~$ exit
exit
linux@linux-laptop:~$

```


Yeah, it looks a bit weird, but the line after you entered bash is a prompt for a new instance of bash. You then exited from that OK and were returned to your first instance of bash (that the second one was running in). In short, it looks like bash is behaving fine and the problem may be with "gnome-terminal", like you said. Try entering the "gnome-terminal" command in a gnome terminal:
```
gnome-terminal
```
What should happen is that a new terminal should open up. See if you can exit that or if there are any messages spat out in the calling terminal.

The bash config files look OK to me; could you post the contents of "/usr/share/applications/gnome-terminal.desktop": I'll see if there's anything unusual in there (although I doubt it).

Can I just check to see if I understand your problem: you type in "exit" and the shell echoes it and then just hangs. Does pressing anything work (like Ctrl-c, Ctrl-z, Ctrl-d)?

---

### Post by kanikilu on 2009-08-19
Just curious, but can you check the following:

- Open gnome-terminal (Applications > Accessories > Terminal)
- Go to **Edit **> **Profile Preferences**
- Go the the **Title and Command** tab
- Make sure **When command exits** is set to **Exit the terminal** and not **Hold the terminal open**

---

### Post by kayvortex on 2009-08-19
Actually, could you (in the terminal window) click on "Edit" and then on "Profile Preferences". Then, go to the "Title and Command" tab and tell me what is selected under "When command exits:". It should be "Exit the terminal"; can you check to see if it's not "Hold the terminal open".

Edit: beat me to it, kanikilu!

---

### Post by SpinningAround on 2009-08-20
> **kanikilu said:**
> Just curious, but can you check the following:

- Open gnome-terminal (Applications > Accessories > Terminal)
- Go to **Edit **> **Profile Preferences**
- Go the the **Title and Command** tab
- Make sure **When command exits** is set to **Exit the terminal** and not **Hold the terminal open**

Thanks that finally solved it, but don't know how it was changed to begin with :confused:

Also thanks to everyone that has offered me help with this problem =D>:-D

---

