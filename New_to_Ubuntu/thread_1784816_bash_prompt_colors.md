---
title: "bash prompt colors"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by musendrophilus on 2011-06-17
When I use this line in bash, it sets the prompt display the way I want it to be shown in the terminal.

```

export PS1='\e[1;32m[\u@\h: \W \t]\$ \e[m'

```

I want this to be permanent. I've tried editing /etc/bash.bashrc then tried editing /etc/profile to no avail.

It's plain to me that I'm doing this in the wrong files despite using the information I've found at several tutorials. Where the heck do I place this line so the change is permanent?

---

### Post by Toz on 2011-06-17
It's probably being overwritten by the PS1 entry in the .bashrc file in your home directory. Try appending that line to the end of your ~/.bashrc file. Note that this file is in your home directory and hidden, so you'll have to turn on the display of hidden files to display it.

---

### Post by musendrophilus on 2011-06-17
Yay, thank you!

---

