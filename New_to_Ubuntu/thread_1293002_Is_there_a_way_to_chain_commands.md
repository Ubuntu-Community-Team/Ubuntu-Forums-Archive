---
title: "Is there a way to chain commands?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by Amablue on 2009-10-16
For example, most of the time when I change directories on the command like with cd I want to immediatly follow it with ls so I can see what I'm working with. Is there a way to make it so that executing the command cl mydir/, for example,  would do execute cd mydir and then ls?

---

### Post by zerhacke on 2009-10-16
Put a ; (semicolon) between commands.

cd mydir ; ls

---

### Post by Fire_Chief on 2009-10-16
You can use the && notation to chain commands if you like such as```
cd mydir && ls && chown root.root filename
```

---

### Post by tom4everitt on 2009-10-16
You can also write your own script:

```

cd /usr/bin
sudo emacs cl

```

Add something like this to the file:

```
#!/bin/bash

cd $1  # $1 refers to the first argument given to your script.
ls

exit 0
```

Then you give everyone permission to run it: 

```

sudo chmod 777 cl
```

Since it is stored in the /usr/bin, it will automatically be activated once you type it in the terminal. Hence, you can use it just the way you described, i.e:

```

cl name-of-dir
```


EDIT: This tip is essentially useless. Running cd inside the script won't have any effect outside the script (in the terminal). But there are a lot of other fun stuff to do with scripting :) (just google "bash scripting tutorial" if you wanna know more.)

---

### Post by nothingspecial on 2009-10-16
From your question - why not ```
ls /directory/you/want/to/be/in/
```

eg ```
ls /media/disk/music/
```

---

### Post by Amablue on 2009-10-16
> **nothingspecial said:**
> From your question - why not ```
ls /directory/you/want/to/be/in/
```

eg ```
ls /media/disk/music/
```

I often want to change my working directory and immediately see what's in there, and I like to save myself those two or three keystroke :P

---

### Post by prshah on 2009-10-16
> **Amablue said:**
> I often want to change my working directory and immediately see what's in there, and I like to save myself those two or three keystroke :P

Spoken like a true power user.

---

### Post by sisco311 on 2009-10-16
you can use a bash function:
```
function xs() { cd $@ && ls; }
```
add the line to the ~/.bashrc file.

```
xs path/to/dir
```

EDIT2:

you can define an alias:
```
alias cd="xs"
```

---

### Post by bodhi.zazen on 2009-10-16
There are several ways to string commands.

command1; command2

runs command 1 then command2

And:
command1 && command2

command 2 only runs if command 1 is successful

Or
command1 || command2

command 2 runs if command 1 fails


command1 | command2
pipes the output of command 1 to command2

etc, etc ...

---

### Post by Amablue on 2009-10-16
> **sisco311 said:**
> you can use a bash function:
```
function xs() { cd $@ && ls; }
```
add the line to the ~/.bashrc file.

```
xs path/to/dir
```

EDIT2:

you can define an alias:
```
alias cd="xs"
```

Thanks, this is what I was looking for :D

---

### Post by ackley on 2009-10-16
I never knew about adding a semicolin after a command. I've always used "&&". Now I can save TWO whole keystrokes! :D

---

### Post by clockworkpc on 2010-08-25
Thanks for the tips, everyone.

Here is an example of chained commands giving me the desktop-audio-and-webcam recording that I always wanted in Ubuntu.

[http://www.youtube.com/watch?v=KmlO0iUQp4Q](http://www.youtube.com/watch?v=KmlO0iUQp4Q)

---

