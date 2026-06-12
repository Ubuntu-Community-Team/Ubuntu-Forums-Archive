---
title: "What's wrong with the 'ls' function?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by kajman on 2009-05-18
As I remember it from Ubuntu 8.04, the ls function was more 'colorful'.
Scripts, directories, hidden files and so had their specific color.
Now when using Kubuntu 9.04, the ls function stays gray all the time.
I think this may be related with the console program that is used in KDE and it is different. Am I right? 

Any suggestions, to make it the same as it was earlier?

---

### Post by kajman on 2009-05-18
Well, I've installed htop a minute ago and it is in full color as it was earlier under Ubuntu 8.04/GNOME. So maybe I am wrong?

---

### Post by Celauran on 2009-05-18
Check that the following are present and uncommented in .bashrc
```
eval "`dircolors -b`"
alias ls='ls --color=auto'
```

---

### Post by vikkikanhaua on 2009-05-18
u have to make an alias of ls as "alias ls='ls --color=auto'"
(without double quotes) in your home .bashrc or any other file which holds your aliases.
then it will work

---

### Post by kajman on 2009-05-18
> **Celauran said:**
> Check that the following are present and uncommented in .bashrc
```
eval "`dircolors -b`"
alias ls='ls --color=auto'
```

I perfectly understand the second line, but what exactly does the first mean? 

Thanks to both you guys, I've learned something useful today :)

---

### Post by Celauran on 2009-05-18
[dircolors](http://linux.die.net/man/1/dircolors) is the program that defines the colours used by ls

---

### Post by kajman on 2009-05-18
Thanks.

---

