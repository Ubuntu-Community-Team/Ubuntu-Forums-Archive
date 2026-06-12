---
title: "Bash shell help"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by abraves247 on 2009-11-21
I am new to Ubuntu and I am trying to learn how to do simple scripts with vi
I am trying to do a simple calculator this is what I have
 
#!/bin/bash
 
echo -e "Enter first number: \c"
read NUMBER1
 
echo -e "Pick on of the operations +, -, /, *: \c"
read MATH
 
echo -e "Enter second number: \c "
read NUMBER2
 
 
if [ $MATH = + ]
then echo -e "= "
$(($NUMBER1+$NUMBER2)) 
 
if [ $MATH = - ]
then echo -e "= "
$(($NUMBER1-$NUMBER2)) 
 
if [ $MATH = / ]
then echo -e "= "
$(($NUMBER1/$NUMBER2)) 
 
if [ $MATH = * ]
then echo -e "= "
$(($NUMBER1*$NUMBER2)) 
 
fi
 
when I run it I get ./calc: line 15: 3: command not found
I think I am close I am just missing somthing any help would be good

---

### Post by ayenack on 2009-11-21
You've got an extra space at the end of this line between the \c ". Try changing it from.

```
echo -e "Enter second number: \c "
read NUMBER2
```

To

```
echo -e "Enter second number: \c"
read NUMBER2
```

This is also the line referring to line 15. (I think.)

---

### Post by lswb on 2009-11-21
You almost got it, just change all $((...)) lines lke so:

echo $(($NUMBER1+$NUMBER2))

---

### Post by abraves247 on 2009-11-21
Thankyou both for the help that did the trick

---

### Post by Zoot7 on 2009-11-21
For reference purposes, here's a good tutorial on the basics of scripting in bash. I used one very like it a couple of years to cut my teeth with Bash. :)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

