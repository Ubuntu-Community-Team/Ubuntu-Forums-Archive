---
title: "using pipes_?"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by quartaela on 2011-03-31
i have a homework assignment to tomorrow but i can't finished it. i guess i have a problem about using pipes. in our assingment there are some instructions we must to do but i can't managed two of them which are;

3. Download the file from  [http://cse.yeditepe.edu.tr/~oturkes/spring2011/cse232/week7/rms.txt](http://cse.yeditepe.edu.tr/~oturkes/spring2011/cse232/week7/rms.txt) using “wget” 
command as a background process.
4. Write the last ten lines which contain the word “free” in the downloaded file to a new text file named free.txt

i downloaded the file with;

"wget [http://cse.yeditepe.edu.tr/~oturkes/spring2011/cse232/week7/rms.txt](http://cse.yeditepe.edu.tr/~oturkes/spring2011/cse232/week7/rms.txt) &"

so i write "$grep free rms.txt | tail -10 free.txt" but i doesn't working. i guess i must use pipes which i know the output of the first command is the input of the second command. logically it must do the instruction succesfully. :). please help

---

### Post by r-senior on 2011-03-31
You are almost there. If you enter this part of your command:

```
$ grep free rms.txt | tail -10 
```

you should find it works. So now all you need to do is redirect the output of that pipe to a file. As it's homework, I won't tell you exactly how ;), but it's not a pipe.

```
$ man bash
```

Then hit '/' and type REDIRECTION (case is important). Hit '/' followed by <return> until you get to the section entitled REDIRECTION that gives you the answer.

---

### Post by quartaela on 2011-03-31
well ok i wrote "$ grep free rms.txt | tail -10 > free.txt" and it worked!. thanks a lot :)

---

### Post by JKyleOKC on 2011-03-31
The "$" at the start of each line is a prompt character; you don't need to type it in. This is true in all the threads I've seen from you so far; your instructor should have made this point clear. It would actually be possible for someone to create a command named "$" and then typing it in would execute that program, instead of what you intended to do!

---

### Post by quartaela on 2011-03-31
> **JKyleOKC said:**
> The "$" at the start of each line is a prompt character; you don't need to type it in. This is true in all the threads I've seen from you so far; your instructor should have made this point clear. It would actually be possible for someone to create a command named "$" and then typing it in would execute that program, instead of what you intended to do!

ok this is a usefull information :). thanks for warning

---

