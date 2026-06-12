---
title: "CLI way of killing a process or processes? (QUICK question! :) )"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by earthpigg on 2009-01-24
i know how to do this via point-click, i want to know the terminal way...

my audio is jacked up. this has happened before, and i've solved it by terminating it in the system monitor.

1. how do i get a list of all processes running with 'pulse' in the name?

2. killall [process] is how you kill said process(es), correct?

thanks in advance ;)

---

### Post by binbash on 2009-01-24
just read this (dont forget examples) : 

[http://linux.die.net/man/1/pkill](http://linux.die.net/man/1/pkill)

---

### Post by bgerlich on 2009-01-24
list of all processes:
ps -A
An operand to forward the output to another program
|
search function that displays only lines with queried phrase
grep pulse

All together:
```
ps -A | grep pulse
```

---

### Post by ken22 on 2009-01-24
hi, 

to get a list of all processes with pulse in the name

```
ps aux | grep pulse
```

then kill the process ids listed.

---

### Post by earthpigg on 2009-01-24
i couldn't find anything about locating a process if i only know _part_ of its name... any hints?

edit: crossed posts.... got it, thanks guys!

now i gotta remember this...

---

### Post by bgerlich on 2009-01-24
grep works that way. Remember, like most things in Linux it is case sensitive.

---

### Post by lswest on 2009-01-24
you can, if you want to kill all instances of a program, run ```
sudo killall *app_name*
```

also

```
sudo kill $(pidof *app_name*)
``` also works to kill all the instances.

---

