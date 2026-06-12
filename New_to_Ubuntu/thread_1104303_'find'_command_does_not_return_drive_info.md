---
title: "'find' command does not return drive info"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by egalvan on 2009-03-23
I was practicing breaking,,, er,,, learning new commands, yeah, that's right...

I was following a how-to about re-installing GRUB...

one of the steps was to run this command:

```
sudo find /boot/grub/stage1

```

this is supposed to return the location of the stage1 files...

but all i get is the file name returned...

why don't I get the location?

What am I doing wrong?

yes, this is done on a working Ubuntu install..

see screen shot...

---

### Post by Sealbhach on 2009-03-23
You're meant to go into grub first.

sudo grub

then try find.


.

---

### Post by howlingmadhowie on 2009-03-23
hello :)

what are you trying to find out? you seem to already know the location of the file. find is used for other things, for example 
```

find . -type d

```
will return a list of directories in the current working directory (the "." token)

---

### Post by egalvan on 2009-03-23
> **Sealbhach said:**
> **You're meant to go into grub first.**

sudo grub

then try find.


.

OK, works perfect now...

find under grub is not the same as find under the cli...

got it.

Many thanks...

One step closer to Linux Geek-ness
ErnestG

---

### Post by egalvan on 2009-03-23
> **howlingmadhowie said:**
> hello :)

what are you trying to find out? **you seem to already know the location of the file**.

Well, of course I know where the files are... 
I put them there... :p

but what if I didn't?

Seriously now...
As I stated in my original post, I am just practicing commands.
Following 'how-to's' in order to learn 'how to' do stuff.
When the results don't come out the same as in 'the book',
then I try to find out why.
One of the basis of acquiring knowledge...

"Practice Makes Perfect"

So I practice.

Which usually results in breaking things...
which is why I practice on a "practice" computer... :)


> **find is used for other things,** for example 
```

find . -type d
```
*will return a list of directories in the current working directory (the "." token)*

I read the 'man find' pages and the first thing I saw was
"*find - search for files in a directory hierarchy*"
I understood this OK.
Then I read this:
[I]searches the directory tree rooted at each given file  name  by  evaluating  the
       given  expression  from left to right, according to the rules of prece&#8208;
       dence (see section OPERATORS), until the outcome  is  known  (the  left
       hand  side  is  false  for and operations, true for or), at which point
       find moves on to the next file name.
[/I]
Which I have no idea what it means...
so I am 'playing' with this command to learn it... :)
ErnestG

---

