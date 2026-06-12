---
title: "Pipes in linux vs pipes in windows"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by gidra on 2009-05-01
I'm doing my assignment about linux and here pops out this question : What is the difference with pipes under Linux compared to Windows pipes ? 

I tried to google a litte but didn't find definite answers. Btw there also is these 2 commands : ls -al|grep 2003 , ls -al|sort -k 4,4| more . I can't figure out what the heck they're supposed to do.

Thanks for your help

---

### Post by kanikilu on 2009-05-01
We're not really here to do homework, but I can point you to some resources:

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

[http://www.linuxcmd.org/](http://www.linuxcmd.org/)

This one specifically has a section on piping and redirecting:

[http://jucato.org/blog/ubuntu-classroom-command-line-basics/](http://jucato.org/blog/ubuntu-classroom-command-line-basics/)

Also, **man** is your friend - look up the man pages for commands you don't understand. You're not really going to learn anything if we just *tell* you what a command does. E.g. ```
man sort
```

Once you know what a pipe does in Linux, see what it does in Windows, and compare:

[http://technet.microsoft.com/en-us/library/bb490982.aspx](http://technet.microsoft.com/en-us/library/bb490982.aspx)

*BTW, these links were found in 2 quick Google searches - obviously one can't know *everything*, so the trick is knowing where and how to find answers...

---

### Post by gidra on 2009-05-01
Aye thanks, i'll read them through

---

### Post by Spiritous on 2009-05-01
Isn't this cheating ;o?

---

### Post by Dougie187 on 2009-05-01
Lol, yes it sort of is cheating. I think it's even in the code of conduct to not post homework questions.

---

### Post by Niniel on 2009-05-01
Knowing where to look for/ask for answers... that can't be cheating. :)

---

### Post by jhenager on 2009-05-01
At least this wasn't comparing screensavers....

Piping in Windows owes it's roots to CPM, which was the foundation for the original DOS (which wasn't very original).

Piping in Linux is patterned after UNIX.

If you use my answer and get a D-, I deny all complicity.
If they would have had computers when I was in high school, my CTRL, C and V keys would have been completely worn out.

---

### Post by gidra on 2009-05-02
I don't think asking for help is a form of cheating. Anyways i managed to find my way through to solve the problems using the above links. thanks

---

