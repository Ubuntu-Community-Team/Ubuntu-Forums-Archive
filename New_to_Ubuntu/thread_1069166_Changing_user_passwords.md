---
title: "Changing user passwords"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by zyban03 on 2009-02-13
In a nutshell
I am trying to change a list of users passwords with a bash script. This link ([http://www.howtoforge.com/user_password_creating_with_a_bash_script](http://www.howtoforge.com/user_password_creating_with_a_bash_script)) was helpful but the password part doesn't work for me.
Is there a way to change a users password with just a single line. Or is there a way to send text back to the screen when it asks you to enter your new password?

Password Script
#!/bin/sh
for i in `more userlist.txt `
do
echo $i
echo $i"123" | passwd –-stdin "$i"
done

Ubuntu Server 8.04

---

### Post by supersonicdarky on 2009-02-13
```
#!/bin/bash
# 1st param - pswd
# 2nd param - text-file with usernames, one per line

if [ $# -lt 2 ]; then
	echo "Usage: ./passwd.sh <passwd> <text file>"
	exit
fi

for i in `cat $2`; do
	echo "$i:$1"
	yes "$1" | passwd "$i"
done

```
here you go

if you want, i can modify it to read a txt file that has both username and passwd on each line and then set the passwd accordingly

---

### Post by zyban03 on 2009-02-14
THANKS!
I will give that shot. I will just add the password expire line to the bottom and that should give all the new users I create a temp pass and then make them change it at first login. I will let you know my results.:P
Thanks Again!!

---

### Post by zyban03 on 2009-02-15
> **supersonicdarky said:**
> ```
#!/bin/bash
# 1st param - pswd
# 2nd param - text-file with usernames, one per line

if [ $# -lt 2 ]; then
	echo "Usage: ./passwd.sh <passwd> <text file>"
	exit
fi

for i in `cat $2`; do
	echo "$i:$1"
	yes "$1" | passwd "$i"
done

```
here you go

if you want, i can modify it to read a txt file that has both username and passwd on each line and then set the passwd accordingly

I tried your code a couple of different ways and kept getting a line 14 syntax error which I couldn't figure out. However you did get me on the right track. I did some digging on alternative ways to change and re-wrote it like so
```

#!/bin/sh
for i in `more userlist.txt `
do
echo $i
echo $i:temp123 | chpasswd
passwd $i -e
echo; echo "User $i will be forced to change password on next login!"
done

```

Worked out like a champ!! 
Thanks for your all your help.

---

