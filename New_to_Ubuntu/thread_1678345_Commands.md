---
title: "Commands"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Karlof on 2011-01-30
Hi forum I cannot Get sudo apt -get clean to work in the terminal command

Message unable to open downloads E lockdown

Help please thanks

---

### Post by Perfect Storm on 2011-01-30
you need to close Ubuntu Software Center or/and Synaptic Package Manager. These things can't run at the same time.

---

### Post by Stephen Morgan on 2011-01-30
On my system Software Centre and apt-get clean work perfectly well at the same time.  Actually, I can get it to not work now I try, but only by running apt-get while actually installing/removing software is in progress in software centre (not with the programmes reversed, Software Centre waits for apt-get to finish).  The error message looks like this:  E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable) E: Unable to lock the download directory  So if that's what the OP's seeing he's got his answer.

---

### Post by Karlof on 2011-01-30
Hi forum
 
I cannot make the command apt-get clean work

Message E locked out  cannot access downloads

help please

thanks

---

### Post by [Snc] on 2011-01-30
> **Karlof said:**
> Hi forum
 
I cannot make the command apt-get clean work

Message E locked out  cannot access downloads

help please

thanks

Have you tried with
```
sudo apt-get clean
```
?

---

### Post by davec64 on 2011-01-30
As Sncs said make sure you use "sudo" and also make sure you haven't got Synaptic, Software Centre or Update Manager open. :)

---

### Post by Karlof on 2011-01-30
Hi forum 

tried sudo, zero result

Next please

---

### Post by Karlof on 2011-01-30
Hi steve 

with respect your answer is beyond a newbie like me

---

### Post by howefield on 2011-01-30
Threads merged, please resist the urge to post duplicate threads. :)

---

### Post by [Snc] on 2011-01-30
> **howefield said:**
> Threads merged, please resist the urge to post duplicate threads. :)

lol :)

well, the merged answer should be:

Synaptics, Update manager and apt-get (in the terminal) cannot run at the same time, since they make changes to the same resource, so close Synaptics and/or software Update manager and make sure you have administrator rights, when updating with apt-get (use sudo)

---

