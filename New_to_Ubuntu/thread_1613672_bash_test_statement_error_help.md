---
title: "bash test statement error help"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by outleradam on 2010-11-04
can someone explain this to me?

```

adam@adam-desktop:~$ $a=1
0=1: command not found
adam@adam-desktop:~$ echo $?
127
adam@adam-desktop:~$ a=0
adam@adam-desktop:~$ b=1
adam@adam-desktop:~$ c=1
adam@adam-desktop:~$ d=1
adam@adam-desktop:~$ test $a = 1 || test $b = 0 &&  test $c = 0  && test $d = 0 && echo "why is this true?"
adam@adam-desktop:~$ test $a=1 || test $b=0 &&  test $c=0 && test $d=0 && echo "why is this true?"
why is this true?
adam@adam-desktop:~$ 

```If $a=1 fails, then why would that last statement work?

---

### Post by CharlesA on 2010-11-04
I've never seen it used like that.

I've always run tests in shell scripts using if statements.

```
read -p "What does A equal? " a
if [[ $a = 1 ]]
then
echo True
else
echo False
fi

```

---

### Post by outleradam on 2010-11-04
k, but how do the conditions validate the tests?

---

### Post by CharlesA on 2010-11-04
> **outleradam said:**
> k, but how do the conditions validate the tests?

How do you mean?

if a = 1 then it echos "true" to the screen, else it echos "false"

In your original post, you had the last command using "||" which basically means run that command if $a does not equal 1.

---

### Post by Vaphell on 2010-11-04
test $a=1 || test $b=0 &&  test $c=0 && test $d=0 && echo "why is this true?"

= without surrounding spaces is the cause of failure
```
test 0=1 && echo true
``` returns true, but
```
test 0 = 1 && echo true
``` returns nothing
```
test 0 -eq 1 && echo true
``` also returns nothing

---

### Post by Old *ix Geek on 2010-11-04
> **outleradam said:**
> can someone explain this to me?

```

adam@adam-desktop:~$ $a=1
0=1: command not found
adam@adam-desktop:~$ echo $?
127
adam@adam-desktop:~$ a=0
adam@adam-desktop:~$ b=1
adam@adam-desktop:~$ c=1
adam@adam-desktop:~$ d=1
adam@adam-desktop:~$ test $a = 1 || test $b = 0 &&  test $c = 0  && test $d = 0 && echo "why is this true?"
adam@adam-desktop:~$ test $a=1 || test $b=0 &&  test $c=0 && test $d=0 && echo "why is this true?"
why is this true?
adam@adam-desktop:~$ 

```If $a=1 fails, then why would that last statement work?

There are several issues, starting with this:
```
$a=1
0=1: command not found
```
You're attempting to run a command--and I don't think that's what you're intending to do. I think you want to set "a" equal to "1", is that correct? But issuing "$a=1" as you have, the shell is taking the value of $a, which was "0", prepending that to "=1" (0=1) and trying to run it as a command, hence the '0=1: command not found.' You can see what I'm talking about by first setting "a" equal to something else:
```
$ a=5
$ $a=1
5=1: command not found
```
Also, the tests you're using are not equivalent to each other. Try this:
```
$ echo $a
5
$ test $a = 1
$ echo $?
1
$ test $a=1
$ echo $?
0
```
Do you see, and understand, the difference?

Also, if I were doing this it'd be in a shell script, using brackets for testing--and being careful to quote appropriately. The value of a string enclosed in quotes is not necessarily the same as that string NOT enclosed in quotes.

---

### Post by outleradam on 2010-11-04
No, I don't understand.  It should be checking for an exit status of 0 right?

```
adam@adam-desktop:~$ a=1
adam@adam-desktop:~$ $a=0
1=0: command not found
adam@adam-desktop:~$ echo $?
127
adam@adam-desktop:~$ test $a=0 && echo true
true

```

the exit status of $a=0 is 127.  Why does it exit true?

---

### Post by Vaphell on 2010-11-05
it doesn't matter what $a=0 alone returns, value of test $a=0 is what counts and that is 0. Apparently condition logic is not based on returned values or returned values are interpreted differently. Add spaces around the 'equal' sign and your problems will disappear (or use -eq, it's as foolproof as it gets because you can't write a badly parsed condition with it)

**test 1=1** && echo true  => true (returned 0)
but 
**1=1** || echo true    => true (returned not-0)
bolded parts decide and they don't have the same return code/logic value

besides, why worry why malformed command works incorrectly? it's malformed in the first place, all kinds of crap can happen. Every part of condition needs to be surrounded by spaces, period.

---

### Post by Old *ix Geek on 2010-11-05
> **outleradam said:**
> No, I don't understand.  It should be checking for an exit status of 0 right?No. At least I don't think so--I'm not really sure what you're trying to do. Of course it's possible to check for a given exit status, but is that what you want? Or do you want to test whether "a" equals "0"?
> 
```
adam@adam-desktop:~$ a=1
adam@adam-desktop:~$ $a=0
1=0: command not found
adam@adam-desktop:~$ echo $?
127
adam@adam-desktop:~$ test $a=0 && echo true
true

```
the exit status of $a=0 is 127.  Why does it exit true?
Try this:
```
$ test $a=0
$ echo $?
0
$ test $a=1
$ echo $?
0
$ test $a=5
$ echo $?
0
$ test $a=11
$ echo $?
0
$ test $a=1234567890
$ echo $?
0
```You're going to get a true/0 exit status EVERY TIME, regardless of what you put after the "=" because the test isn't doing what I think you think it is. Repeat the above, this time putting spaces before and after each = sign:
```
$ test $a = 0
$ echo $?
1
$ test $a = 5
$ echo $?
0     *because we set "a" = "5" a while ago*
$ test $a = 11
$ echo $?
1
$ test $a = 1234567890
$ echo $?
1
```
In the original case, test is just saying, yes, that string ($a=1 or whatever) exists. That's not what you want, right? In the second case, it's comparing the value of "a" with the number after the = sign, so it only yields a true exit status if the value of "a" equals, in our case, "5".

(Note: My scripting skills--and ability to explain them--are very rusty. If someone else has a better way of wording this, please do!)

---

