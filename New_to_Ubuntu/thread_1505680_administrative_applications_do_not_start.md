---
title: "administrative applications do not start"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by kingaddi on 2010-06-09
I recently upgrading from Ubuntu 7.04 to 8.04 and everytime I try starting "administrative application", after a short time the message in the taskbar disappears and no program has started.  I am using gnome.

I know that I did not give all the information needed to troubleshoot so please bear with me and ask me question.

---

### Post by SlidingHorn on 2010-06-09
might be my own ignorance, but I don't know what this "administrative application" is...have any details about it?

---

### Post by kingaddi on 2010-06-09
From the drop down menu I go to system-->administration--->hardware drivers or hardware testing or synaptic package manager.

Those particular ones are not working.

> **SlidingHorn said:**
> might be my own ignorance, but I don't know what this "administrative application" is...have any details about it?

---

### Post by sydbat on 2010-06-09
> **kingaddi said:**
> From the drop down menu I go to system-->administration--->hardware drivers or hardware testing or synaptic package manager.

Those particular ones are not working.To clarify, you can click on these, but they are not opening, correct?

Also, you say you "upgraded" from 7.04 to 8.04. How long ago was this? I did not think that was possible, as you would have to go 7.04 > 7.10 > 8.04, and the repos for 7.04 and 7.10 have been out of service for well over a year. If you were able, I imagine this has caused some kind of corruption somewhere and is creating your difficulties.

However, if you had a 8.04 CD and did a clean install, that would be different.

Finally, have you considered updating to 9.10 or 10.04?

---

### Post by Gone fishing on 2010-06-09
I suggest you open a terminal and run gksu synaptic and if it doesn't open past the error message on the forum

---

### Post by kingaddi on 2010-06-09
I tried your suggestion and the results are exactly the same.

> **Gone fishing said:**
> I suggest you open a terminal and run gksu synaptic and if it doesn't open past the error message on the forum

---

### Post by kingaddi on 2010-06-09
I was able to upgrade from 7.04 to 8.04 by clicking on the upgrade manager.  

But on another note I notice that I no longer have super user access.

> **sydbat said:**
> To clarify, you can click on these, but they are not opening, correct?

Also, you say you "upgraded" from 7.04 to 8.04. How long ago was this? I did not think that was possible, as you would have to go 7.04 > 7.10 > 8.04, and the repos for 7.04 and 7.10 have been out of service for well over a year. If you were able, I imagine this has caused some kind of corruption somewhere and is creating your difficulties.

However, if you had a 8.04 CD and did a clean install, that would be different.

Finally, have you considered updating to 9.10 or 10.04?

---

### Post by Metrop021 on 2010-06-09
> **kingaddi said:**
> I tried your suggestion and the results are exactly the same.

there was no error message?

---

### Post by 29732 on 2010-06-09
I had the same problem, although I'm on 10.04 and i fixed that by uninstalling a corrupted program, WINE for me specifically 
  or maybe you should try Computer Janitor 

Try running it with this terminal command:
sudo computer-janitor-gtk

although it might not work in 8.04 because I've never used it

---

### Post by 29732 on 2010-06-09
wait, no super-user access???

well thats weird....

---

### Post by kingaddi on 2010-06-09
Good news I figured it out!

I was reading through this posting:
[https://bugs.launchpad.net/ubuntu/+bug/203593](https://bugs.launchpad.net/ubuntu/+bug/203593)

Apparently I was missing the following line from my /etc/hosts:

127.0.1.1 [insert computer name]


Once I added the information all my problems were solved.  As well it also solved the issue where I couldn't use the sudo command.

---

