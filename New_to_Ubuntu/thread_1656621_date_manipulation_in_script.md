---
title: "date manipulation in script"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by jimwill on 2010-12-31
I know that it has to be something simple, but when I run the following in cli it works, but in a script it gives an error. What am I doing wrong?
> n=$(date --date="2 days ago")
echo day before yesterday $n
echo "*********************************"
echo $n
echo ${n:0:10}
x=${n:0:10}
echo $xthis works fine on the cli, but in a script -
> #!/bin/sh

n=$(date --date="2 days ago")
echo day before yesterday $n
echo "*********************************"
echo $n
echo ${n:0:10}
x=${n:0:10}
echo $xI get a "Bad substitution" error at the "echo ${n:0:10}" line.

This is a short test script that I'm trying to get to work to include into another script where I need the first 10 chars of each date for the previous 6 days as a variable.

---

### Post by Wtower on 2010-12-31
Ubuntu default user shell is bash. The substitution you specify is valid for bash only, and therefore you need to change the shebang to bash:

```
#!/bin/bash
```

---

### Post by jimwill on 2010-12-31
Ok!
Thanks!
I guess that means I had better check to see if my other script works in bash, don't want to mess up something that is already working!:p

I had a suspicion something like that was the problem, but wasn't sure!

At least it is a learning experience!!!!:lolflag:

Again - Thank you!

---

### Post by jimwill on 2010-12-31
As an add on to this question -
is it possible to change shell's mid script?
can I change from #!/bin/sh to #!/bin/bash and back inside a script or do I need to just create a seperate script that uses #!/bin/bash and run it from the #!/bin/sh script?
Or am I getting myself totally lost ??? :confused:

also, how do I mark this solved  -  or is that necessary?

---

### Post by Wtower on 2010-12-31
I'm glad it helped. Personally I prefer bash for a number of reasons like the one you described and for the regular expressions. And as I mentioned earlier, being the default (in /etc/passwd for each user), explains why it was valid as in the command line. And yes, please do mark the thread as solved! (It is a good practice.)

Happy New Year

---

