---
title: "Are the installed programs accesible for all?"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-07-03
Good morning,

I have just a quick question. I am setting up a multi-user desktop. This is the first time that I have done it in Ubuntu. I normally only need the system for myself and therefore have usually just had one user/account - mine.

But now, I have convinced a friend and their family to use Ubuntu because XP was just saturated and they didn't have a recovery CD to re-install, so Ubuntu was a logical choice.

Anywho, what I am going to do is set up the parents as the primary user and then set up separate accounts for the three children. The parents will have admin access, when necessary, but the children will not.

What I want to know and have never really looked into before is, if the parents install a program, such as a game, image editor, etc (i.e. Alien Arena, GIMP, Ubuntu Tweak, etc.) while logged into their desktop, will that game/program also be accessible for the other users, in this case the children, when they log into their desktop? Or do I need to add them to a certain group to have access to the programs?

Also, if the parents install a program that only they want access to and not the children, how would I go about doing that? I really don't want to have to change the permissions manually because that will take a long time. Thanks for the help! :D

-Spydey

---

### Post by bodhi.zazen on 2010-07-03
In general, yes, but there are some exceptions.

If you use the repositories, then any installed applications should be available to all.

If, however, you install from source or you download a binary (such as firefox) it depends on where you place it and the permissions of the directory you assign.

For example, if you place the firefox binary in your home directory, and your home directory has permissions of 770 / 660 then, firefox will NOT be available to all.

With what you are planning you should be fine.

There may be some administrative applications which the children will not be able to access, which is probably what you want.

---

### Post by spydeyrch on 2010-07-03
Perfect! That is exactly the type of answer and information that I was looking for. Thanks for the clarification. :p

> 
There may be some administrative applications which the children will  not be able to access, which is probably what you want. 	


So if I understand you correctly, even if the parents install an admin application via the repos, due to it being an admin app and the children's accounts being non-admin, then they should not be able to see them, right?

I am not at home right now, so I can't check personally, but if I wanted to give one of the children admin rights, what group(s) would I add him to? Thanks. :)

-Spydey

---

### Post by bodhi.zazen on 2010-07-03
> **spydeyrch said:**
> Perfect! That is exactly the type of answer and information that I was looking for. Thanks for the clarification. :p



So if I understand you correctly, even if the parents install an admin application via the repos, due to it being an admin app and the children's accounts being non-admin, then they should not be able to see them, right?

I am not at home right now, so I can't check personally, but if I wanted to give one of the children admin rights, what group(s) would I add him to? Thanks. :)

-Spydey

Children can see the applications, they can start them, but they will then be asked for their password. Since they are not in the admin group, the admin apps will not run.

---

### Post by spydeyrch on 2010-07-03
That is what I figured. Thanks for your help.

I am going to mark this thread as solved.

-Spydey

---

