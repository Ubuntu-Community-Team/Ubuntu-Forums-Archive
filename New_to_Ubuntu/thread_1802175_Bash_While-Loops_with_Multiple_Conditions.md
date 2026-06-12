---
title: "Bash: While-Loops with Multiple Conditions"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by roololing on 2011-07-11
Is there a way to create while-loops with multiple conditions? Like if you want to read a few things from a file and check if a flag is true it'd be something like this:
```
flag=1
while [ $flag -eq 1 ]&&[ read var1 var2 ];
do
        #stuff
done
```
I tried that code, but I got an error saying there are too many variables. I think the **read** function is trying to assign the variables $var1, $var2, and $]. But I'm not sure. Anyone have any ideas?

Any help is appreciated.

---

### Post by AlphaLexman on 2011-07-11
> **roololing said:**
> Is there a way to create while-loops with multiple conditions? Like if you want to read a few things from a file and check if a flag is true it'd be something like this:
```
flag=1
while [ $flag -eq 1 ]&&[ read var1 var2 ];
do
        #stuff
done
```I tried that code, but I got an error saying there are too many variables. I think the **read** function is trying to assign the variables $var1, $var2, and $]. But I'm not sure. Anyone have any ideas?

Any help is appreciated.
The '**while**' command is often specified with the 'test' construct, however, your test condition will never fail, so you have an infinite number of '**read var1 var2**'

Maybe you have more code that changes the value of '**$flag**'... you would need to post it!

---

### Post by roololing on 2011-07-11
> **AlphaLexman said:**
> The '**while**' command is often specified with the 'test' construct, however, your test condition will never fail, so you have an infinite number of '**read var1 var2**'

Maybe you have more code that changes the value of '**$flag**'... you would need to post it!

Sorry, I'll try to simplify what I have, as it's quite lengthy.
```
flag=1
while [ $flag -eq 1 ][ read var1 var2 ];
do
        if [ #blah ]; then
                #Perform some tasks.
        else
                flag=0
        fi
done < inputfile.txt

```

It reads from a file, so "read var1 var2" won't always be true.

---

### Post by sisco311 on 2011-07-11
> **roololing said:**
> Is there a way to create while-loops with multiple conditions? Like if you want to read a few things from a file and check if a flag is true it'd be something like this:
```
flag=1
while [ $flag -eq 1 ]&&[ read var1 var2 ];
do
        #stuff
done
```
I tried that code, but I got an error saying there are too many variables. I think the **read** function is trying to assign the variables $var1, $var2, and $]. But I'm not sure. Anyone have any ideas?

Any help is appreciated.

You can  replace **[ EXPRESSION ]** with **test EXPRESSION** (check out `man bash | less +/"^ +test expr"').

Do you really want the second test command? ;)

---

### Post by roololing on 2011-07-11
> **sisco311 said:**
> You can  replace **[ EXPRESSION ]** with **test EXPRESSION** (check out `man bash | less +/"^ +test expr"').

Do you really want the second test command? ;)

So like
```
flag=1
while test $flag -eq 1 -a read var1 var2;
do
        #stuff
done
```
?
It still says there are too many arguments....

---

### Post by sisco311 on 2011-07-11
> **roololing said:**
> So like
```
flag=1
while test $flag -eq 1 -a read var1 var2;
do
        #stuff
done
```
?
It still says there are too many arguments....

That's the equivalent of:
```

while [ $flag -eq 1 -a read var1 var2 ];
do
        #stuff
done
```

You didn't get rid of the second `test' command; you merged its EXPRESSION  with the first one. 

I guess, you are looking for something like:
```

flag=1
while [ $flag -eq 1 ] && read -r var1 var2;
do
       : 
done < file

```

Check out the bash guide at: [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

---

### Post by roololing on 2011-07-11
> **sisco311 said:**
> That's the equivalent of:
```

while [ $flag -eq 1 -a read var1 var2 ];
do
        #stuff
done
```

You didn't get rid of the second `test' command; you merged its EXPRESSION  with the first one. 

I guess, you are looking for something like:
```

flag=1
while [ $flag -eq 1 ] && read -r var1 var2;
do
       : 
done < file

```

Check out the bash guide at: [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

Ah. Annoyingly simple, as usual. :lolflag:
Thanks.

---

