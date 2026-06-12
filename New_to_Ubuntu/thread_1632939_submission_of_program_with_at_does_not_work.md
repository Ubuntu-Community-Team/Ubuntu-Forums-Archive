---
title: "submission of program with at does not work"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by dieter-erich on 2010-11-28
Hi!
when starting the following program:

mpirun -n 3 xmipp_mpi_ml_refine3d -i ml_1245.sel -vol 3ref.sel -ang 10 -o ref -iter 20 

from the bash shell it runs without problems

when writing these same commands into the file "job" and running

at -f job now 

I get the message that the job has been submitted but nothing happens:

atq does not show anything and top shows that nothing runs

when I submit a bash script that e.g. copies files it works well

what is wrong? I spent hours trying out a number of things but did not get it to run in batch mode

Thanks for hints, D-E

---

### Post by wojox on 2010-11-28
Try

```
sudo at -f job now 
```

Then 

```
man at
```

---

### Post by dieter-erich on 2010-11-28
Hi wojox,
  thanks, but sorry, it does not work! I do neither need sudo when submitting a bash script as this works well!
D-E

---

### Post by wojox on 2010-11-29
Okay specify when you want it

```
at now + 2 minutes -f job now
```

---

### Post by dieter-erich on 2010-11-29
Thanx, but why should it run when I specify 'now + 2 minutes' instad of 'now'? Would it need some time to get it started? As I wrote before, it works fine with a file containing e.g.:

z=z
for i in *.spi
do
cp $i $i$z
done

but it does not when submitting the program I specified!

---

### Post by gmargo on 2010-11-29
What shows up **/var/log/syslog** when it runs?

Also, make sure you have a Mail Transfer Agent installed, like postfix.  The output of any commands (or errors) will be emailed to you.

---

### Post by dieter-erich on 2010-12-01
Well, I do not see anything relevant in the syslog. There is nothing referring to at! I have the impression that the problem is the transfer of the parameters. Commands not having parameters seem to work. E.g. command xyz > x works, while command -i xyz -o x do not. Neither does it help to give the complete path. The program has to run in directory which it is being started in and take the input from the parameters given. I have tried to enclose the whole command into ' ' or ` ` and many other things. Sofar no avail. Help ist greatly appreciated!

---

