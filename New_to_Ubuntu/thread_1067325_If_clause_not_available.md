---
title: "If clause not available"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Jhodytropical on 2009-02-11
Hi all,
 In my Linux Programming class, we are studying Linux Scripting and my decisions structures are not working. When I type 'man if' I got " no manual entry for if'. I think that I am missing a something on my configuration. I am using Ubuntu 8.10. Any ideas what files are missing in my installation ?

---

### Post by Tatty on 2009-02-11
"if" is not an application.  I think you want ```
man bash
```

---

### Post by Jhodytropical on 2009-02-11
> **Tatty said:**
> "if" is not an application.  I think you want ```
man bash
```

I know it is not. The if clause in my scripts would not work because the "if" command is not available in my shell. My question is: what is it that I am missing in my Ubuntu installation that  makes that not available ? When I type " man if" I get a message saying " no manual entry for if" .
Thanks

---

### Post by kk0sse54 on 2009-02-11
> **Jhodytropical said:**
> I know it is not. The if clause in my scripts would not work because the "if" command is not available in my shell. My question is: what is it that I am missing in my Ubuntu installation that  makes that not available ? When I type " man if" I get a message saying " no manual entry for if" .
Thanks

You are getting no manual entry because it's not an application. In other words it's not an unix command.

---

### Post by Jhodytropical on 2009-02-11
> **C!oud said:**
> You are getting no manual entry because it's not an application. In other words it's not an unix command.

Ok,
 Maybe I am not clear enough. Please tell me what's wrong with this script ?

clear
declare -i grade
echo " What grade do you expect to have for this class ? " 
read -p grade

if [ $grade > 90 then ]
 echo -n " You are perfoming at my Level - Congrats "
else
 echo -n " You can do better than that " 
 echo -n " Stop going to bed early - paresseux "
fi
====================/.
 and here is the output :
 What grade do you expect to have for this class ? 
grade54
ifexample: line 8: syntax error near unexpected token `else'
ifexample: line 8: `else'
jean@jean-laptop:~$

---

### Post by kk0sse54 on 2009-02-11
```
if [ $grade > 90 then ]
```
I'm no programmer but the "then" should be outside the brackets

```
if [ $grade > 90 ]; then
```

---

### Post by howlingmadhowie on 2009-02-11
> **Jhodytropical said:**
> I know it is not. The if clause in my scripts would not work because the "if" command is not available in my shell. My question is: what is it that I am missing in my Ubuntu installation that  makes that not available ? When I type " man if" I get a message saying " no manual entry for if" .
Thanks

if is a shell reserved word, which means it's part of the shell, and is used to steer program execution.

there's also the category of built-in commands. here's a list: 
[clickity]("http://linux.about.com/library/cmd/blcmdl1_builtin.htm").

built-in commands are different from called commands because they run inside the shell instead of forking a new process to run in.

---

### Post by Jhodytropical on 2009-02-11
clear
declare -i grade
echo " What grade do you expect to have for this class ? " 
read -p grade

if [ $grade > 90 ]; Then
 echo -n " You are perfoming at my Level - Congrats "
else
 echo -n " You can do better than that " 
 echo -n " Stop going to bed early - paresseux "
fi
==============
New error message:
 What grade do you expect to have for this class ? 
grade54
ifexample: line 8: syntax error near unexpected token `else'
ifexample: line 8: `else'
jean@jean-laptop:~$ gedit ifexample
jean@jean-laptop:~$

---

### Post by howlingmadhowie on 2009-02-11
> **Jhodytropical said:**
> 
if [ $grade > 90 then ]


either:

```

if [[ $grade -gt 90 ]]; then

```

or:

```

if (( $grade > 90 )); then

```

---

### Post by kk0sse54 on 2009-02-11
Should be a lower case t "then" after which I was able to get it to work

---

### Post by Tatty on 2009-02-11
It should be "then" not "Then" after your if condition

---

### Post by howlingmadhowie on 2009-02-11
> **Jhodytropical said:**
> 
ifexample: line 8: syntax error near unexpected token `else'
ifexample: line 8: `else'
jean@jean-laptop:~$ gedit ifexample
jean@jean-laptop:~$

```
elif
```

-------

sorry, scratch that :) i'm tired and it's late :)

---

### Post by Jhodytropical on 2009-02-11
Thanks for your help.

I tried both ways and got the same error message:

jean@jean-laptop:~$ bash -f ifexample

 What grade do you expect to have for this class ? 
grade54
ifexample: line 8: syntax error near unexpected token `else'
ifexample: line 8: `else'

---

### Post by howlingmadhowie on 2009-02-11
can you paste your current code?

---

### Post by Tatty on 2009-02-11
this code works for me...

```
clear
declare -i grade
echo " What grade do you expect to have for this class ? "
read -p grade

if [ $grade > 90 ]; then
echo -n " You are perfoming at my Level - Congrats "
else
echo -n " You can do better than that "
echo -n " Stop going to bed early - paresseux "
fi
```

**EDIT:** actually, its not quite working as it is not displaying the correct message when below 90.  I am not familiar with bash im afraid, but there are no error messages coming up.

---

### Post by Jhodytropical on 2009-02-11
Hi

It seems to work now, but It doesn't take into consideration the truth of the condition. For example if you enter 95 it still goes to the second message which is : " You can do better ..."



clear
declare -i grade
echo " What grade do you expect to have for this class ? " 
read -p grade

if [[ $grade -gt  90 ]]; then
 echo -n " You are perfoming at my Level - Congrats "
else
 echo -n " You can do better than that " 
 echo -n " Stop going to bed early - paresseux "
fi

---

### Post by kk0sse54 on 2009-02-11
*deleted* using an older version of your code

---

### Post by howlingmadhowie on 2009-02-11
> **Jhodytropical said:**
> Hi

It seems to work now, but It doesn't take into consideration the truth of the condition. For example if you enter 95 it still goes to the second message which is : " You can do better ..."



clear
declare -i grade
echo " What grade do you expect to have for this class ? " 
read -p grade

if [[ $grade -gt  90 ]]; then
 echo -n " You are perfoming at my Level - Congrats "
else
 echo -n " You can do better than that " 
 echo -n " Stop going to bed early - paresseux "
fi

you're not storing the entered value anywhere.
you can do this by writing:

```

read -p "grade: " grade

```

---

### Post by Jhodytropical on 2009-02-11
Here's the final script that seems to work. Thanks for your support. I hope someone else can benefit from your wisdoms. Many thanks to all of you . 

clear
declare -i grade
echo " What grade do you expect to have for this class ? : " 
read grade

if [ $grade -gt  90 ]; then
 echo -n " You are perfoming at my Level - Congrats "
else
 echo -n " You can do better than that " 
 echo -n " Stop going to bed early - paresseux "
fi
echo ""

---

