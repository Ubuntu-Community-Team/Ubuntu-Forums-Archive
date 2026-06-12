---
title: "copy and paste"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by alexeyhurricane on 2009-04-30
ok i got file to copy from desktop and paste in to /root/foldername/folder folder but it doesnt let me do it how can i do that!

---

### Post by SuperSonic4 on 2009-04-30
You would have to use sudo to become root but beware of doing stuff as root as it can screw the system. What is the file you're trying to copy? Perhaps it would be better off in your home directory

```
sudo !!
``` will run your last command as root

---

### Post by barbedsaber on 2009-04-30
> **SuperSonic4 said:**
> 
```
sudo !!
``` will run your last command as root

OMG thank you
that is awesome
I didn't know that
you are awesome
thank you.
(this will save me heaps of time and frustration after typing out a massive command)

---

### Post by johnwillis on 2009-04-30
> **SuperSonic4 said:**
> You would have to use sudo to become root but beware of doing stuff as root as it can screw the system. What is the file you're trying to copy? Perhaps it would be better off in your home directory

```
sudo !!
``` will run your last command as root

You can also run the graphical file manager as root using the command :

Press ALT+F2
Type "gksu nautilus"
Hit Enter
Type your root password

This is then a file manager with full permission...

**BE CAREFUL what you move/delete. It's ability can break your system... be careful...**

---

### Post by alexeyhurricane on 2009-04-30
thank you very much,

God bless!

---

### Post by lvleph on 2009-04-30
> **barbedsaber said:**
> OMG thank you
that is awesome
I didn't know that
you are awesome
thank you.
(this will save me heaps of time and frustration after typing out a massive command)

The TAB key is a wonderful thing.

---

### Post by halitech on 2009-04-30
> **SuperSonic4 said:**
> You would have to use sudo to become root but beware of doing stuff as root as it can screw the system. What is the file you're trying to copy? Perhaps it would be better off in your home directory

```
sudo !!
``` will run your last command as root

you should only use sudo when running commands in the terminal, if you want to run a graphical app then you should use gksu or gksudo as sudo can/will corrupt files when used to run graphical apps.

---

### Post by SuperSonic4 on 2009-04-30
> **barbedsaber said:**
> OMG thank you
that is awesome
I didn't know that
you are awesome
thank you.
(this will save me heaps of time and frustration after typing out a massive command)

You can also press up and then home to go to the start of the last command :p


Also, it's better to run gksu for graphical apps as has been said, my method assumes you're using the terminal and cp/mv

---

