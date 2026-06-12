---
title: "how to include the $ symbol between &quot; &quot; in a script?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by kazabubu22 on 2009-05-05
i tried to use a script as suggested in the thread below to make my usb modem work.. the problem is that i can't connect after  that and i think the problem is that my password contains ths $ symbol.somewhere in the script i have to change the expression :
PASSWORD "pasword" 
with mine.
when i write the $ in it seems that this means something and that it affects the rest of the letters in the password as well as they change color in gedit..

i could change the password but i would like to know how would i be able to do this without changing anything!sorry for my bad english and sorry if the question is silly, i'm newbie!

[http://ubuntuforums.org/showpost.php?p=4402171&postcount=32]("http://ubuntuforums.org/showpost.php?p=4402171&postcount=32")

---

### Post by sisco311 on 2009-05-05
```
VAR="variable"
echo $VAR
```
The first line creates a variable called VAR and assigns the string "variable" to it. The value of the variable is retrieved by putting '$' in at the beginning. 

Use the non-quoted backslash (\) escape character to preserve the literal value of the next character that follows.

i.e.

```
PASSWORD "pa$sword"        # pa + value of the variable sword  
-->
PASSWORD "pa\$sword"       # pa$sword 

```

---

### Post by vaughany on 2009-05-05
Thanks, that was useful. :)

---

### Post by hexanol on 2009-05-05
Well, you can either escape the $ sign or use single quote.

```
~$ test="hey"
~$ echo "$test"
hey
~$ echo "\$test"
$test
~$ echo '$test'
$test

```

Oops, a bit late.

---

### Post by kazabubu22 on 2009-05-05
thanks a lot everyone! :biggrin:

---

