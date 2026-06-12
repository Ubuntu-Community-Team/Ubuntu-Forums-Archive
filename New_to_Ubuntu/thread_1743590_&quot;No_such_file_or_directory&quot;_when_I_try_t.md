---
title: "&quot;No such file or directory&quot; when I try to go to desktop directory from root"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by BTXNick on 2011-04-29
Whenever I go ":cd /" and then I try to go back to "cd Desktop" or anywhere else it tells me there is no such file or directory. Why? Isn't cd / the main directory? This is really annoying. 

Thanks.


EDIT! Nvm, realized I have to go home then go to my directory. Interesting.

---

### Post by spiky001 on 2011-04-29
Just entering cd will get you back home. or```
 cd && cd Desktop
```

---

### Post by hakermania on 2011-04-29
Yeah, the Desktop directory is under '/home/$USERNAME' or simply '~'
The following will all guide you to your home directory:
1) Normal way: cd /home/username (which username is the username with which you login)
2) Other ways:
[B]a) cd
b) cd ~
c) cd /home/$USER
[/B]d) cd /home/$USERNAME
e) cd /home/$(logname)

The Bold ones work only if the user isn't root, while the others work in both occassion. I personally use d) inside my scripts and a) or b) in normal terminal use.

Also, don't forget that 'pwd' shows your current path!

---

### Post by sisco311 on 2011-04-29
> **hakermania said:**
> 

The Bold ones work only if the user isn't root, 

They work for root as well. ;)

Exactly how it's documented in the man page:
```
env LESS="$LESS +/^ +Tilde Expansion" man bash
```
```
env LESS="$LESS +/^ +cd " man bash
```

You might want to check out the differences between sudo's **-i** and **-s** option:
```
env LESS="$LESS +2/^ +-s " man sudo
```
```
env LESS="$LESS +/^ +-i " man sudo
```
and
[uhelp]community/RootSudo#Special notes on sudo and shells[/uhelp]

---

### Post by bodhi.zazen on 2011-04-29
> **hakermania said:**
> Yeah, the Desktop directory is under '/home/$USERNAME' or simply '~'
The following will all guide you to your home directory:
1) Normal way: cd /home/username (which username is the username with which you login)
2) Other ways:
[B]a) cd
b) cd ~
c) cd /home/$USER
[/B]d) cd /home/$USERNAME
e) cd /home/$(logname)

The Bold ones work only if the user isn't root, while the others work in both occassion. I personally use d) inside my scripts and a) or b) in normal terminal use.

Also, don't forget that 'pwd' shows your current path!

use $HOME rather then /home/$(USER,USERNAME,(logname)

:twisted:

Even better, use tab completion

~<tab>/Desk<tab>

You may need to add a little to the initial tab

~use<tab>/Desk<tab>

---

