---
title: "Creating a BASH script to restart itself?"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-04-01
I just want a simple code that when placed in a bash script and run, it will resart the whole script.

Please help!

---

### Post by perpetualcacophany on 2009-04-01
I would have to imagine that telling it to execute the script again at the end of it would make the script repeat. Something like:

```
#! /usr/bin/sh
commands
commands
commands
bash scriptname
```

I just tested it and it does work. Just put "bash scriptname" (where scriptname is obviously the name of you script) at the end and it should make it run in an infinite loop.

---

### Post by taylor102387 on 2009-04-01
Thank you so much, it works. How do I thank you....I cant find the thank u button. :P

---

### Post by James_Lochhead on 2009-04-01
Thank you has been removed temporarily due to some kind of error with the forums.

By the way what you want to do is called recursion.

---

### Post by egalvan on 2009-04-01
> **James_Lochhead said:**
> 
By the way what you want to do is called recursion.

Strictly speaking, it's not "recursion" if it doesn't have a termination condition. :)

*sorry, couldn't resist*

        If you still don't get it, see: "Recursion".

:lolflag:

---

### Post by DGortze380 on 2009-04-01
> **perpetualcacophany said:**
> I would have to imagine that telling it to execute the script again at the end of it would make the script repeat. Something like:

```
#! /usr/bin/sh
commands
commands
commands
bash scriptname
```

I just tested it and it does work. Just put "bash scriptname" (where scriptname is obviously the name of you script) at the end and it should make it run in an infinite loop.

On modern systems, it's likely not an issue, but be careful of infinite loops, or long recursions that use too many resources.

---

### Post by kpatz on 2009-04-01
> **perpetualcacophany said:**
> ```
#! /usr/bin/sh
commands
commands
commands
bash scriptname
```Don't do it that way.  It's launching another shell on each loop.  You'll max out your system after a few hundred/thousand iterations (insert a ps and a sleep inside the loop to see for yourself).

You could use **exec bash scriptname**, then it won't fork a new process every time, but it will still restart the shell every time, which is less efficient than doing this:

```
#! /usr/bin/sh
while true
do
 commands
 commands
 commands
done

```

---

### Post by alexeix on 2009-09-17
Hi,

How do you create a bash script?  I mean, I presume you create a text file, but what do you save it as?

Thanks.

---

### Post by stderr on 2009-09-17
You save it. On linux, file extensions don't matter very much/at all. You could stick a .sh on the end if you *really* want. Just make sure the first line is:

```
#!/bin/bash
```

(or replace /bin/bash with the path to another shell, e.g. zsh, or correct the path if necessary)

---

### Post by DaithiF on 2009-09-17
you can save it as whatever you like.  the filename doesn't matter.  theres a convention to name script files with a '.sh' suffix, but its just a convention, its not required.

the important part is to have a 'shebang' as the first line, like
```
#!/bin/bash
```
which tells the system to have bash execute the script

---

### Post by NoaHall on 2009-09-17
Note - be very careful , I once created a infinite while loop and it managed to bring down the school network.. It wasn't my fault, 0 is just always less than one. :D

---

### Post by roololing on 2011-06-22
I'm pretty new to bash, so I don't know if this is at all an efficient  way to restart a program, or if something keeps running or not, but it's  how I did it in a program I've recently written. It's pretty simple, I  just did
```
clear
exec filename
```Which pretty much "clears" (makes a bunch of new lines until the  terminal looks empty) what you currently have in the terminal and  executes the file again, from the beginning.

---

### Post by kidknapp on 2011-06-22
:p

---

