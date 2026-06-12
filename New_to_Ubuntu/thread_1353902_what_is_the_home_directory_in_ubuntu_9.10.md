---
title: "what is the home directory in ubuntu 9.10"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by varun05 on 2009-12-13
hey cn nybody tell me what is a user's home directory in ubuntu 9.10
thnx in advance..:D
sry if this is too basic bt i hv an assignment that says give a terminal command to change ur dir to home directory.. i know dat cd command will b ysed bt hv no idea of d home directory..
PLSS HELP URGENTLY..

---

### Post by Joeb454 on 2009-12-13
It will be /home/username

Naturally replacing "username" with whatever that persons username is :)

---

### Post by CharlesA on 2009-12-13
Should be the same as 9.04. /home/$USER/

---

### Post by quinnten83 on 2009-12-13
the same as any other Linux distrib out there....
/home/user
/home/$user
~/$user
whateva!!

---

### Post by Physical Hook on 2009-12-13
> **quinnten83 said:**
> the same as any other Linux distrib out there....
/home/user
/home/$user
[COLOR=Red]~/$user[/COLOR]
whateva!!

[COLOR=Red]/home/user/user[/COLOR] ? 8-[

---

### Post by mikewhatever on 2009-12-13
Click Places and then the topmost link, the folder that opens is your home directory.

---

### Post by 3rdalbum on 2009-12-13
Firstly, I don't think the Ubuntu Forums people allow you to post your homework online for us to help you with.

It's a trick question. If you just type "cd" without any arguments, it goes to the user's home directory.

---

### Post by Iowan on 2009-12-13
"~" is a shortcut to the home directory. Easy way to get there is:```
cd ~ 
```Although, as **3rdalbum** pointed out, the "~" is not absolutely necessary. To get to a subdirectory, you could: ```
cd ~/subdirectory 
```

---

### Post by CharlesA on 2009-12-13
Would:
cd ~
pwd

work?

*hide*

---

### Post by bodhi.zazen on 2009-12-13
> **CharlesA said:**
> Would:
cd ~
pwd

work?

*hide*

all you need is cd , no need for ~ , default behavior is to cd to ~ is not argument is given.

---

### Post by chriswyatt on 2009-12-13
[http://www.lmgt4u.com/?q=home+directory+ubuntu](http://www.lmgt4u.com/?q=home+directory+ubuntu)

Sorry, just couldn't help myself ;)

---

### Post by theozzlives on 2009-12-13
> **bodhi.zazen said:**
> all you need is cd , no need for ~ , default behavior is to cd to ~ is not argument is given.

I didn't know you didn't need the tilde (~). That's cool.

---

### Post by cartisdm on 2009-12-13
> **varun05 said:**
> hey cn nybody tell me what is a user's home directory in ubuntu 9.10
thnx in advance..:D
sry if this is too basic bt i hv an assignment that says give a terminal command to change ur dir to home directory.. i know dat cd command will b ysed bt hv no idea of d home directory..
PLSS HELP URGENTLY..

Maybe you shouldn't be posting your computer homework and should spend some more time in your English class....

:D:D:D

---

### Post by CharlesA on 2009-12-13
> **bodhi.zazen said:**
> all you need is cd , no need for ~ , default behavior is to cd to ~ is not argument is given.

Is it that way on most distros?

---

### Post by chriswyatt on 2009-12-13
It's similar to 'cd %USERPROFILE%' in Windows.

---

### Post by bodhi.zazen on 2009-12-13
> **CharlesA said:**
> Is it that way on most distros?

It is that way in every distro I have tried.

---

### Post by spillin_dylan on 2009-12-13
> **bodhi.zazen said:**
> It is that way in every distro I have tried.

It is probably that way in most distros because that is part of the bash shell, right?  I think maybe a different shell (zsh, csh, dash, sh, etc) *might* treat the command differently, but even that's a stretch, because cd is such a common command.

---

### Post by bodhi.zazen on 2009-12-13
> **spillin_dylan said:**
> It is probably that way in most distros because that is part of the bash shell, right?  I think maybe a different shell (zsh, csh, dash, sh, etc) *might* treat the command differently, but even that's a stretch, because cd is such a common command.

see man cd

[http://linux.die.net/man/1/cd](http://linux.die.net/man/1/cd)

---

