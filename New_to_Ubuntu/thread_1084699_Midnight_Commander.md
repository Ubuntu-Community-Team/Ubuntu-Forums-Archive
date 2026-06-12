---
title: "Midnight Commander"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by darwall on 2009-03-02
Hi all!
Anyone who are familiar with mc ? (Midnight Commander)
I can't get mc to remember the path in Ubuntu.
( in Fedora there is no such problem)
Sometimes I use mc to change directory. Instead of typing long directory names, I use mc to switch to the directory where I wanted to work. 
But with Ubuntu it always change back to my home directory when I close mc. And then I have to type the long directory names again.
I tried to copy the ~/.mc/ini file from a Fedora computer to an Ubuntu computer but it didn't help.
Would appreciate a good idea very much.

Sven Darwall

---

### Post by kellemes on 2009-03-02
Is Ctrl-o an alternative you can live with?

[The -P option]("http://www.chm.tu-dresden.de/edv/mc/mc4.5/manual1.html#3") seems to be the better solution.. It doesn't seem to function for me but maybe you've better luck.

---

### Post by brian_p on 2009-03-02
> **kellemes said:**
> 

The -P option seems to be the better solution..

It is.

> It doesn't seem to function for me but maybe you've better luck.

```
alias mc='. /usr/share/mc/bin/mc-wrapper.sh'
```

---

### Post by kellemes on 2009-03-02
```
alias mc='. /usr/share/mc/bin/mc-wrapper.sh'
```

Thanks, it works fine indeed.

---

### Post by darwall on 2009-03-04
Hello kellemes!
How do you use the code "alias mc='. /usr/share/mc/bin/mc-wrapper.sh'"?
Do you write it in your ~/.bashrc?
I found a file with exactly the same contence, "/usr/share/mc/bin/mc.sh"
The CTRL-o option is working, it seems to hide mc, and next time I press CTRL-o, mc comes back again. But I prefer to be able to close mc without changing the path.  Thanks!!!  Sven Darwall

---

### Post by brian_p on 2009-03-04
> **darwall said:**
> 

How do you use the code "alias mc='. /usr/share/mc/bin/mc-wrapper.sh'"?
Do you write it in your ~/.bashrc?

Yes. Log out. Log in. Then

```
mc
```

> I found a file with exactly the same contence, "/usr/share/mc/bin/mc.sh"

mc-wrapper.sh is what you want.

---

### Post by darwall on 2009-03-04
THANKS Brian and kellemes!! Now it works just the way I wanted it to.
Sven Darwall :D

---

