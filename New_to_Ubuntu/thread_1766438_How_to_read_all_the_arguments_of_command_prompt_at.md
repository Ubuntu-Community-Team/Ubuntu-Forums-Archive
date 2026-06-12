---
title: "How to read all the arguments of command prompt at once in c?"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by dannydud on 2011-05-24
Hi,
Can any one pls suggest me how all the arguments (entire line) of the command prompt can be read at once...I want to run a program which has to read a sentence & store it into memory using c...This sentence has to be read as argument from command prompt...

Say

:~$./a.out Sky is blue

how can i read the sentence "sky is blue" at once and store it in a file..

I am newbie to ubuntu..So kindly help..
Thanks in advance

---

### Post by compmodder26 on 2011-05-24
try  putting the sentence in quotes and it should be treated as a single argument.

---

### Post by blind2314 on 2011-05-24
> **dannydud said:**
> Hi,
Can any one pls suggest me how all the arguments (entire line) of the command prompt can be read at once...I want to run a program which has to read a sentence & store it into memory using c...This sentence has to be read as argument from command prompt...
 
Say
 
:~$./a.out Sky is blue
 
how can i read the sentence "sky is blue" at once and store it in a file..
 
I am newbie to ubuntu..So kindly help..
Thanks in advance
 
 
What have you tried so far? Seems like sort of a strange "assignment" for something that isn't school related. If you're trying to learn on your own, just having the answer given to you won't help in the long run, I promise :)

---

### Post by Wim Sturkenboom on 2011-05-24
The shell will pass each 'word' in the sentence as an argument to the program; there is no way around it.

So you have two options:
1)
as said, put the sentence between double quotes
2)
read all arguments one by one and append them to each other

---

### Post by dannydud on 2011-05-26
Hi everyone,
Sorry for my late reply..Thanks for ur help..I knew about reading arguments 1 by 1..But I was not knowing about string inside quotes...Putting the string inside double quotes worked...Thanks once again to everyone..:).

---

