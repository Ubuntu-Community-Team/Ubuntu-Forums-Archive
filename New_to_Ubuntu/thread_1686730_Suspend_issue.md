---
title: "Suspend issue"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by uam on 2011-02-12
.

---

### Post by tednix on 2011-02-13
Welcome to the forums.

I too am interested in a fix for my suspend problems for my Toshiba laptop.  I have been searching for a solution for several weeks now.  What I've noticed is that most requests for help with suspend either go unanswered or are not solved.

Evidently laptop hardware is so variable that linux can not keep up with all of the necessary drivers and the manufacturers don't provide support.

Until then rebooting seems to be the solution.

---

### Post by hansolo4949 on 2011-02-13
Have you installed uswsusp? That worked for me!

---

### Post by tednix on 2011-02-13
Thanks hansolo4949.  I installed it through the software center and will give it a try.

I noticed that the last update was over 3 years ago.  I hope that it works on my 2 y.o. laptop.  My suspend problems are intermittent so it may take a while to determine if this is going to work.

I did not find any listing in my menus after installation so I guess that there is no user input or control.

---

### Post by uam on 2011-02-14
.

---

### Post by Habeouscorpus on 2011-02-14
The program I use to suspend is called acpitool. You can get it through the repostories. Unfortunately, you have to do it as root, and through the commmand line.

But! I have a solution. 

Create a desktop launcher, and input the command ```
gksu acpitool -S
```

This is your hibernation.

Create another launcher, and input ```
 gksu acpitool -s
```

This is your suspend. 

Now, all you have to do is double click, and enter your password. Presto! Prefect hibernation.

---

### Post by uam on 2011-02-15
.

---

