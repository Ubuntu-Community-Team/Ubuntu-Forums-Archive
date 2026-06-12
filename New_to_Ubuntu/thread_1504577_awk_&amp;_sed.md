---
title: "awk &amp; sed"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Drenriza on 2010-06-08
Awk and sed. What is best?
What is the main difference between the 2 programs.

And is their other programs that can do the same as awk and sed?

thanks on advance.

---

### Post by Paddy Landau on 2010-06-08
This thread belongs in the [Programming Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=39").

awk and sed are completely different. They are complementary, rather than one-or-the-other.

sed is great for editing files or output.

awk is a programming script that you can use on Linux.

Go through the manuals carefully to understand them. Google too will help.

---

### Post by Drenriza on 2010-06-08
So what can you program with awk. The same as with bash or?

---

### Post by Paddy Landau on 2010-06-08
> **Drenriza said:**
> So what can you program with awk. The same as with bash or?
awk is a programming language that (as with any other) allows math, logic, and I/O. I haven't used it for many years, but when you hit limits with bash, awk will allow you to go further.

awk is a good programming language for scripting requirements. If you want to program heavily in bash, awk is a good thing to learn. It does seem a little clumsy at first, but once you get your head around it, it's easy.

Of course, there are other programming languages out there, but awk fits nicely with bash.

---

### Post by Drenriza on 2010-06-08
Isee.

Quick question tho.

If i want to get an output of 2 different things with awk from a single line, how do i do that?

```
who | awk '{ print $1 }'
```
This prints the first row. But how do i also get it to print the second row along with the first one? in one command.

---

### Post by Paddy Landau on 2010-06-08
Sorry, it's so long since I used awk that I don't remember.

You may want to go carefully through the manual, and look up awk tutorials on Google. It's not complicated.

These questions really don't belong in this forum.

---

### Post by Drenriza on 2010-06-08
> **Paddy Landau said:**
> 

These questions really don't belong in this forum.

I know but i cant move the thread, and you were here so.

---

### Post by iponeverything on 2010-06-08
> **Drenriza said:**
> Isee.

Quick question tho.

If i want to get an output of 2 different things with awk from a single line, how do i do that?

```
who | awk '{ print $1 }'
```
This prints the first row. But how do i also get it to print the second row along with the first one? in one command.

who | awk '{ print $1" "$2 }'

---

### Post by Drenriza on 2010-06-08
> **iponeverything said:**
> who | awk '{ print $1" "$2 }'

Super. Thanks mate

---

