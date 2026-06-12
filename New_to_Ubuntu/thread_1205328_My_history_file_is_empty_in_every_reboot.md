---
title: "My history file is empty in every reboot"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by gjhames on 2009-07-05
My .bash_history file is empty every time I login.
My .bashrc is the same. Not edited. 
Thanks.

---

### Post by esalnoj on 2009-07-06
Be glad your .bash_history is cleaned after every reboot.

As long as you aren't using the same terminal commands over and over after every boot-up, you don't need that particular log file for the system to work.

Sorry if I like to go by memory.

---

### Post by gjhames on 2009-07-06
Wrong.
I need the history file for the reverse search.

---

### Post by Mornedhel on 2009-07-06
> **esalnoj said:**
> Be glad your .bash_history is cleaned after every reboot.

As long as you aren't using the same terminal commands over and over after every boot-up, you don't need that particular log file for the system to work.

Wha ?...

As the OP says, having a bash history persistent between sessions is, well, almost the whole point of having a bash history. It's much less useful if it's cleaned between boots. I suspect you don't use the command line much.

To the OP: Could you clarify something for me ?  Do you mean your .bashrc is empty ?  If so, I do believe the default configuration (from /etc/bash.bashrc) does not enable the history features.  I can post a .bashrc (mostly vanilla default) if you need one.

---

### Post by gjhames on 2009-07-06
Yeah. I didn't look at my /etc/bash.bashrc.
It's not the /home/me/bashrc that is empty. Is the .bash_history that is empty!!!!

---

### Post by Mornedhel on 2009-07-06
> **gjhames said:**
> Yeah. I didn't look at my /etc/bash.bashrc.
It's not the /home/me/bashrc that is empty. Is the .bash_history that is empty!!!!

OK, I just wanted to make sure, since your first post was kind of confusing. Could you post the contents of ~/.bashrc ?

---

### Post by gjhames on 2009-07-08
Thanks.
There is (/home/me/.bashrc):
```

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

if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

case "$TERM" in
    xterm-color) color_prompt=yes;;
esac


if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
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
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

#THIS THING I DID FOR SOLVE THIS PROBLEM, BUT NOTHING CHANGE
HISTSIZE=20000000
HISTFILESIZE=20000000

export HISTSIZE HISTFILESIZE


export EDITOR=vim



```



this one is the /etc/bash.bashrc


```
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

---

### Post by Mornedhel on 2009-07-08
It doesn't look bad to me.

The following lines are related to history control in your .bashrc :

```
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
export HISTCONTROL=ignoreboth
```

The first export is a hack around, apparently, mc's own history settings. Not to worry, since the second export overwrites the first. I have mine set to ignoreboth as well, so we can safely assume that this is not the problem.

```
# append to the history file, don't overwrite it
shopt -s histappend
```

Mmohkay, I don't have this, but it doesn't hurt. My own .bashrc is a bit tweaked.

Also, both snippets come from /etc/skel/.bashrc so they're sane defaults that should not prevent a history file from being created and used.

Try the following to help diagnosing the problem. Start a terminal, check the contents of the .bash_history file with tail ~/.bash_history, write a few commands (anything), check again if there's anything in there. If so, good, your history file can be written to and the problem is elsewhere. If not, try forcing a write with history -w, check again the contents. If still nothing, report here and we'll see where to go from there.

---

### Post by gjhames on 2009-07-08
My .bash_history is perfectly writable, as I said in the post, this file is empty every logon.

---

### Post by Mornedhel on 2009-07-08
Ok, so within a session the history mechanism works perfectly ?

This is worrying. Cleaning the history is sometimes done as part of an attack on your system. If your history is always cleaned it might be that your setup is compromised. After a few Google searches, this is what is most often associated with your exact symptoms (although a few users report having their history cleaned every so often, the ones that have their history cleaned every time are apparently advised to check for intrusions).

The last natural cause that I can think of is that somehow your session is started from a login shell and your .bash_logout is configured to clean history at every logout. This is not very likely, and I doubt that you'll find anything, but check .bash_logout anyway. The default .bash_logout should contain only the clear_console bit.

Otherwise, as a last ditch effort to prevent .bash_history from being removed (this won't work against even a simple history -c or catting /dev/null to the file, only simple rm's), you could set the file to append-only with sudo chattr +a .bash_history, although this will probably eventually conflict with the HISTFILESIZE limit.

---

### Post by Baltazar72 on 2012-05-22
Hi

Sorry for waking up an old tread, but googling my problem took me here, so this might help others.
I had a problem that my history was empty on start of new session. EG using the history cli command.

The problem I had was the hy historyfile somehow had become root:root ownership

```
sudo chown your_username:your_username /home/your_username/.bash_history
```

fixed my problem :)

---

