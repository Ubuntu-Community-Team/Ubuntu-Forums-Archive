---
title: "Terminal Terminology and Setting"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Jamessharpshooter on 2011-05-24
Hello, Its been a while since I've been here, and seeing this is a really simple question, I am asking it here. Also the beginner community may also like to learn about this 'whats-it-called' that im trying to find a name for.

K, so when I open up Terminal, it gives me a prompt. Cool. Now I use the Terminal a lot. When I say a lot, I mean A LOT.  I've always found it annoying that when I start the terminal and after I enter a command, it will make a new line with:
```
james@james-Aspire-1810TZ:~$ 
```
Currently, this is my user @ hostname:~$, Which makes my prompt look really cluttered.

So..

What is this called? 
Can I change it to something shorter like just my username? I would like to change it to something like this:
```
james:~$ 
```:D

Thanks,
James

---

### Post by rosencrantz on 2011-05-24
try this link:
[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)
You can make your changes permanent by appending the following to ~/.bashrc:
PS1=<whatever expression you figured out>
export PS1

PS1="\u:\w$ "
should do the trick for you...

---

### Post by bodhi.zazen on 2011-05-24
It is called the "PS1" and you can customize in it in .bashrc

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

export PS1="\u:\w$"

---

### Post by bodhi.zazen on 2011-05-24
> **rosencrantz said:**
> try this link:
[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)
You can make your changes permanent by appending the following to ~/.bashrc:
PS1=<whatever expression you figured out>
export PS1

It simplifies your file, IMO, it you export and define yoru variable on one line.

So rather then two lines

```
foo=bar
export foo
```

use one
```
export foo=bar
```

---

