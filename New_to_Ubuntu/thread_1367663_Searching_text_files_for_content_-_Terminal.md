---
title: "Searching text files for content - Terminal"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-29
Hello,

I have large folder (/home/brad/database) that contains a ton of text files relating to various topics. 

What I want to do is search the text files for ones containing specific text: (e.g. "compile") and return the names of the files containing that text.

For example, lets say I have two files: A.txt, and B.txt

A.txt contains "hi"
and B.txt contains "hello"

Now I want to search the folder for all files containing the word "hello", and return a list of those files, which in this case would return B.txt . 

How can I do this using the terminal?

---

### Post by eeeandrew on 2009-12-29
Hi! This is done using the grep command. For more information on how to use the command type:
> man grep in a terminal. When your done reading you can press q to quit.

From what I can see you should use the -l option to have it return file names that match. So to do this you would open terminal change directory till your in the one you wanna search then use a command like this one.
> grep -l searchterm *.txt

where *.txt is wildcard which tells it to check all files of type .txt.
where searchterm is the term your looking for(in quote marks if theres a space ie. "search term")
Hope this helps

---

### Post by leef on 2009-12-29
```
find /home/brad/database | xargs grep hello | uniq
```

not sure tho bud.

---

### Post by darkeye123 on 2009-12-29
Thanks a lot guys :)

The command that worked for me was the one eeeandrew posted.

Thanks again!

---

### Post by Iyunkateus on 2009-12-29
> **darkeye123 said:**
> Hello,

I have large folder (/home/brad/database) that contains a ton of text files relating to various topics. 

What I want to do is search the text files for ones containing specific text: (e.g. "compile") and return the names of the files containing that text.

For example, lets say I have two files: A.txt, and B.txt

A.txt contains "hi"
and B.txt contains "hello"

Now I want to search the folder for all files containing the word "hello", and return a list of those files, which in this case would return B.txt .

How can I do this using the terminal?
Try this:
```
grep -l compile *
```This searches all files for "compile", and the [FONT=Courier New]-l[/FONT] option shows just the file names that matched, while [FONT=Courier New]grep[/FONT] usually shows where it matched as well.

---

### Post by garryknight on 2009-12-29
The advantage to using **find** with **grep **is that while grep only looks in the directory you point it at (or the current directory as a default), the find command digs down through subdirectories too. And, of course, that can be a disadvantage.

---

### Post by tom.swartz07 on 2009-12-29
> **darkeye123 said:**
> Thanks a lot guys :)

The command that worked for me was the one eeeandrew posted.

Thanks again!

And this is why I love the terminal.

---

