---
title: "help/need to open large text file"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-12
I have a 13mb text file, a log file. I don't want to use grep to output it to a smaller file since I unfortanuatly there isn't any good search criteria for me to filter out. So, here is the problem:


I try to open the file in gedit and gedit complains that it can't find the correct char encoding, which is ridiculous. I have been able to open it before, the problem is that it is so large. What is a text editor that can handle this?

---

### Post by viralmeme on 2010-03-12
> **TurnOfTide said:**
> I have a 13mb text file, a log file .. What is a text editor that can handle this?
Emacs ?

---

### Post by Lord DEA on 2010-03-12
try using Vim (console) or open office writer

---

### Post by jpkotta on 2010-03-15
> **ymitchell said:**
> Emacs ?

Emacs will work, but might be a bit slow.  One editor that always impresses me with its large file performance is Nedit.

---

### Post by finku on 2010-03-15
You might also use the following tips;

- Use less or more to view
- Use VI to edit
- Pipe less into grep ( grep <key_word> <file_name> | less -S ) and view only needed data
- use AWK and only view the needed bit ( awk '/start_pattern/,/stop_pattern/' file.txt )

In all cases, best hint is to use terminal :)

---

### Post by HermanAB on 2010-03-15
Howdy, since it is a text file, there is no structure to it, so simply break it up into smaller pieces with a utility called 'split'.

Read man split for details.  It is quite trivial.

---

### Post by mikemelen on 2010-03-15
use vim editor for read the file in terminal

vim filename | more
vim filename | less

---

