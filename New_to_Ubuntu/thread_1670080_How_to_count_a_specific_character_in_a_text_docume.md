---
title: "How to count a specific character in a text document"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-01-18
Probaly seems like a weird question but is there a terminal command to count specific characters in a text document, for example i have a text document that consists of about 3000 lines of: 1,1,1,0,0,1,0,1,1,0,1,0,0 etc.
is there a command that i can run once to count the 0's and once to count the 1's?
Thanks 
Mark

---

### Post by apmcd47 on 2011-01-18
To count the zeroes:```
tr -d '1' < file.txt | wc -c
```
To count the ones:```
tr -d '0' < file.txt | wc -c
```

*tr* is short for translate and is normally used to change one set of characters into another, but it can be used to delete characters from a file as used here. *wc* is short for word count, but it counts words, characters and lines.

Andrew

Actually, thinking about it, the above will also count newline characters and other characters not in the above sets. Try ```
< file.txt wc -c
``` to get the total size and subtract the above from it.

---

