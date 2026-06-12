---
title: "Emacs Themes"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Jepic Phail on 2010-01-17
I am very new to emacs and I can't figure out how to change emacs theme. I can start emacs and open color-theme-select buffer, but this is about it. I don't know how apply themes (looks like I can only preview them?) and I don't know how to add new theme to the list. Any help would be appreciated.

---

### Post by Mornedhel on 2010-01-17
Add the following to your .emacs file (before the custom-set-variable part) :

```
(require 'color-theme)
(color-theme-initialize)
(color-theme-robin-hood)
```

Replace color-theme-robin-hood by the color theme of your choice. This should load the color theme library and apply a theme at startup.

To install other themes, download the .el file corresponding to the theme you wish to install, add it to your load-path or load it explicitly, after loading the color-theme library :

```
(load-file "path/to/new-color-theme.el")
(color-theme-new-theme)
```

---

### Post by Jepic Phail on 2010-01-17
Thanks for your help. I successfully applied the theme that I wanted. However, it looks like the new theme only works when I launch emacs in a separate window. If I try to run emacs in the terminal, the theme looks horrible. 

```
(require 'color-theme)
(setq color-theme-is-global t)
(load-file "/usr/share/emacs/site-lisp/emacs-goodies-el/chocolate-rain.el")
(color-theme-chocolate-rain)
```

---

### Post by Mornedhel on 2010-01-17
Anything you installed through Ubuntu's package facilities will already be added to your load-path, so you don't need to load it explicitly. (load-file "blah") is necessary only for files that you copy to your own home directory instead of installing them globally.

I see from your screenshot that you're running Emacs 22. If you have Jaunty Jackalope or Karmic Koala, Emacs 23 is in the repositories (Jaunty has it as emacs-snapshot and Karmic has it as emacs23 and emacs-snapshot). Emacs 23 has interesting new features, among others antialiased fonts even in the X version. Emacs 22 will have antialiased fonts only in the console version, and only thanks to the terminal emulator which takes care of it itself.

Finally, the color differences between the console and the X version most likely comes from the fact that your terminal does not think it can support enough colors. Fortunately, there is a workaround.

Install the ncurses-term package, which will bring additional terminal definitions, among which one with support for more colors :

```
sudo apt-get install ncurses-term
```

Edit your .bashrc file so that the beginning looks like this (the first export line is the important one) :

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# this provides 256 color support
export TERM=xterm-256color

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

```

Your terminal emulator should now be able to display a lot more colors. Hopefully this will solve your problem.

Edit: Attached is a screenshot from a maximized Emacs 23 X frame, and another frame in a terminal. Both share the same buffers.

---

### Post by Jepic Phail on 2010-01-17
As suggested, I upgraded to emacs 23 and it looks fantastic. However, even after ther upgrade and modifying my .bashrc, the terminal version of my emacs still looks terrible. Not quite sure what is causing this problem. 

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

# this provides 256 color support
export TERM=xterm-256color
```

---

### Post by jpkotta on 2010-01-18
Have you tried different terminal emulators (xterm, rxvt, rxvt-unicode, ...)?  It could be that the theme (chocolate-rain in this case) just doesn't work very well in a terminal; however it did look passable for all the terminals I tried.

---

### Post by Mornedhel on 2010-01-18
> **jpkotta said:**
> Have you tried different terminal emulators (xterm, rxvt, rxvt-unicode, ...)?  It could be that the theme (chocolate-rain in this case) just doesn't work very well in a terminal; however it did look passable for all the terminals I tried.

Did the light chocolate background work for you in xterm ? I'm running one in 256 colors right now, and it looks like the background color is more severely limited than the rest. I tried M-x set-background-color to the color specified by chocolate-rain and it gave me the same burgundish color as the OP's terminal. The rest of the colors are OK.

Jepic Phail: I suggest picking a different theme, or using it with a different background that will render better in a terminal, or if you feel like it change the background color depending on the type of session.

Can I ask why you need a terminal session anyway ?

---

### Post by Jepic Phail on 2010-01-18
I guess it's just my personal preferences. I have no particular reason why I need to run emacs in the terminal. Anyways, it feels like the problem has grown way in over my head. I will mark this thread as solved since I got the theme that I wanted to work. Thanks for all the help.

Update: 
I just disabled the tool and menu bar to make it looks its running from the terminal.

---

