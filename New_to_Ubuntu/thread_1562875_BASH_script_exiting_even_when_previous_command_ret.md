---
title: "BASH script exiting even when previous command returned exit code 0"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by CharlesA on 2010-08-28
Hi there,

I'm trying to streamline my script a bit, since it wasn't designed to fail if one of the commands returned an error.

I've tried a couple different things, but can't seem to figure out why it's not working the way I think it should be working.

```
#!/bin/bash

HOME=/home/charles
LOG=$HOME/messages.log
ERR=$HOME/error.log

echo -e "Installing Samba... \c"
apt-get install samba --assume-yes  1>> $LOG 2>> $ERR || exit
echo -e "\t\t\t\t\t\t\tDone!"

```

This works perfectly, but doesn't display an error message. I want to echo a specific message to the screen, if the command fails.

Anyway, if I use something like this:

```
apt-get install samba --assume-yes  1>> $LOG 2>> $ERR || echo "Samba failed to install."; exit
```

Or this:

```
apt-get install samba --assume-yes  1>> $LOG 2>> $ERR || echo "Samba failed to install." && exit
```

The script stops even if apt-get returned an exit code of 0, and I don't know why.

Any ideas?

Thanks.

---

### Post by zpletan on 2010-08-28
Ah yes - I love bash.  :)

> **CharlesA said:**
> ```
apt-get install samba --assume-yes  1>> $LOG 2>> $ERR || echo "Samba failed to install."; exit
```
This will do:
> If apt-get install samba fails, then echo string
> Exit, regardless of anything.
Semicolons are like newlines - they delimit commands

> **CharlesA said:**
> ```
apt-get install samba --assume-yes  1>> $LOG 2>> $ERR || echo "Samba failed to install." && exit
```
This will do:
> If apt-get install samba fails, then echo string
> Else if apt-get install samba succeeds then exit
The || and && things (don't remember exact term :D) operate on the first command in the sequence

It looks like you need to use parentheses, like so:
```
apt-get install samba --assume-yes 1>>$LOG 2>>$ERR || (echo "Samba failed to install." ; exit)
```
Parentheses make a "mini script" that bash sees as one command, no matter how many commands are actually in it.

---

### Post by CharlesA on 2010-08-28
Thank you!

Funny how in all my googling, I didn't find anything that talked about using Paranthasis.

---

### Post by Vaphell on 2010-08-28
a || b && c is all about calculating the boolean value of the expression. It is calculated from left to right as || and && are of equal strength.

a || b - a=true is enough to evaluate, b skipped (TRUE || DONTCARE = TRUE)
a && b - a=false is enough to evaluate, b skipped (FALSE && DONTCARE = FALSE)
a || b && c has to evaluate all 3 parts bacause the value of the whole depends on the value of the last part (c). for a||b=true you get true && true = true but true && false = false. That's why you want to group stuff with parentheses to change the order of operators in expression they are calculated with

---

### Post by CharlesA on 2010-08-28
Thanks to both of you. It looks like I needed to group the command with "{ }" instead of "( )" since using parenthasis start it as a subshell and exit that subshell, but not the current script.

Thanks again!

Reference: [http://www.gnu.org/software/bash/manual/bashref.html#Command-Grouping](http://www.gnu.org/software/bash/manual/bashref.html#Command-Grouping)

---

