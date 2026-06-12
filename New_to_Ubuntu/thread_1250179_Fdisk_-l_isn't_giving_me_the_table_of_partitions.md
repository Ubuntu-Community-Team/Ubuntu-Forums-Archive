---
title: "Fdisk -l isn't giving me the table of partitions"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Clixer on 2009-08-26
Hi guys, i'm a newbie of the Ubuntu world, and I want some help for my problem:
 
I installed the 9.04 version of Kubuntu, Jaunty Jackalope, and everything went fine, but when I try to install some programs using the bash shell, I use the command su or sudo, and then my keyboard doesn't write any letter i press, for the password.
 
Instead, if I try to install it, using the graphical method, with KPackage, it writes my root password! Maybe a problem with the keyboard??
 
Help me, thank you!

---

### Post by mcduck on 2009-08-26
When you type your password in a terminal nothing is even supposed to be printed on screen.

Just type the password and press Enter, and it will work. :)

---

### Post by bumanie on 2009-08-26
There is no visual output when typing your password in terminal. Also, just in case you don't know fdisk -l should have a lower case "F"

---

### Post by Clixer on 2009-08-26
Oh what a fool, i am! I forgot something!
fdisk also (I used F capital letter without thinking) isn't giving me any table of partitions, that is when i write in terminal "fdisk - l" with L lowercase letter, it doesn't give me the partitions table. What I get is only the [EMAIL="utent@utentdesktop"]utent@utentdesktop[/EMAIL]: and stop!

---

### Post by Bartender on 2009-08-26
Do you get the same strange error with any other terminal command?

---

### Post by mcduck on 2009-08-26
> **Clixer said:**
> Oh what a fool, i am! I forgot something!
fdisk also (I used F capital letter without thinking) isn't giving me any table of partitions, that is when i write in terminal "fdisk - l" with L lowercase letter, it doesn't give me the partitions table. What I get is only the [EMAIL="utent@utentdesktop"]utent@utentdesktop[/EMAIL]: and stop!

You need to run it with "sudo".

```
sudo fdisk -l
```

---

### Post by Clixer on 2009-08-26
EDIT: Sudo isn't giving problem to me anymore, and fdisk -l shows me the partitions, all resolved!
 
Thank you for the advice Mark!

---

### Post by Mark Phelps on 2009-08-26
Folks provide responses here based on the thread titles.  Instead of going off on an entirely different tangent, you would do better starting a new thread.  That way, folks that know how to solve your new problem will see the new thread and respond.

Also, since this is a networking issue, you should go to the networking subforum and do a search on Conexant before posting.  You just might find posts that already deal with the problem.

---

