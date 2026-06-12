---
title: "What in the world terminal!!!????"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by constellanation on 2011-03-04
sorry a bit flustered have been trying to get some "easy" stuff done, and had to restart my computer in the middle of it, opened terminal and all I have is a blinking cursor...

I can type stuff, but that does nothing.

I tried a second restart, but still only a cursor in terminal...

please help, I was actually making progress...


and if anyone knows how to make adb in android recognize a nook color, could you be a chum... I've got it recognizing my n1... but not the color, atleast I don't think it is, I can't really check now.....

---

### Post by TeoBigusGeekus on 2011-03-05
What kind of terminal? Is it a grub prompt, an initramfs or a normal terminal one?
Can you post its whole prompt?

---

### Post by maqtanim on 2011-03-05
Is there anything written on the 'terminal'?? Any message?

---

### Post by dyltman on 2011-03-05
> **constellanation said:**
> sorry a bit flustered have been trying to get some "easy" stuff done, and had to restart my computer in the middle of it, opened terminal and all I have is a blinking cursor...

I can type stuff, but that does nothing.

I tried a second restart, but still only a cursor in terminal...

please help, I was actually making progress...


and if anyone knows how to make adb in android recognize a nook color, could you be a chum... I've got it recognizing my n1... but not the color, atleast I don't think it is, I can't really check now.....

My dad has been having a similar issue that he can't type in a prompt with a blinking cursor, it usually fixes itself by switching windows doing stuff that gives the terminal no focus -> focus.

Also just to be sure, you're running the terminal found in Applications -> Accessories -> Terminal right?

---

### Post by constellanation on 2011-03-05
Yeah it is the default terminal on a regular 10.10 install, when I open it there is only a blinking cursor.  I can type, but it does not recognize them as commands.  Very bizarre, because I had done all the recent updates, with a restart terminal worked.  Restarted again, because I needed a break to think, turned back on the problem started.


editing bash.rc wouldn't cause this would it? I did try to add something there.

> **TeoBigusGeekus said:**
> 
Can you post its whole prompt?

do you mean something special, or just what would normally be say "username@username$" because if that's what you mean, that's blank

---

### Post by fabricator4 on 2011-03-05
Try a console.  Hold down <ctrl> and <alt> and then press <F2>

This should get you to a console, exactly like terminal but full screen text.

Do <ctrl>+<alt> and press <F7> to get back to X.  Unless of course this is pooched too, but it should work.  In so many important respects those consoles (F1 through F6) ARE Linux, even if you never use them.

If consoles are OK, but the problem in terminal persists then you could try to uninstall (completely) gnome terminal and then re-install gnome-terminal with synaptic.

If it's the bash shell itself that has gone AWOL, I have no idea how to fix that one (but I'm sure we'll get suggestions)

Chris

---

### Post by AlphaLexman on 2011-03-05
> **constellanation said:**
> do you mean something special?
I think what TeoBigusGeekus means, and is looking for, is your prompt:```
>
```
That would indicate an unfinished built-in command.

---

### Post by constellanation on 2011-03-05
> **fabricator4 said:**
> Try a console.  Hold down <ctrl> and <alt> and then press <F2>

This should get you to a console, exactly like terminal but full screen text.

Do <ctrl>+<alt> and press <F7> to get back to X.  Unless of course this is pooched too, but it should work.  In so many important respects those consoles (F1 through F6) ARE Linux, even if you never use them.

If consoles are OK, but the problem in terminal persists then you could try to uninstall (completely) gnome terminal and then re-install gnome-terminal with synaptic.

If it's the bash shell itself that has gone AWOL, I have no idea how to fix that one (but I'm sure we'll get suggestions)

Chris

after doing that I got a log in screen and was able to log in!
I'll try the uninstall reinstall in just a second

> **AlphaLexman said:**
> I think what TeoBigusGeekus means, and is looking for, is your prompt:```
>
```
That would indicate an unfinished built-in command.

there's a screenshot of well my screen :)

edit: how would I uninstall gnome-terminal in synaptic it says it requires me to also remove gnome-desktop, I feel that may be important :)

---

### Post by jbiggs12 on 2011-03-05
Try entering in control-D; that should mark an end-of-file and potentially finish the input to whatever command you're running.

---

### Post by constellanation on 2011-03-05
> **jbiggs12 said:**
> Try entering in control-D; that should mark an end-of-file and potentially finish the input to whatever command you're running.

where would I enter that at?

---

### Post by jbiggs12 on 2011-03-05
> **constellanation said:**
> where would I enter that at?
When you open the terminal and you have the option to enter text, hit ctrl-d.

---

### Post by constellanation on 2011-03-05
> **jbiggs12 said:**
> When you open the terminal and you have the option to enter text, hit ctrl-d.

That's painfully obvious. I typed control -D about five times with different spacing and caps locks', unfortunately ctrl-D (the keypress) did nothing :(

is there anyway to edit my bash.rc file without terminal? If so, I could easily take out the two lines I added last night and see if that makes a difference.

---

### Post by fabricator4 on 2011-03-05
> **constellanation said:**
> 

edit: how would I uninstall gnome-terminal in synaptic it says it requires me to also remove gnome-desktop, I feel that may be important :)


Yes, very important I think.  OK Just try re-installing it instead.

Chris.

---

### Post by fabricator4 on 2011-03-05
> **constellanation said:**
> 
is there anyway to edit my bash.rc file without terminal? If so, I could easily take out the two lines I added last night and see if that makes a difference.

Yes, just use the console you logged into before:

```

sudo nano bash.rc 

```

Chris

---

### Post by constellanation on 2011-03-05
reinstallation of gnome-terminal hasn't seemed to change anything.

---

### Post by fabricator4 on 2011-03-05
> **constellanation said:**
> I typed control -D about five times with different spacing and caps locks', unfortunately ctrl-D (the keypress) did nothing :(


try <ctrl>c

---

### Post by constellanation on 2011-03-05
> **fabricator4 said:**
> try <ctrl>c

YOU ARE THE GENIUS!! What did I just do? and what did I do that that fixed!


Thank you and everyone else who helped you guys are one of many that make linux/ubuntu great!

---

### Post by fabricator4 on 2011-03-05
> **constellanation said:**
> YOU ARE THE GENIUS!! What did I just do? and what did I do that that fixed!


<ctrl>c generates a software interrupt that causes a program break.  Back in the days when a terminal was all you had I wouldn't have said "control c", I would have said "break".  ... and you would have known what I meant.


There was obviously some unfinished code that was looping, as AlphaLexman said.

Maybe the change you made in bash.rc?

Chris

---

### Post by constellanation on 2011-03-05
what's weird is I opened bash with nautilus, and couldn't see my changes.  So I did something wrong somewhere. which might explain why I couldn't get what I was trying to do to work! :P


But really I do appreciate it, thanks!
also thanks for the explanation too

---

### Post by anand warik on 2011-03-06
CTRL C halts the program. My problem is whenever i use man command i need to use CTRL Z to come back to the normal, but that way the processes get adding up. CTRL C doesn't seem to help me come out of man pages.

---

### Post by JKyleOKC on 2011-03-06
To exit from a man page, press 'q' and that should do it.

I've created a panel launcher for "xman" though so that I don't have to go into a terminal to view a man page. I use the command "xman -notopbox -pagesize 829x814-0-6" in the launcher to bring the page up in full width and without the initial tiny menu-like window. Makes it quite easy to check things out without getting in the way of whatever I may be trying to do in a terminal window!

---

### Post by fabricator4 on 2011-03-06
> **anand warik said:**
> CTRL C halts the program. My problem is whenever i use man command i need to use CTRL Z to come back to the normal, but that way the processes get adding up. CTRL C doesn't seem to help me come out of man pages.

In man press colon ":" and you will get a command line at the bottom of the screen, then just press 'q'

---

### Post by constellanation on 2011-03-06
I'm back, ha. 

So ctrl C gets my terminal to work, but everytime I open the terminal I still get the same blinking cursor (runnning process, I suppose screen) is there a way after hitting ctrl c, I can see what was running prior so that I can fix the actual problem?

---

### Post by AlphaLexman on 2011-03-06
Well **Ctrl-C** is only a short-term fix for your problem, it will '*break*' the command interpreter, i.e. the built-in command (I mentioned previously) that is looking for an exit code.

You probably have an unfinished opening statement such as; {case, do, for, if, read, (or) while}; without an [ending|closing] argument such as; {done, esac, (or) fi}.

Yeah, there are more openers than closers due to nesting statements. 

You should check the following files, in order:
[LIST]
[*]/etc/profile
[*]/etc/bash.bashrc
[*]~/.bash_profile
[*]~/.bash_login
[*]~/.profile
[*]~/.bashrc
[/LIST]
Don't worry if some of the files don't exist, not all of them are required. The most likely culprit is '~/.bashrc'.

**Source** each of the above individual files from a terminal by placing a dot "." and a space " " before each file and the /full/path/to/filename and post the results of ANY errors. EDIT: Or empty terminals.

EDIT #2: It is also possible you have an open quote, from a backtick [`], or a single quote ['], or a double quote ["].
Good luck.

---

### Post by anand warik on 2011-03-07
@JKyleOKC
Although this window is not similar to other GUI windows, since it doesn't allow to scroll. By clicking left and right mouse click scroll does take place only if mouse pointer is in the scroll bar. Space helps in scrolling only downwards. Is there keys.
Anyway it is better than CLI, since i can browse through the list.

Thanks

---

### Post by JKyleOKC on 2011-03-07
In my system, the mouse wheel works to scroll smoothly in both directions. Also, the "Getting Started" page that shows up when you launch xman has a list of the hotkeys that it recognizes.

I should have mentioned the non-usual action of the scroll bar, though!

---

### Post by constellanation on 2011-03-08
> **AlphaLexman said:**
> 
**Source** each of the above individual files from a terminal by placing a dot "." and a space " " before each file and the /full/path/to/filename and post the results of ANY errors. EDIT: Or empty terminals.

EDIT #2: It is also possible you have an open quote, from a backtick [`], or a single quote ['], or a double quote ["].
Good luck.


ok you lost me there, is that a command that will run them? or am I physically opening each of these files and looking for an error?  and I do agree it's probably in the bash file. Yet I don't see the changes I thought I had initially made?

---

### Post by milindo on 2011-03-10
[COLOR="Red"]Sorry for this, didn't see thread was solved. Can't delete this[/COLOR]

---

### Post by cgroza on 2011-03-10
> **anand warik said:**
> CTRL C halts the program. My problem is whenever i use man command i need to use CTRL Z to come back to the normal, but that way the processes get adding up. CTRL C doesn't seem to help me come out of man pages.
Q does.

---

### Post by AlphaLexman on 2011-03-11
> **constellanation said:**
> is that a command that will run them?Yes.
> **constellanation said:**
> or am I physically opening each of these files and looking for an error?No.

**First of all**,

You have made at least one reference to "**my bash file**" and at least two references to "**bash.rc**". We can only assume you mean the same file in each instance. However, **both of these are incorrect**, and is misleading to those who are willing to help you!

The open-ended command is most likely in one of these files:
> /etc/profile
/etc/bash.bashrc
~/.bash_profile
~/.bash_login
~/.profile
~/.bashrc

**Second of all**,

**NOTE:** There is not a file above named "**~/.my bash file**" or even "**~/.bash.rc**". However, that doesn't mean they don't exist or are not part of the problem. They may be invoked in any of the above files.

Let's start at what I think is the most obvious place, and where I think you are referring to with the your statements, the '**~/.bashrc**'. Let's clear some things up before we proceed...

As I stated previously, the usage of <**CTRL-C**> (break) is only a short-term fix and not a solution to your problem.

I may have erroneously over-estimated your understanding about 'sourcing' a file. I apologize, so we will skip that step for now.

**Most importantly**,

Please post the output (with code tags) from a terminal (after typing the <CTRL-C> thing!) of the following:
```
cat ~/.bashrc
```

What we are looking for is an open-ended builtin command; some examples are if, case, do, without a closing fi, esac, done. It could also be just an open quote mark.

---

### Post by constellanation on 2011-03-15
> **AlphaLexman said:**
> 
I may have erroneously over-estimated your understanding about 'sourcing' a file. I apologize, so we will skip that step for now.
.

Ha, definitely don't over-estimate my abilities :) I learn quick, but that's the extent of it.  Also thanks for your help, sorry for the slow reply, I've gotten tied up with work and family lately.

also sorry for the confusion over the misnaming of .bashrc :)

and on to the problem at hand

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

export PATH=${PATH}:~/android-sdk-linux_x86/platform-tools
source ~/.bashrc

```

the last line```
export PATH=${PATH}:~/android-sdk-linux_x86/platform-tools
source ~/.bashrc
```is the only thing I recognize as having edited.

EDIT: there is no closing fi after that line, I'm guessing that is my problem with terminal? Ironically I can delete that line altogether since I sold the nook color that I was trying to do the stuff for.

EDIT2: deleted that last line and saved the file, terminal now opens correctly.  Thanks again for your guidance and help!

---

