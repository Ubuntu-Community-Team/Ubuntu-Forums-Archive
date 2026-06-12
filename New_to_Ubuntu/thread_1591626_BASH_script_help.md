---
title: "BASH script help"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by hellomoto on 2010-10-09
I am trying to grasp some basic BASH scripting, im getting a bit confused regarding variables.

```

VAR="uptime"
$VAR

```
This would assign the variable as uptime the print the uptime.
$3 hours, 15 minutes

```

VAR="uptime"
echo "Your computer has been on for $VAR"

```

I would expect this to output as follows:
$Your computer has been on for 3 hours, 15 minutes

However what I get is:
$Your computer has been on for uptime

Would I be right in saying $VAR is being read as a "string" and not as a "variable". If this is the case how do I change it to be read as a variable?

---

### Post by CharlesA on 2010-10-09
Put it in the varable like so:

```
VAR=$(uptime)
```

The one you have set in the OP will just echo uptime to the terminal, not run the command.

The only problem is that uptime prints out like this:

```
charles@atlantis:~$ uptime
 12:42:21 up 1 day,  5:40,  1 user,  load average: 0.00, 0.00, 0.00
```

---

### Post by SeijiSensei on 2010-10-09
```

VAR=`uptime`

```

Using the "backtick" operator (to the left of 1 in the upper row of the keyboard) evaluates the expression inside the backticks and passes the result to VAR.  An alternative to using the backticks is an expression like this:

```

VAR=$(uptime)

```

---

### Post by CharlesA on 2010-10-09
> **SeijiSensei said:**
> 
```

VAR=$(uptime)

```

That is the preferred way, since it's easier to nest than backticks.

---

### Post by hellomoto on 2010-10-09
this fixed the problem, thankyou

---

### Post by honeybear on 2010-10-09
> **SeijiSensei said:**
> ```

VAR=`uptime`

```

Using the "backtick" operator (to the left of 1 in the upper row of the keyboard) evaluates the expression inside the backticks and passes the result to VAR.  An alternative to using the backticks is an expression like this:

```

VAR=$(uptime)

```

the ```
 VAR=`uptime` 
``` is usually adviced, because it is more powerful"" and less messy

---

### Post by honeybear on 2010-10-09
Question:

```

VAR=`cat FILE`
if [ "$VAR" != "" ] ; then 
```


or 

```
if [ "`cat FILE`" != "" ] ; then 
```


which one is better/working ?

---

### Post by Vaphell on 2010-10-09
imo it's the same in this case
if i am not mistaken `` is less desirable when you want to process the output of a command in multiple steps - `` is like macro so in reality it's the command itself substituted for the variable, thus making it that each time variable is used, the command is run.
 $(...) on the other hand stores the output in a variable, so the command is only run once. I may be mistaken though so take that with a grain of salt.

---

### Post by CharlesA on 2010-10-09
See the thread [here]("http://ubuntuforums.org/showthread.php?t=1587331") (and links therein) for more info as to why $(...) is prefered to backticks.

---

### Post by honeybear on 2010-10-09
> **CharlesA said:**
> See the thread [here]("http://ubuntuforums.org/showthread.php?t=1587331") (and links therein) for more info as to why $(...) is prefered to backticks.

well discussion like tastes but ok

in my examples, am I right ? both work?

so taht 
```
if [ `cat command.txt | grep convert` != "" ] ; then 
``` works flawless, can you imagine it with $() ? then you would need ""

---

### Post by CharlesA on 2010-10-09
> **honeybear said:**
> 
```
if [ `cat command.txt | grep convert` != "" ] ; then 
``` 

You'd write it like this:

```
if [ $(cat command.txt | grep convert) != "" ] ; then
```

---

### Post by honeybear on 2010-10-09
> **CharlesA said:**
> You'd write it like this:

```
if [ `cat command.txt | grep convert` != "" ] ; then
```

thanks 

wrong code:
```
if [  `cat command.txt | grep convert` != "" ] ; then
```[/QUOTE]


good code:
```
if [ $(cat command.txt | grep convert) != "" ] ; then
```[/QUOTE]


good code: (thx, I learn)
```
if [ "`cat command.txt | grep convert`" != "" ] ; then
```[/QUOTE]


```
 for each in *.grf ; do echo $each ; FILE2=`echo $each | sed 's/\.[^\.]*$//'` ;  DATENOW=`date +%F[%HH%MM%S]` ; echo $DATENOW_$FILE2.txt ; done 

```  why it does not put the time DATENOW in the echo $DATENOW_$FILE2.txt  output? It is strange ...

---

