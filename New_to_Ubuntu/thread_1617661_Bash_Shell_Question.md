---
title: "Bash Shell Question"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by andrew222 on 2010-11-09
OK, I am using PuTTY and not Ubuntu but I know this is a good forum to ask shell related questions....

Here is my question,  I am in the PuTTY shell terminal (Which is using bash shell) and I want to change directories to 
[COLOR="Red"]
/home/mydirectory[/COLOR]

So I type in [COLOR="Red"]cd /home/mydirectory [/COLOR]and nothing happens

However if I type in [COLOR="Red"]cd /home[/COLOR], I am now in that directory

[COLOR="Red"][andrew@alphaone home]$[/COLOR]

I will then type 'ls' and will see 'mydirectory' as one of the listed directories...

So I will then type in c[COLOR="Red"]d /mydirectory[/COLOR]

And then I will get this message


[COLOR="Red"]-bash: cd: /mydirectory: No such file or directory[/COLOR]

....But why is this directory listed when I type 'ls'??


Can someone tell me what I need to do to correct this?  I tried looking up the answer on Google but I can seem to find the right resources....

---

### Post by Glencore on 2010-11-09
Perhaps it is a case of incorrect case. GNU/Linux is case sensative. So to cd to Downloads you would have to type a capital D.

You can also type the first part of it and use tab completion (by pressing tab).

---

### Post by andrew222 on 2010-11-09
That was the issue...thanks very much for the reply

---

### Post by mcduck on 2010-11-09
> 
So I will then type in cd /mydirectory

And then I will get this message


-bash: cd: /mydirectory: No such file or directory

....But why is this directory listed when I type 'ls'??

at this point the problem is that you aren't trying to access a directory called "mydirectory" in your current location (/home/mydirectory), you are trying to access a directory called "mydirectory" directly under the root (/mydirectory).

Leave the slash away. It isn't something you add to the beginning of directory names, it really *means* the root of the filesystem.

---

