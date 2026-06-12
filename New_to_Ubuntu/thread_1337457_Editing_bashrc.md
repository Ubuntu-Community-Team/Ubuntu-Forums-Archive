---
title: "Editing bashrc"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Xye on 2009-11-25
Hey.

I'm following a set of instructions for installing a program:

> if running bash or ksh (if in doubt type echo $SHELL), source the etc/bashrc file by adding the following line to the end of your $HOME/.bashrc file: 
. $HOME/OpenFOAM/OpenFOAM-1.6/etc/bashrc

Then update the environment variables by sourcing the $HOME/.bashrc file by typing in the terminal: 
. $HOME/.bashrc

But I cannot for the life of me work out how to even find let alone edit the bashrc file.

I am currently using Ubuntu 9.10 (64bit i think)

Thanks for your help.

---

### Post by wojox on 2009-11-25
Go to Places > Home Folder

Press Ctrl + H 

Scroll down to .bashrc

---

### Post by Xye on 2009-11-25
Ah ha! Thanks!

Hummm ok I've updated it.

Now when i open the terminal i get:

> bash: /home/xye/OpenFOAM-1.6.x/etc/bashrc: Permission denied

Do I need to log in as the Admin or something?

---

### Post by Charlietje on 2009-11-25
Did you try:
```
sudo nano .bashrc 
```

You will be asked to enter your password

---

### Post by Xye on 2009-11-25
Ok I put in the sudo nano .bashrc and its put it all out into the terminal screen.

I can see where i have added to it at the bottom. What do i do now?

---

### Post by ATL™ on 2009-11-25
ctrl+x to exit
y to save changes
enter to confirm file name

in that order.

---

### Post by Xye on 2009-11-25
> **ATL&#8482 said:**
> ctrl+x to exit
y to save changes
enter to confirm file name

in that order.

Ok that did nothing. Ctrl+x just exited it and i was typing y to the next terminal line.

---

### Post by Xye on 2009-11-25
Sorry my bad. it did do that when i changed it :$

but when i reopen the terminal after saving it it still give the same message.

[Edit] Is it affected by where i put it in the bashrc file? [/edit]

---

### Post by Xye on 2009-11-25
Does anyone know please?

---

