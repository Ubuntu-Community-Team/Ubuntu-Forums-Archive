---
title: "grep help"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by abhishek1912 on 2011-06-08
How to
ls |grep <keyword1> <keyword2>
In words:
ls(list files) such that they contain keyword1 .It also should be displayed if it contains keyword2(though not necessarily keyword1, kinda like OR function)

---

### Post by Toz on 2011-06-08
Try:
```
ls | grep -E 'key1|key2'
```

---

### Post by josephmills on 2011-06-09
```
dmesg(or whatever) | **egrep** whatever|whateveer|whatever|whatever|ect......
```
Please see [http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

---

### Post by DaithiF on 2011-06-09
you can also do this directly in bash with shell expansion (when you have extglob set)
```
shopt -s extglob
ls *@(word1|word2)*

```

---

### Post by abhishek1912 on 2011-06-09
ls | grep -E 'key1|key2'
It works!

dmesg(or whatever) | egrep whatever|whateveer|whatever|whatever|ect..

me, ubuntu noob. dmesg is a very cool command.
But its not working for me. Can u be more explicit?

shopt -s extglob
ls *@(word1|word2)
This works for me straight up. But I have no clue how its working. Thanks, will read into it.

PS: How'd u guys get to know these things? Tutorials?(I dont prefer asking such questions)

---

### Post by DaithiF on 2011-06-09
> **abhishek1912 said:**
> 
shopt -s extglob
ls *@(word1|word2)
This works for me straight up. But I have no clue how its working. Thanks, will read into it.


the man page for bash is a wonderful thing:
```
man bash | less +"/If the extglob"
```

---

### Post by Fisher_ on 2011-06-09
> **DaithiF said:**
> you can also do this directly in bash with shell expansion (when you have extglob set)
```
shopt -s extglob
ls *@(word1|word2)*

```

Can you do it with braces expansion?

---

### Post by DaithiF on 2011-06-09
> **Fisher_ said:**
> Can you do it with braces expansion?
yes, ls *{word1,word2}* would expand to:
ls *word1* *word2*
which will give equivalent results in this case (and without needing extglob set)

there are other extglob patterns that you wouldn't be able to replicate easily though (e.g. !(...) - match anything except one of the given patterns)

---

### Post by Fisher_ on 2011-06-09
Nice. What does the * stand for though?

---

### Post by sisco311 on 2011-06-09
> **Fisher_ said:**
> Nice. What does the * stand for though?

[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob) ;)

---

### Post by Toz on 2011-06-09
> **abhishek1912 said:**
> PS: How'd u guys get to know these things? Tutorials?(I dont prefer asking such questions)
From years and years in the trenches - the unix trenches that is.

---

### Post by idoitprone on 2011-06-09
```
ls | grep "key1\|key2"
```

---

