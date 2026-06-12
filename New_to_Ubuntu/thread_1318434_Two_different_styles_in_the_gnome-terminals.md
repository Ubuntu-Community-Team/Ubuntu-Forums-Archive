---
title: "Two different styles in the gnome-terminals"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-11-07
The following is what is in my .bashrc file:

```

#.bashrc

#function prompt
#{
#local WHITE="\[\033[1;37m\]"
#local GREEN="\[\033[0;32m\]"
#local CYAN="\[\033[0;36m\]"
#local GRAY="\[\033[0;37m\]"
#local BLUE="\[\033[0;34m\]"
#local RED="\[\033[0;31m\]"
#local YELLOW="\[\033[1;33m\]"
#export PS1="
#${WHITE}[\t]
#${YELLOW}$PWD
#${GREEN}$ "
#}
#prompt


PS1='
\[\033[1;37m\][\t]
\e[1;33m$(pwd) \e[1;32m\n\$ '

alias ll="ls -l"
alias la="ls -A"
alias l="ls -CF"

```

The top portion has all the configurations for the terminal and the bottom has a few aliases. Screenshot: "Terminal" shows what the terminal looks like when I click on Accessories>Terminal

Now, I have also installed the "nautilus-open-terminal" package and this adds an "Open in Terminal" button to the nautilus context menu allowing you to open a terminal pointed at the current folder. When I do this I see a terminal that has a completely different style to the screenshot of "Terminal". See, screenshot: "Open-Terminal".

I have had these settings since about Fiesty Fawn without any problems. Why are there two different styles to the terminals now?

Thanks!

---

### Post by ikisham on 2009-11-08
Maybe nautilus has its own config settings for terminals. If you find them then you may be able to edit them as you did with .bashrc.

---

### Post by abhiroopb on 2009-11-08
Any idea where those settings may be?

Whats striking is that I have been upgrading (with clean installs) since Fiesty and I always just copy over my .bashrc files into the new install. This has never happened before.

---

### Post by ikisham on 2009-11-08
Well, it was a guess.
You could examine your home folder and its hidden directories and files. Like my .nautilus folder is empty so if there's something on yours that may mean something. Also check if there are is something in .config or anything related to "nautilus-open-terminal" or .gnome2/nautilus-scripts (but I suspect not).

Otherwise you may even stumble on something when you start using it.

Hope it helps.

---

### Post by abhiroopb on 2009-11-22
Tried checking all the folders/files you suggested. Also checked gconf-editor. Doesn't seem to be any option to change the profile and link it with my .bashrc. 

The inconsistency is quite annoying. :(

---

