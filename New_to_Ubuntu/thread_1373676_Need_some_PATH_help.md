---
title: "Need some PATH help"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Diametric on 2010-01-06
Hi.  Does anyone know what the default PATH is upon installation?  And if so, how to get your path back to that via the terminal?  I began using the following command in an attempt, but it has only added extra directories that I do not need.

Here is the command I used:

PATH=$PATH:/home/myusername/bin

And what I got is:  /home/myusername/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/myusername/bin:/home/myusername/bin

When I type "echo $PATH"

I can't seem to get my path back to what it was....grrrr.

Cheers,
-Diametric

---

### Post by mvalviar on 2010-01-06
I'm not an expert, but a modified PATH reverts to it's default value when you end your session if I'm not mistaken.

---

### Post by Diametric on 2010-01-06
Nope, it has remained in a modified state.  I attempted to follow someone else's instructions and all that did was save what it was changed to.  Thus, I need to know how to get it back to where it is supposed to be

---

### Post by asmeetkumar on 2010-01-06
> **Diametric said:**
> Hi.  Does anyone know what the default PATH is upon installation?  And if so, how to get your path back to that via the terminal?  I began using the following command in an attempt, but it has only added extra directories that I do not need.

Here is the command I used:

PATH=$PATH:/home/myusername/bin

And what I got is:  /home/myusername/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/myusername/bin:/home/myusername/bin

When I type "echo $PATH"

I can't seem to get my path back to what it was....grrrr.

Cheers,
-Diametric

hi there
you still have the output of your command : /home/myusername/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/myusername/bin:/home/myusername/bin

and then you ask for your default path......

if this was the actual output of your command then you have your original path with you......

and that is : /home/myusername/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/myusername/bin

the effects of commands you've listed last only till the end of your current session. so if you want to get your original path back logout and login to your system again. that will reset it..

hth

---

