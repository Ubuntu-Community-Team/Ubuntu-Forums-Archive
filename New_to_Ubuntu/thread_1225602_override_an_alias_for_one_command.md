---
title: "override an alias for one command"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by PGScooter on 2009-07-28
Hi, I have aliases set in my .bashrc. They work great, but sometimes I want to use the original command. The command is not a builtin command so I can't use the ```
builtin
``` command.

How can I do this? I looked in man bash under aliases but I couldn't find anything.

Thanks

---

### Post by kerry_s on 2009-07-28
that does not make sense. 

an alias is just that, you can have as many as you want.

this is what i picture:

alias 1='your-command'
alias 2='your-other-command'

don't be cryptic, just tell us the exact command your using & the command you want to run.

---

### Post by llamabr on 2009-07-28
What exactly is the command?

It sounds like you used an alias to rename an app, like this

```
ls="alias ls | more"
```

I think that would work, but then you don't have access to plain ls.  Instead, call it something unique, like:

```
lsm="alias ls | more"
```

Which would solve your problem.  

If that's not it, though, just post your actual alias, and we'll fix it.

---

### Post by kerry_s on 2009-07-28
> **llamabr said:**
> What exactly is the command?

It sounds like you used an alias to rename an app, like this

```
ls="alias ls | more"
```

I think that would work, but then you don't have access to plain ls.  Instead, call it something unique, like:

```
lsm="alias ls | more"
```

Which would solve your problem.  

If that's not it, though, just post your actual alias, and we'll fix it.


i bet thats exactly what he did.

OP: an alias is suppose to be something you can remember or just something short to save you typing, for example heres mine:

```

alias !='sudo'
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install' 
alias r='sudo apt-get remove --purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get clean'
alias ch='clear;rm ~/.bash_history;history -c'
alias grep='grep --color'
alias less='most'
alias more='most'

```

---

### Post by PGScooter on 2009-07-28
Sorry, I should have been more specific. The alias is ```
vlc='/home/fredrick/temp/vlc-1.0.0/vlc'
```.

I then installed 1.0.1 from the ppa and wanted to run the new version instead of the one that I built. I thought that there was a way to override an alias by enclosing the command in double quotes, single quotes, or prefixing or appending a symbol. It looks like I'm wrong. I guess the best way is to do as you guys have suggested and make the alias name different from the command name.

---

### Post by llamabr on 2009-07-28
Ah, you also did exactly what I describe:

```
alias grep='grep --color'
```

For you, it will be impossible to use grep without color.  If you wanted that, you could use:

```
alias grepc="grep --color"
```

Though your way works when you'll never want it without.  I believe ubuntu comes with a few aliases to help save us from ourselves, such as:

```
alias rm="rm -i"
```

---

### Post by kerry_s on 2009-07-28
> **PGScooter said:**
> Sorry, I should have been more specific. The alias is ```
vlc='/home/fredrick/temp/vlc-1.0.0/vlc'
```.

I then installed 1.0.1 from the ppa and wanted to run the new version instead of the one that I built. I thought that there was a way to override an alias by enclosing the command in double quotes, single quotes, or prefixing or appending a symbol. It looks like I'm wrong. I guess the best way is to do as you guys have suggested and make the alias name different from the command name.

yeah just alias it to something else "vlc2"


> Ah, you also did exactly what I describe:

that's intentional i don't want it to use plain "grep", as for "less" i changed to using "most", but i often forget that i uninstalled less, same applies for "more". :D

---

### Post by benj1 on 2009-07-28
a backslash before a command will override an alias

so if you had an alias

alias rm='rm -i'

'rm' would ask for confirmation
'\rm' would invoke the default rm

this is also useful for swapping commands
eg 
alias ls='rm'
alias rm='\ls'

or one that is actually useful

alias emacs='emacs -nw'
alias xemacs='\emacs'


but to be honest if you want to use the new vlc long term just remove the alias form your .bashrc

---

### Post by PGScooter on 2009-07-28
benj1,

That's exactly what I was looking for! Thank you.

I will heed your warning. I only intend to use it on a short-term basis for one-case exceptions when I am feeling lazy :)

Thanks for all of the replies. I have learned some nifty aliases from this thread.

---

