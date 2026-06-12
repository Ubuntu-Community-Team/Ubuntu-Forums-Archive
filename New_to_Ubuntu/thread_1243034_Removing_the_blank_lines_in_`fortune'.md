---
title: "Removing the blank lines in `fortune'"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by harry71194 on 2009-08-17
Okay, hi. When I execute a fortune, it puts out into many lines into IRC, despite the length and screensize.

I run the command

/exec -o fortune -s | sed 's/\t//g' | sed 's/\n//g'

That SHOULD remove all the newlines, that cause my fortune to look like this, right?
> 21:12:36 You can't erase a dream, you can only wake me up.
21:12:36 -- Peter Frampton
See, even though I remove the newline character, \n, it still makes 2 or more lines. (the removal of \t is so I do not get an error in some rooms).



So help me exec fortune all into 1 message please! :) I have tried everything to fix it.


Thanks in advance.

---

### Post by harry71194 on 2009-08-18
Oh awesome. echo == awesome.

/exec -o echo `fortune -s` | sed 's/\t//g' | sed 's/\n//g'

---

### Post by DaithiF on 2009-08-18
and just to explain why your sed approach won't work ... its not possible to strip newlines using sed like that, since sed operates on one line at a time, there isn't actually any newline character in each line for it to replace.

you *can* make sed do what you want in a slightly more convoluted way:
```
sed ':a;N;$!ba;s/\n//g' somefile
```

:a   create a label to branch back to later
N    read in the next line and add it to the pattern space
$!ba   for every line except the last, branch back to the start of our expression (ie. keep on reading in subsequent lines)
s/\n//g on the last line, remove all newlines from pattern space (and print the result)

```
cat somefile | tr -d '\n'

```is almost an equivalent, except that you don't get a final newline this way

---

