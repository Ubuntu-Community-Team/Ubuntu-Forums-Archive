---
title: "could not authenticate an unexpected error has occurred"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by ArielEnter on 2009-10-19
I was having the following message when trying to change my users and groups from System>Administration>Users and Groups:

could not authenticate an unexpected error has occurred

The message used to pop out when trying to unlock more options from the user and groups dialog. I solved it and I wanted to share it in the forum since it was hard for me to find what was going on. 

It came out that I didn't have policykit-gnome installed.

I think this was a very basic problem, but I'm a very novice user of Ubuntu and this forum, that's the reason I posted here first. So please if this thread didn't suppose to go here, is repeated, or I'm making bad use of the forum, kindly let me know.

I don't know how policykit-gnome got uninstalled. But I'll post my version of Ubuntu.

Ubuntu 9.04 - Jaunty Jackalope

---

### Post by alanbrodbeck on 2009-11-04
before getting too deeply involved  with polkit
Try:

Applications => Accessories => Terminal
When the terminal window appears type:
$ passwd

after being prompted to change my password I was able to properly unlock Users and Groups.

---

