---
title: "alias command in login script"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by bunburya on 2009-11-14
Hi all,

I am running Kubuntu 9.10 on my laptop. I'm pretty much computer illiterate so I'm trying to educate myself a little on the workings of the OS. I'm taking a look at the tutorial at [www.linuxcommand.org](www.linuxcommand.org) because I like the way it is written.

Basically I am here : [http://www.linuxcommand.org/wss0020.php](http://www.linuxcommand.org/wss0020.php), I am being told to put the line **alias l='ls -l'** in my .bash_profile file so that it will be implemented on login. In my $HOME directory, however, I do not have a .bash_profile file, rather I have a .profile file instead. I assumed it did the same thing. So I put the aforementioned alias line in .profile, logged out, logged in again, tried the command **l** in Yakuake (I'm running a graphical interface and doing all this through Yakuake, dunno if that's relevant) and got nothing. If I simply type **alias l='ls -l'** into Yakuake then it works but it does not seem to be executing that line at login.

Can anyone tell me what I am doing wrong or how to get it to execute that line at login? Thank you in advance.

By the way my .profile as edited reads as follows:
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

alias l='ls -l'

```

---

### Post by impert on 2009-11-14
If you have a .bashrc you can put it there, I think.

---

### Post by cariboo on 2009-11-14
The aliases can go in either /etc/bash.bashrc, or /etc/skel/.bashrc

---

### Post by bowlesling on 2009-11-23
@bunburya--

I've been playing with similar stuff from the tutorial. From what I've gathered, the absolute best thing is to read the bash man (the manual) --- of course this is recommended for anything. Beside that, there is some useful info if you read the comments in your .bashrc and .profile . 

What is suggested in those comments is to create .bash_aliases through your text editor (I use mainly emacs, and also TeXmacs and gedit) for all your aliases---though they will work in .bashrc. In fact, if you read in your .bashrc you will see a place for defining aliases:

> 
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable color support of ls and also add handy aliases
#if [ -x /usr/bin/dircolors ]; then
 #   eval "`dircolors -b`"
  #  alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
#fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
 

 I have commented out all that stuff (putting a # at each line), and copied it over to .bash_aliases ($HOME/.bash_aliases) leaving the color definitions for* ls* active. Notice also, that .bashrc actually suggests using **alias ll='ls -l' **(I think the tutorial is just using the *alias l='ls -l' *as an example, not as a suggestion for a useful alias).

As far as .bash_profile works: bash will read some files first --- .bash_profile and .bash_login will the be the first consecutively --- and even though I've seen recommendations for having .bash_profile I can't seem to get it to work very well... and it seems like you'd have to re-define more PATHs than you would if you used .bashrc and .bash_aliases (NOTICE IN THE ABOVE, THAT .bash_aliases $PATH  IS ALREADY GIVEN FOR YOU, YOU JUST NEED TO CREATE THE FILE).  

Here is the comment in .profile, with the $PATH shown for .bashrc:
>  
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



Even when I tried working with .bash_profile, it didn't pass over .bashrc --- I chalk this up to me not being able to do it right. Long story short... I read about some problems using .bash_profile... but using .bashrc and creating .bash_aliases has not given me any trouble... and it seems like .bashrc and .profile are encouraging this method.

Lastly, in .bashrc I have the path for shell scripts in my newly created $HOME/bin directory: 

#path for shell scripts on start up
export PATH=$PATH:$HOME/bin

There is also a path defined for $HOME/bin in .profile:

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

But I took this out because my scripts in $HOME/bin ran fine with the path defined in .bashrc (I think either way will work, I'm not sure then benefits of one over the other i.e., *export* command over* if ... then ... fi*). Maybe I'll re-define the $PATH in my .bashrc as an *if *and see what happens... I suspect it will work just as well.

Hope this helps.

---

