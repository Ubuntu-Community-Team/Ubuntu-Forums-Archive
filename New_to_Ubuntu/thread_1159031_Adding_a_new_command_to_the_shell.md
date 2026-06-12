---
title: "Adding a new command to the shell"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by ierpe on 2009-05-14
There is probably threads already explaining this but I cant find any, so please redirect me if so...

So lets say I have a script shell in usr/share/app/mycommand.sh

How do I do to have mycommand accessible everywhere? I suppose I have to create a symbolic link, but where?

---

### Post by eldragon on 2009-05-14
> **ierpe said:**
> There is probably threads already explaining this but I cant find any, so please redirect me if so...

So lets say I have a script shell in usr/share/app/mycommand.sh

How do I do to have mycommand accessible everywhere? I suppose I have to create a symbolic link, but where?

you want to run it with a gui or through the shell?

if its through the shell, i would create an alias in ~/.bashrc

edit the file, and type somewhere near the already defined aliases:
```

alias mycommand='/usr/share/app/mycommand.sh'

```

---

### Post by ierpe on 2009-05-14
Thanks thats what I was looking for.

---

### Post by MrWES on 2009-05-14
> **ierpe said:**
> There is probably threads already explaining this but I cant find any, so please redirect me if so...

So lets say I have a script shell in usr/share/app/mycommand.sh

How do I do to have mycommand accessible everywhere? I suppose I have to create a symbolic link, but where?

What I did was make a directory in my home directory called bin; and I store all my scripts in there. You can add this path to your .bashrc; Alt + F2 then gedit .bashrc . Add the following statement, and edit to meet your needs:
```
PATH=$PATH:/home/bill/bin
```

Save and exit. Now open a terminal and type
```
source .bashrc
```

Now any executable scripts you put in your home /bin directory will execute accordingly.

Bill

---

