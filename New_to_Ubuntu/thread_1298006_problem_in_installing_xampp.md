---
title: "problem in installing xampp"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by itsme33 on 2009-10-22
hi ,
please help to install xampp perfectly.actually i have a problem,when i tried to install xampp. the problem is 

itsme@itsme-laptop:~/Desktop$ sudo tar xvfz xampp-linux-1.7.1.tar.gz -C /opt
tar: xampp-linux-1.7.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by lovinglinux on 2009-10-22
> **itsme33 said:**
> hi ,
please help to install xampp perfectly.actually i have a problem,when i tried to install xampp. the problem is 

itsme@itsme-laptop:~/Desktop$ sudo tar xvfz xampp-linux-1.7.1.tar.gz -C /opt
tar: xampp-linux-1.7.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I have just installed xampp following [this tutorial](http://ubuntuforums.org/showthread.php?t=223410).

Make sure you have a file **xampp-linux-1.7.[B]1**.tar.gz[/B] in the directory you are running the command from (in this case ~/Desktop)? The current version of xampp is 1.7.**2**, so check if the file you have is 1.7.1 or 1.7.2 and change the command accordingly.

---

### Post by kellemes on 2009-10-22
Tab-key can be so handy in situations like this..
[http://blogs.pcworld.co.nz/pcworld/tux-love/2008/02/hidden_linux_tabcompletion.html]("http://blogs.pcworld.co.nz/pcworld/tux-love/2008/02/hidden_linux_tabcompletion.html")

---

### Post by buzzing_bee on 2011-10-07
so i'm done with installing xampp 1.7.7 and success to connect to [http://localhost](http://localhost) but when i click on phpMyAdmin, **its language is on Germany**, i've choose the language to English when the first time connecting to [http://localhost](http://localhost)

how to change the language on phpMyAdmin become English??


sorry if my English so bad..:biggrin:

------[color=red]SOLVED[/color]-------------
i'm sorry but i've solved this problem..my eyes didn't see that there's a box for changing the language...
i'm an amateur...

---

### Post by lovinglinux on 2011-10-10
Since buzzing_bee solved the problem is this thread is 2 years old, I am closing it.

---

