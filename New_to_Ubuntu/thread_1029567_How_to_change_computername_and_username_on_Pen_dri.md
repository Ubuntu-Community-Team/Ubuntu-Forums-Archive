---
title: "How to change computername and username on Pen drive"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by mihashise on 2009-01-03
I've installed pen drive Kubuntu 8.10 on my USB. It works perfectly, the only thing that disturbs me now is how to change computername and username. 
I would like to change both in order to make the ssh more convenient and I do not want to look at ubuntu@ubuntu all the time. 
I have tried to edit /etc/hostname but after booting I was welcomed by ubuntu@ubuntu again and also the /etc/hostname changed back to ubunto although I have done the sudo editing. 

2. question: How to change username from ubuntu to something else.


Thanks for the answers,

Miha

---

### Post by ithanium on 2009-01-03
for the second question go to System > Administration > Users and Groups. Select your username and press Properties
i don't know if it's the same for **k**ubuntu :(

---

### Post by mihashise on 2009-01-03
Unfortunately I can not find System > Administration > Users and Groups.

Well, I can go to K-menue, Applications, System, User Manager and choose ubuntu user but it is impossible to change it.
Am I doing something wrong?

Miha

---

### Post by sexcopter on 2009-01-21
> **mihashise said:**
> I've installed pen drive Kubuntu 8.10 on my USB. It works perfectly, the only thing that disturbs me now is how to change computername and username. 
I would like to change both in order to make the ssh more convenient and I do not want to look at ubuntu@ubuntu all the time. 
I have tried to edit /etc/hostname but after booting I was welcomed by ubuntu@ubuntu again and also the /etc/hostname changed back to ubunto although I have done the sudo editing. 

2. question: How to change username from ubuntu to something else.


Thanks for the answers,

Miha

I'm going to be upfront and say now that I don't know for sure how USB live installations "work", but I have an idea what your problem *might* be.

I think that there is a kind of Ubuntu image that is written to the pen drive when you install it initially, and when you start it up, it extracts the contents into your memory for the live session. As such, when you change files, it's only changing the current instance of Ubuntu, not the files on the USB drive.

If I'm right, then you would have to modify files in the Ubuntu iso before making the USB drive. Actually, there may be other ways, but all of this is way beyond my scope. It might point you in the direction to look further though.

Good luck,

James

---

