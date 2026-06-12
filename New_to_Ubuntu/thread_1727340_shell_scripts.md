---
title: "shell scripts"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by sreaney89 on 2011-04-12
hi guys i am a student, 

i need help with this script;

.....

SIZE=`du -ls`

if [ $SIZE -k -gt 100 ];
then echo "You have used more than 100k of disk space"
else echo "You have not used more than 100k of disk space"
fi

.....

im running it in the bourne shell, but i keep getting this error.. 
[: 6: 1892: unexpected operator

basically what i have to do is displaye a message about disk space if there is more than 100k free and  if there is not..

regards

Stefan

---

### Post by safarin on 2011-04-12
hi sreaney89,

I think you use the wrong options/arguments
I get this error when trying it in my shell.
You can check it.

```
du: invalid option -- 'g'
du: invalid option -- 't'
Try `du --help' for more information.
```

---

### Post by sreaney89 on 2011-04-12
hmm strange, i dont seem to get that.. what i am trying to do however is check that, using a simple command, if there is 100k space free..

Can you offer any help?

note this is a script.. im running it from an executable file

---

### Post by f1tz on 2011-04-12
Hmm... if you type "du -s", you end up with a "." a few characters away. Cut this out with sed or something. Try this:

```
#!/bin/sh
SIZE=$(du -s | sed 's/\.//')
if [ $SIZE -gt 100 ];then
echo "You have used more than 100k of disk space"
else 
echo "You have not used more than 100k of disk space"
fi
```

---

### Post by safarin on 2011-04-12
> **sreaney89 said:**
> hmm strange, i dont seem to get that.. what i am trying to do however is check that, using a simple command, if there is 100k space free..

Can you offer any help?

note this is a script.. im running it from an executable file

If I not mistaken..
$SIZE -k -gt 100 is equal to 

```
$ du -ls -k -gt 100
``` when you type in the terminal, so this is how I get this error. Try 

```
$ man du
```
you can see the available option and argument there. 

I don't know what -k -gt 100 for.. maybe you could make it clear. 
I never use du command. First time I see it.. :D but I think you should compare the result ($SIZE) with that 100k of space.

for this line.. I don't see any comparison.. $SIZE -k -gt 100 

P.S: I also just learned scripts myself.. so maybe I got wrong.. If I could help, I will help. :P

---

### Post by rosencrantz on 2011-04-12
is -gt the 'greater than' operation for the if clause? It seems to get interpreted as another option for du.
Also, du doesn't display free space (that's df), only used space.

---

### Post by hakermania on 2011-04-12
Guys, the problem is that the output of du -ls has a dot in the corner, so, it is not a number, it is a string!
Also, prefer $() intead of ``

---

### Post by safarin on 2011-04-12
Ahhh.. It's has dot(.) at the end of the numbers. Hahaha...
@rosencrantz : thank you rosencrantz for giving me info about -gt

---

### Post by hakermania on 2011-04-12
[f1tz]("http://ubuntuforums.org/member.php?u=1275847") has given a solution for the dot, please try it

---

### Post by sreaney89 on 2011-04-12
yea its greater than for the if clause and yea i thought it was interpreted as a string myself.. didnt know how to fix it. Anyway that seems to work, need to test it a bit more, sorry for the confusion it was the used space that i needed

---

### Post by 5149.5 on 2011-04-12
This will work better. The -k switch belongs with the ls command.


```
SIZE=`du -lsk`

if [ $SIZE -gt 100 ];
then echo "You have used more than 100k of disk space"
else echo "You have not used more than 100k of disk space"
fi
```

---

### Post by safarin on 2011-04-12
> **sreaney89 said:**
> yea its greater than for the if clause and yea i thought it was interpreted as a string myself.. didnt know how to fix it. Anyway that seems to work, need to test it a bit more, sorry for the confusion it was the used space that i needed

I just found a good link.. maybe you could also learn from this link..

[http://www.cyberciti.biz/tips/shell-script-to-watch-the-disk-space.html]("http://www.cyberciti.biz/tips/shell-script-to-watch-the-disk-space.html")

---

### Post by hakermania on 2011-04-12
> **5149.5 said:**
> This will work better. The -k switch belongs with the ls command.


```
SIZE=`du -lsk`

if [ $SIZE -gt 100 ];
then echo "You have used more than 100k of disk space"
else echo "You have not used more than 100k of disk space"
fi
```

No, no no!
Don't confuse the asker please, and read the previous posts!
There is a dot (.) after the number, and that causes $SIZE to be a string!

---

### Post by 5149.5 on 2011-04-12
Got it. I missed the decimal point and jumped the gun.

---

### Post by sisco311 on 2011-04-12
In bash you could use an array:
```

#!/bin/bash

du=( $(du -ls) )
if (( du[0] > 100 ))
then
   echo
else
   echo
fi
```

---

### Post by DaithiF on 2011-04-14
or cut:
SIZE=$(du -ls | cut -f1)

---

