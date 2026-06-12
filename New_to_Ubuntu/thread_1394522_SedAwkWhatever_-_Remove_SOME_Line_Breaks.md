---
title: "Sed/Awk/Whatever - Remove SOME Line Breaks"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by wbryan6 on 2010-01-30
This seemed like as good a place as any to ask this question.  Let's say you have a text file that contains the following:

```
Hello
World
Hello 
World
Hello 
World
```

What is one way that you can turn this into:

```
Hello World
Hello World
Hello World
```

Not all line breaks are removed.  Only the ones that are between "Hello" and "World" are replaced by spaces.  Any ideans?

---

### Post by llamabr on 2010-01-30
Maybe this problem is more complicated, but this sounds like a job for your text editor, not for sed and awk.  in nano, or emacs will come with search and replace.

If you explain your actual problem, we can probably code something up.

---

### Post by Mornedhel on 2010-01-30
A perl one-liner does the job.

Cute one:

```
perl -ne 'chomp and print "$_ " and next if /Hello/; print' filename.txt
```

Practical one:

```
perl -ne 's/\n/ / if /Hello/; print' filename.txt
```

Replace /Hello/ with a regular expression that suits you better if necessary.

---

### Post by wbryan6 on 2010-01-30
Sorry if this sounds ignorant, but I typically use vi for my console text editing and am not overly comfortable with nano or emacs.  I could probably learn how to do a simple search and replace with one of them, but this seems to be a reoccurring issue in some of my scripting and I don't always have the ability to edit the text file in question.

Basically, like my example, I have a text file where I have repeated occurrences of a line break getting in the way of manipulating a string of text.  In the case of what I'm doing now, I have addresses listed as:
```
123 Main St.
Your Town, USA 12345
```

I would prefer to store this as:
```
123 Main St. Your Town, USA 12345
```

All other line breaks in the file are not a problem, just the one that breaks the address apart.

---

### Post by wbryan6 on 2010-01-30
Thank you Mornedhel.  I'll give that a try.

---

### Post by wbryan6 on 2010-01-30
Works like a champ!  Thanks again.

---

### Post by DaithiF on 2010-01-31
just to add a sed equivalent:
```
sed '/Hello/N;s/\n/ /' somefile
```
...match lines containing Hello, for each of these, read in the following line and replace the newline between the 2 with a space.

---

