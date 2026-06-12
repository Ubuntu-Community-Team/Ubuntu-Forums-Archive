---
title: "Can you explain the prompt?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by dromichaetes on 2009-07-09
As I am trying to get more accustomed with the CLI I would very much appreciate if someone could explain me in noob words (if possible) this Chinese:

```

cristi@lappytop:~$ echo $PS1
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$

```

I know this is my prompt, but the variable $PS1 seems to be longer than what I would have expected:

```
\u@\h: #which means user@hostname:
```

---

### Post by LinuxFox on 2009-07-09
I don't know what you're trying to do and I never did try that, but I'll explain what I know about the command line.  The Terminal does all sorts of tasks for example "sudo" lets you do stuff that a root user can do, or "apt-get" installs a program from the repository.  It's also used to help compile programs from source.

I remember asking about the Terminal once, and someone linked me to a site that helps explain it.  It's [LinuxCommand.org]("http://linuxcommand.org/"), and it might be worth looking at.

I hope this information is useful.

---

### Post by nothingspecial on 2009-07-09
See [[COLOR="Red"]here[/COLOR]]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html")

---

### Post by Cheesemill on 2009-07-09
Check out the following documentation, it will teach you more than you ever thought possible about the bash prompt!!
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

Check out section 2.5 - Bash Prompt Escape Sequences

---

### Post by dromichaetes on 2009-07-09
> **LinuxFox said:**
> I don't know what you're trying to do and I never did try that, but I'll explain what I know about the command line.  The Terminal does all sorts of tasks for example "sudo" lets you do stuff that a root user can do, or "apt-get" installs a program from the repository.  It's also used to help compile programs from source.

I remember asking about the Terminal once, and someone linked me to a site that helps explain it.  It's [LinuxCommand.org]("http://linuxcommand.org/"), and it might be worth looking at.

I hope this information is useful.

Actually my question was more concrete :) . I do have learned quite a few things about the CLI, but I wanted a "down-to-earth" translation for the bash-language which stands for my $PS1, especially that is a bit longer than the standard. 

> nothingspecial 	 		**Re: Can you explain the prompt?**
 		See [[COLOR=Red]here[/COLOR]]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html") 

@nothingspecial, 
thanks for the link, but what the whole string stands for, and especially the highlighted one?

\[\e]0;\u@\h: \w\a\]$[COLOR=Blue]{debian_chroot:+($debian_chroot)}[/COLOR]\u@\h:\w\$

---

### Post by dromichaetes on 2009-07-09
> **Cheesemill said:**
> Check out the following documentation, it will teach you more than you ever thought possible about the bash prompt!!
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

Check out section 2.5 - Bash Prompt Escape Sequences

Cheesemill, for some reason I cannot open the webpage. It may be because of the Chinese government :) as it happens that I am in China right now... When I was documenting for this question I had already tried to open the page. When I am home it opens without a glitch, but now is a different story...

---

### Post by Mornedhel on 2009-07-09
> **dromichaetes said:**
> what the whole string stands for, and especially the highlighted one?

\[\e]0;\u@\h: \w\a\]$[COLOR=Blue]{debian_chroot:+($debian_chroot)}[/COLOR]\u@\h:\w\$

The part before the chroots is the escape sequence designed to set your terminal title (the window bar) to user@host:pwd. The chroot part is, *probably*, when you're in a chrooted environment, for the prompt to reflect the chrooted pwd, although I never chrooted anything and I am certainly not an expert on this. The last part is, like you've found out already, user@host:pwd.

---

### Post by dromichaetes on 2009-07-09
> **dromichaetes said:**
> 
@nothingspecial, 
thanks for the link, but what the whole string stands for, and especially the highlighted one?

\[\e]0;\u@\h: \w\a\]$[COLOR=Blue]{debian_chroot:+($debian_chroot)}[/COLOR]\u@\h:\w\$

Perhaps I wasn't clear enough. Let me put it this way: if my PS1 in /etc/profile is

```
PS1='\u@\h:\w\$ '
```

then why, when I type 

```
echo $PS1
```

I get the long string? The value of the variable $PS1 shouldn't be the onedefined by the /etc/profile?

---

### Post by Cheesemill on 2009-07-09
The value of your PS1 is defined in your ~/.bashrc file.

---

### Post by Mornedhel on 2009-07-09
> **Cheesemill said:**
> The value of your PS1 is defined in your ~/.bashrc file.

To be pedantic, the value of PS1 in .bashrc (user config) overrides the value of PS1 in /etc/profile or /etc/bash.bashrc (global config).

---

### Post by Cheesemill on 2009-07-09
> **Mornedhel said:**
> To be pedantic, the value of PS1 in .bashrc (user config) overrides the value of PS1 in /etc/profile or /etc/bash.bashrc (global config).

I know, I was trying to keep thing simple :)

---

### Post by dromichaetes on 2009-07-09
> **Mornedhel said:**
> The part before the chroots is the escape sequence designed to set your terminal title (the window bar) to user@host:pwd. The chroot part is, *probably*, when you're in a chrooted environment, for the prompt to reflect the chrooted pwd, although I never chrooted anything and I am certainly not an expert on this. The last part is, like you've found out already, user@host:pwd.

I definitely need to make sense out of this expansions. It makes sense what you said, but in the first part there are only 3 angular brackets, which kinda makes the second angular bracket misplaced?! I understand that the first and the third brackets are backslash-escaped, but what is then the meaning of the second bracket? 

```
\e]0;\
``` 

or am I completely wrong?

---

### Post by Cheesemill on 2009-07-09
```
 When  executing  interactively,  bash displays the primary
       prompt PS1 when it is ready to read  a  command,  and  the
       secondary  prompt PS2 when it needs more input to complete
       a command.  Bash allows these prompt strings  to  be  cus*
       tomized by inserting a number of backslash-escaped special
       characters that are decoded as follows:
              \a     an ASCII bell character (07)
              \d     the date  in  "Weekday  Month  Date"  format
                     (e.g., "Tue May 26")
              \e     an ASCII escape character (033)
              \h     the hostname up to the first `.'
              \H     the hostname
              \j     the  number of jobs currently managed by the
                     shell
              \l     the basename of the shell's terminal  device
                     name
              \n     newline
              \r     carriage return
              \s     the  name  of  the shell, the basename of $0
                     (the portion following the final slash)
              \t     the current time in 24-hour HH:MM:SS format
              \T     the current time in 12-hour HH:MM:SS format
              \@     the current time in 12-hour am/pm format
              \u     the username of the current user
              \v     the version of bash (e.g., 2.00)
              \V     the release of bash,  version  +  patchlevel
                     (e.g., 2.00.0)
              \w     the current working directory
              \W     the  basename  of the current working direc*
                     tory
              \!     the history number of this command
              \#     the command number of this command
              \$     if the effective UID is 0, a #, otherwise  a
                     $
              \nnn   the  character  corresponding  to  the octal
                     number nnn
              \\     a backslash
              \[     begin a sequence of non-printing characters,
                     which could be used to embed a terminal con*
                     trol sequence into the prompt
              \]     end a sequence of non-printing characters
```

From [http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html)

---

### Post by dromichaetes on 2009-07-09
> **Cheesemill said:**
> The value of your PS1 is defined in your ~/.bashrc file.

Here is my .bashrc. I assume the blue-highlighted passage gives the value of my $PS1:

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
[COLOR=Blue][B]case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac[/B][/COLOR]

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

--the rest is not relevant--
```

---

### Post by JKyleOKC on 2009-07-10
Absolutely correct. This redefines your PS1 variable to include the parts you've been questioning. As for why it's this way, I don't know; the answer is probably buried deep in the Debian policies, which seem to be more than a little bit confusing in their micro-management of obscure details...

---

