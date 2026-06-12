---
title: "Command cd and TAB"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by djelf on 2009-05-07
I was wondering if there is a way to use tab after command cd in order to browse automatically the directories of the current folder.
what i mean is not auto-complete the folder name when ex.: ~$cd ab 
and there is a folder with name abc , but display aytomatically every folder with every strike of key TAB ex: cd TAB brings on screeen ~$cd abch
 
thanks in advance

---

### Post by benj1 on 2009-05-07
cd [tab][tab] works for me

---

### Post by MrWES on 2009-05-07
> **benj1 said:**
> cd [tab][tab] works for me

Nice! -- never knew that one -- duh.

Bill

---

### Post by djelf on 2009-05-07
> **benj1 said:**
> cd [tab][tab] works for me 

no man...
i dont mean to display the folders and then go back to comand promt
what i want is by hitting tab to ayto complete the folder without typing any letter of the folder.....
this is how windows and solaris command line works 
any ideas how to?

---

### Post by bostonaholic on 2009-05-07
> **djelf said:**
> no man...
i dont mean to display the folders and then go back to comand promt
what i want is by hitting tab to ayto complete the folder without typing any letter of the folder.....
this is how windows and solaris command line works 
any ideas how to?

it will auto complete if there's only one matching.  If there are multiple folders like abc and abd it will print both.

```
cd ab[TAB][TAB]
```

---

### Post by decoherence on 2009-05-07
like, every time you hit tab, it cycles through each item in the directory?

i don't know. just want to make the question clear for anyone who might.

---

### Post by djelf on 2009-05-07
> **bostonaholic said:**
> it will auto complete if there's only one matching.  If there are multiple folders like abc and abd it will print both.

```
cd ab[TAB][TAB]
```

but i dont want to print them....like i say i need them to be displayed next to cd so i can fast access the folder

---

### Post by djelf on 2009-05-07
> **decoherence said:**
> like, every time you hit tab, it cycles through each item in the directory?

i don't know. just want to make the question clear for anyone who might.

yes thats exactly what i mean
is there a way to do it in ubuntu terminal?

---

### Post by bostonaholic on 2009-05-07
> **djelf said:**
> yes thats exactly what i mean
is there a way to do it in ubuntu terminal?

Ah, so you want it to behave like the windows terminal.

---

### Post by djelf on 2009-05-07
> **bostonaholic said:**
> Ah, so you want it to behave like the windows terminal.

if possible...

---

### Post by barwin on 2009-05-07
There are a few options that affect the behavior of readline / tab-completion in the bash terminal.  If you run

```

man bash

```

Then search for the section titled "Readline Variables" (or just search for "completion" till you get down there).  You'll see a set of environment variables you can set that will change the behavior somewhat.  I don't see anything that would accomplish exactly what you're looking for -- perhaps a different shell would though?  bash is the default (and also my personal preference), but in the past I used tcsh and the options were wildly different.

good luck!

---

### Post by sisco311 on 2009-05-07
Run this command:
```
bind '"\C-i": menu-complete'
```


If you like how that works, add the command to your ~/.bashrc file.

---

### Post by djelf on 2009-05-07
> **barwin said:**
> There are a few options that affect the behavior of readline / tab-completion in the bash terminal.  If you run

```

man bash

```Then search for the section titled "Readline Variables" (or just search for "completion" till you get down there).  You'll see a set of environment variables you can set that will change the behavior somewhat.  I don't see anything that would accomplish exactly what you're looking for -- perhaps a different shell would though?  bash is the default (and also my personal preference), but in the past I used tcsh and the options were wildly different.

good luck!

thx i'll try it

---

### Post by djelf on 2009-05-07
> **sisco311 said:**
> Run this command:
```
bind '"\C-i": menu-complete'
```
If you like how that works, add the command to your ~/.bashrc file.

i type the command but nothing happens..any i idea why ?

---

### Post by bostonaholic on 2009-05-07
> **djelf said:**
> i type the command but nothing happens..any i idea why ?

After you type that, then try your

```
cd ab[TAB][TAB]
```

It will do the auto-complete how you want it to.  I tried it myself and it worked like a charm!  Now, like sisco311 said, type that command into your ~/.bashrc so that it will configure the auto-complete everytime the terminal starts up.

---

### Post by djelf on 2009-05-07
> **bostonaholic said:**
> After you type that, then try your

```
cd ab[TAB][TAB]
```It will do the auto-complete how you want it to.  I tried it myself and it worked like a charm!  Now, like sisco311 said, type that command into your ~/.bashrc so that it will configure the auto-complete everytime the terminal starts up.


NICE GUYS...it works fine 
thank you all very much

---

