---
title: "Bash Scripting HELP! :)"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by cvinkestijn on 2011-02-16
Guys,

I have a problem with my bash scripting knowledge.
I'm searching for a bash script can you help me?

Now modify your script greeting so that it

greets the user by (user)name,
prints the current date, and
prints a list of users currently logged onto the computer.
For example, your output might look similar to the following:

Good morning, vadmin.
Date is Sun Apr 20 12:22:47 CDT 2010
Users on Leah:
vadmin :0           2010-04-20 11:45
vadmin pts/0        2010-04-20 11:45 (:0.0)
vadmin pts/1        2010-04-20 11:49 (:0.0)

Thanks!

Chris

---

### Post by lotharmat on 2011-02-16
Is this homework?

---

### Post by cvinkestijn on 2011-02-16
Yes that's true school, i'm a noob in bash scripting. I have this bash scripting and doesn't not work:

#!/bin/bash






jaar=$(date +%Y)
time=$(date +%H)

#echo $jaar
#echo $time

if [ "$jaar" ]
then
	echo "jaar" $name

elif [ "$time" -lt 12 ]
then
	echo "Good Morning" $name
	
elif [ "$time" -lt 18 ]
then
	echo "Good Afternoon" $name


elif [ "$time" -lt 24 ]
then
	echo "Good Evening" $name



fi

---

### Post by fabricator4 on 2011-02-16
> **cvinkestijn said:**
>  I have this bash scripting and doesn't not work:

I'll say.

You'll [find this]("http://www.freeos.com/guides/lsst/") useful.


Also [crash bash]("http://www.linuxconfig.org/Bash_scripting_Tutorial").

---

### Post by fabricator4 on 2011-02-16
Meanwhile...

Here's a tip that will get you extra marks when your tutor sees your code:

```

#!/bin/bash


foo=( 44 6F 6E 27 74 20 77 72 69 74 65 20 74 68 65 20 73 61 6D 65 20
 63 6F 64 65 20 6F 76 65 72 20 61 67 61 69 6E 2E )
bar=0

while [ $bar -ne 37 ]
do
        echo -e -n "\x"${foo[bar]}
        ((bar++))
done

echo



```

---

### Post by cvinkestijn on 2011-02-16
The problem is, i explain any code for my teacher. :S

Thanks for your code!

---

