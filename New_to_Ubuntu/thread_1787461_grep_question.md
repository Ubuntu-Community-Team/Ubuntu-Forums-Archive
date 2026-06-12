---
title: "grep question"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by xxsawer on 2011-06-21
Hi, I am having this problem... 
I want to search files in some directory for couple of strings, so I use:

[FONT=Courier New]grep -irne string1 -e string2 -e string3 *[/FONT]

Now I would like to get the results sorted according to the strings being searech. So I want first get lines containing string1, then lines containing string2 and so on...
Can this be somehow done?
Thanks for help.

---

### Post by nothingspecial on 2011-06-21
Why not run the command 3 times and dump the output in a file, appending (>> rather than >) the second 2 results. 

```
grep -irne string1 * > grep.txt && grep -irne string2 * >> grep.txt && grep -irne string3 * >> grep.txt
```

---

### Post by xxsawer on 2011-06-21
Thanks, this will be perfect in most cases :)
However if I use pattern file it will not work

[FONT=Courier New]grep -irnf paterns.txt *[/FONT]

If there is no other option, this is sufficient for me

---

### Post by DaithiF on 2011-06-21
when you grep for multiple patterns at a time grep reads each line once and checks all the patterns against that line before moving on to the next line.  So you can't get the behaviour you want using grep, other than by running grep multiple times as nothingspecial suggests.

if you have many patterns in a file you can script the multiple invocations of grep to cut down on typing, e.g. something like:
```
while read pattern
do
   grep -irn "$pattern" * >> outputfile
done < patternfile

```

---

### Post by nothingspecial on 2011-06-21
I think I learn more answering these sorts of questions than I ever would asking them ........... :D

---

### Post by xxsawer on 2011-06-23
Perfect, thanks for explanation :)

---

