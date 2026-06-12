---
title: "simple bash script erro"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-03-01
hi all,

recently started learning how to create scripts. while messing around with a "script" i've made, i have run into a simple error. here's the script:

```
#! /bin/bash
who | wc -l >$users;
echo "There are currently $users users logged in"
~         
```                                              

i get this error:
```

{03-01-09 - 07:51 PM User: j}~$ nusers 
/home/j/bin/nusers: line 2: $users: ambiguous redirect
There are currently  users logged in
{03-01-09 - 07:51 PM User: j}~$ 
```

i know i'm overlooking something really simple here... any help? i've googled the "ambiguous redirect" and haven't found much to go off of...

---

### Post by asmoore82 on 2009-03-01
you can't assign variable values with the **`$`** structure - that's only for getting the values they hold.

assign them with a **`=`** structure and no **`$`** at all

the other missing link you need is how to capture the output of the commands in the variable;
**`>`** is only for redirecting output to files.

For variables and assignment statements, this ability is called **command substitution**
and there are 2 forms of it that do exactly the same thing.
1. the single backquotes - this is the old fashioned way that is more widely
supported by different shells - you will see more often, especially in system startup scripts:
```
variable=`cmd arg1`
```
2. modern BASH style - this is easier on the eyes but will not work in older versions of shells:
```
variable="$( cmd arg1 )"
```

so, your corrected code would look like this:
```
#!/bin/bash
users="$( who | wc -l )"
echo "There are currently $users users logged in."
```

---

### Post by Omnios on 2009-03-01
I just ran that it said there are two users logged in.

 Umm?

---

### Post by jmd9qs on 2009-03-01
wow... quick and precise. thank you for clearing that up!

---

### Post by asmoore82 on 2009-03-01
> **Omnios said:**
> I just ran that it said there are two users logged in.

 Umm?

it counted you twice:

```
**~$** who | wc -l
2
**~$** who
asmoore  tty7         2009-02-26 16:59 (:0)
asmoore  pts/0        2009-03-01 22:07 (:0.0)
```

if we really wanted to be fancy and not count ppl more than once:
```
who | cut -d" " -f1 | sort | uniq | wc -l
```

---

### Post by asmoore82 on 2009-03-01
super-duper shell scripting fun:
[http://ubuntuforums.org/showthread.php?t=1078472](http://ubuntuforums.org/showthread.php?t=1078472)

---

