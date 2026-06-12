---
title: "Pass variables in Range of For Loop?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Berserker v7 on 2009-03-19
Hi guys...

Suppose you have got two variables $a and $b in your shell script and want to give them as range for your For loop, how can this be done?

Say, for example, i want to write a script to accept two numbers from the user and print all numbers between and including them. The following code is intended to do this but it actually passes {$a..$b} as the single value for $i instead of expanding it...
```
a=$1;b=$2
for i in {$a..$b}; do
echo $i
done
```
Please suggest how i can overcome this slight glitch... thanks

Note: I know that this particular problem can be solved without going for a for loop. I have just used it for illustration.

---

### Post by cafeytv97 on 2009-03-19
try this

a=1;b=2
for i in $(seq $a $b); do
echo $i
done

---

### Post by Berserker v7 on 2009-03-20
Thanks a lot!!! that did the trick.....

---

