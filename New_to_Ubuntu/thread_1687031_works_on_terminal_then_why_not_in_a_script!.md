---
title: "works on terminal then why not in a script!"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by unix-lover-2011 on 2011-02-13
here is what I really want to do.
df -kh look at desired mount point or logical partition if its more than threshold lets take 90% send email to unix administrator.

Simulation on home ubuntu env:

command works perfectly fine on terminal.
bazinga@ubuntu-desktop:~/Desktop/shellscripts$ df -kh | grep sda1 | awk '{print $5}'
58%

Here comes my script,
#!/bin/bash
set -x

a=df -kh | grep sda1 | awk '{print $5}'
echo ${a}
if [ ${a} -ge 50]; then
echo "Send RED ALERT email to Unix Administrator's"
else
echo "Do Nothing"
fi
set +x
**** Execution result*****

bazinga@ubuntu-desktop:~/Desktop/shellscripts$ ./ifstatement.sh 
+ grep sda1
+ awk '{print $5}'
+ a=df
+ -kh
./ifstatement.sh: line 4: -kh: command not found
+ echo

+ exit 0

I can't understand why the hell in script df -kh is not working!??

Kindly assist.

Thank you!

---

### Post by unix-lover-2011 on 2011-02-13
also any clue of how to get "number" instead of percentage format?
like 58 instead of 58%

Cheers!
bazinga!!

---

### Post by natex on 2011-02-13
To assign the output of a shell command as a variable. you'll need to enclose your shell command like this. 

a=$(df -kh | grep sda1 | awk '{print $5}')

More info here
[http://desk.stinkpot.org:8080/tricks/index.php/2007/01/assign-output-of-shell-command-to-variable-in-bash/](http://desk.stinkpot.org:8080/tricks/index.php/2007/01/assign-output-of-shell-command-to-variable-in-bash/)

And here
[http://tldp.org/LDP/abs/html/commandsub.html](http://tldp.org/LDP/abs/html/commandsub.html)

There are two ways you can do it. I believe the correct way is with $(*command*) because that form is easier to nest. Have fun!

natex

---

### Post by unix-lover-2011 on 2011-02-16
thanks natex it works and now i am looking how to seperate 55 from 55%

bazinga effect!

---

### Post by PunkLV on 2011-02-17
```
man cut
```
The dirty way
```
sed s/\%// *file*
```
Acceptable way. **s**ubstitute/regexp_what/regexp_with

---

### Post by Old *ix Geek on 2011-02-17
> **unix-lover-2011 said:**
> now i am looking how to seperate 55 from 55%
```
cut -b 1-2
```

---

### Post by tgm4883 on 2011-02-17
> **Old *ix Geek said:**
> ```
cut -b 1-2
```

that wouldn't work for 100% though would it?

---

### Post by Vaphell on 2011-02-17
another way to remove %:
```
a=16755%; a=${a%\%}; echo $a
```

---

### Post by Old *ix Geek on 2011-02-17
> **tgm4883 said:**
> that wouldn't work for 100% though would it?Yes and no. Literally, no, because it would strip off the ending 0. However, if the sysadmin received prior messages alerting them to 90, 95, 99% usage and then got one that said 10...they'd PROBABLY get the idea! :eek: (I know I would.)

---

