---
title: "What is wrong with this script?"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by Come TO love on 2011-05-12
I write this script and do not no whrer the wrong!!
Can anyone hlep me?

#=========================================
Script Name: shell_script1
#=========================================
looptrack=y
while [ “$looptrack” = 1 ]
do
echo -n “Type in the account number:” read account
echo -n “Type the first and last name:” ; read full_name
echo -n “Type the age:” red age
echo -n “Enter another record?” ; read looptrack
finish

---

### Post by An Sanct on 2011-05-12
Try this
```

#=========================================
# Script Name: shell_script1
#=========================================
looptrack=1;
while : [$looptrack="1"]
do
echo -n 'Type in the account number:'; read account;
echo -n 'Type the first and last name:'; read full_name;
echo -n 'Type the age:'; read age;
echo -n 'Enter another record?'; read looptrack;
done;

```

There is still an error in exiting. I will edit this post when I find the solution.

---

### Post by DaithiF on 2011-05-12
something like:
```
looptrack=1;
while [ -n "$looptrack" ]
do
read -p 'Type in the account number: ' account
read -p 'Type the first and last name:' full_name
read -p 'Type the age:' age
read -p 'Enter another record? (return to exit) ' looptrack
done

```

---

### Post by Sef on 2011-05-13
Moved to ABT.

---

