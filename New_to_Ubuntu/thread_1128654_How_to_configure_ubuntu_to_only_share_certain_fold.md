---
title: "How to configure ubuntu to only share certain folders between a dual boot system??"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by scrypt on 2009-04-17
I have just installed Ubuntu onto it's own partition next to my original Vista home premium.
 On a dual boot system with booting controlled by grub.

I chose to import all the avialable folders during the Vista to Ubuntu administrator account import.

I see that my Windows partition is easily available if I choose to mount it from the places drop down menu next to applications.

This has led me to wonder if this can cause any security problems by having all shared between my two partitions?
 
I installed Ubuntu for the obvious security benefits.
But if I can so easily access my Windows Vista Files and Folders

Is this quite dangerous from a security perspective??

Also How can I configure Ubuntu so that I only have One maybe Two folders that can be shared between my two installed OSes??

Because at present I can access pretty much anything on my Vista partition using Ubuntu.

Am I right to be this concerned?

What other security steps should a relative newcomer to sharing files and folders between Two Operating systems, on separate partitions take?

I have had a good read around on-line about this but I have not found anything aimed at complete newcomers to this issue.

Can anybody help me to understand how to safely secure the sharing process between Vista and Ubuntu??

---

### Post by swoll1980 on 2009-04-17
The only security problem you would have is if you had other users you didn't want to have access to that folder. Programs can't access it with out root privileges. Easiest way to prevent a problem is not to give programs root privileges. You can change the permissions of the folder using [chmod]("perlfect.com/articles/chmod.shtml") if you want it to be more secure, or less.

---

