---
title: "bash pipe question"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by PGScooter on 2009-06-13
Hi, how can I get the individual file sizes of files with filenames that contain the word "foo" using a pipe? I figured out how to do it with the ``find'' command, but I would like to get better at pipes.

My attempt does not work:
```
ls | grep foo | du
```

thanks

---

### Post by prvteprts on 2009-06-13
I think it's the grep part that is the problem. Try:

grep *foo* -i

The asterisks mean anything at the head and tail as long as foo is in between. The -i parameter is to ignore the case.

---

### Post by kpkeerthi on 2009-06-13
find /path/to/search -iname "*foo*" -exec du -h '{}' ';'

---

### Post by niteshifter on 2009-06-13
Hi,

kpkeerthi gives a clue (and a working find command), but it's a pretty obscure clue ...

```
ls | grep foo | du
```

Won't work - but you knew that ;) Why? The pipe operator connects the standard output of *ls* to the standard input of *grep foo*, which has it's stdout connected to *du* stdin.

Only one problem: du doesn't have a stdin. du only takes file arguments passed to it on invocation (the command line).

Now somebody might think, this being a coreutils program that '-' (sans quotes) could be used. It even hints at such in the info file - not man page, the info pages, specifically:
```
info coreutils 'du invocation'
```
more to the point:
```
info coreutils 'Common options'
```
A - usually can be used on a coreutils program command line wherever FILE is specified. For example let's play with sort:
```
sort -
```
Notice that the terminal is sitting there, cursor blinking. It's waiting for input (from stdin) so type gg, press Enter, type aa, press Enter, type Ctrl+D (to give an End Of File, ends input) and we see aa on line 1 of output followed by gg.

But not du:
```
du -
```
always croaks. The reason why is left as an exercise for the reader.

---

### Post by asmoore82 on 2009-06-13
Solution #1(Youngling):
```
du -sh **foo**
```
Solution #2(Padawan):
```
ls -sh **foo**
```
Solution #3(Jedi Knight):
```
ls -sh | grep *foo*
```
^^A Jedi can feel the Force *flowing* through him - *"Use the pipes, Luke!"*


Solution #4(Rebel Forces):
```
for file in **foo**
do
  du -sh "$file"
done
```
^^Brute force hacking; but any number of commands could be added to the loop


Solution #5(Jedi Master):
```
find . -iname "**foo**" -print0 | xargs -0 du -sh
```
^^A Jedi uses the Force for Knowledge - This is a recursive search.
*"Through the Force, things you will see. Other places. The future...the past...old friends long gone."*


Solution #6(Dark Side)
```
ls | grep *foo* | xargs du -sh
```
^^Is the Dark Side stronger? No: quicker, easier, more seductive; but not stronger.
This solution _*breaks*_ for filenames with special characters - all other solutions do not.

---

### Post by scorp123 on 2009-06-13
> **PGScooter said:**
> Hi, how can I get the individual file sizes of files with filenames that contain the word "foo" using a pipe?  ```
du -hs ./* | grep foo 
```

---

### Post by nandemonai on 2009-06-13
> **asmoore82 said:**
> Solution #1(Youngling):
```
du -sh **foo**
```
Solution #2(Padawan):
```
ls -sh **foo**
```
Solution #3(Jedi Knight):
```
ls -sh | grep *foo*
```
^^A Jedi can feel the Force *flowing* through him - *"Use the pipes, Luke!"*


Solution #4(Rebel Forces):
```
for file in **foo**
do
  du -sh "$file"
done
```
^^Brute force hacking; but any number of commands could be added to the loop


Solution #5(Jedi Master):
```
find . -iname "**foo**" -print0 | xargs -0 du -sh
```
^^A Jedi uses the Force for Knowledge - This is a recursive search.
*"Through the Force, things you will see. Other places. The future...the past...old friends long gone."*


Solution #6(Dark Side)
```
ls | grep *foo* | xargs du -sh
```
^^Is the Dark Side stronger? No: quicker, easier, more seductive; but not stronger.
This solution _*breaks*_ for filenames with special characters - all other solutions do not.

The force is strong in this one, yes.

---

### Post by PGScooter on 2009-06-13
thanks everyone!! wow... I got answers, I got explanations, and I got humour.. what else could one ask for from a thread?

I have studied all of the commands proposed and their explanations, and I am glad to be able to add some more tools and intuition to my previously force-less Ubuntu skills.

Thank you!!!!!!!!!!!!

---

### Post by scorp123 on 2009-06-13
> **nandemonai said:**
> The force is strong in this one, yes. 
**_The Sith... ^H^H^H Shell Code_**

GUI's are a lie, they're just front-ends to the shell.
Through the shell, I gain sudo.
Through sudo, I gain power.
Through power, I gain root.
Through root, my chains are broken.
uid=0 shall free me.


**_One Truth_**

"man". "man" attracts the fearful, the strong,
the weak, the innocent, the corrupt.
"man". "man" is my ally.

:D

---

### Post by ibuclaw on 2009-06-13
> **scorp123 said:**
> **_The Sith... ^H^H^H Shell Code_**

GUI's are a lie, they're just front-ends to the shell.
Through the shell, I gain sudo.
Through sudo, I gain power.
Through power, I gain root.
Through root, my chains are broken.
uid=0 shall free me.


**_One Truth_**

"man". "man" attracts the fearful, the strong,
the weak, the innocent, the corrupt.
"man". "man" is my ally.

:D

I beg your pardon?

There are ways around the limitations of xarg, you know.

```
ls *foo* | xargs -d'\n' du
```
or
```
ls | grep foo | xargs -d'\n' du
```
The -d sets the delimiter to which xargs parses the content given to it. In this example. you are setting it to '\n' or 'newline', as it is called.

Regards
Iai^H^H^H

---

### Post by scorp123 on 2009-06-13
> **tinivole said:**
> I beg your pardon?    Star Wars Humor. Off-topic, I know I know ...  Just could not resist. :D

---

### Post by asmoore82 on 2009-06-14
*"Once you start down the Dark Path, Forever will it dominate your destiny. Consume you it will."*

> **tinivole said:**
> There are ways around the limitations of xarg, you know.
```
ls *foo* | xargs -d'\n' du
```


^^Solution #7(Sith Lord)

Unix does not prevent filenames from having newlines in them.
Solutions 1-5 are all fine even with this possibility - 6 and 7 are *_not_*.

Solution #3(Jedi Knight) could be slightly better as this:
```
ls -bsh | grep *foo*
```

*"Mind what you have learned. Save you it can!"*

---

### Post by ibuclaw on 2009-06-14
True.


The **Jen'ari** solution, would be this then:
```
ls -sh | grep foo | sed 's/^\s*\(\S*\)\s*/\1	/'
```
Here, we have the 'ls' way, but we use sed to output the data like 'du' does.
To put a \t or "TAB" into the shell line, you press:

```
**Ctrl+V** <**TAB**>
```

:)

---

### Post by ghostdog74 on 2009-06-15
```

ls -sh | grep foo 

```
grep is redundant.
```

ls -sh *foo*

```

---

