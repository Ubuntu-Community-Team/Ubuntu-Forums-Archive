---
title: "Minimizing Sunbird At Startup"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-01-03
This post was originally me posing this question to more experienced Ubuntu users.  Since I never received a response, through some searching over the Internet, I found the answer, and am posting this for anyone else who might be interested.  It's really very simple...in Session Manager, click on "Add", and for "Command", put "kdocker -l [program] (This will be whatever program you would like to run at startup and automatically minimize to the System Tray).  For instance, I wanted Sunbird to not only automatically load at startup, but also minimize without me having to click on kdocker and then click on Sunbird.  So I entered:

kdocker -l sunbird

This really works!!! :KS

---

### Post by blueridgedog on 2009-01-03
Thanks for the investigation and for taking the time to share it.

---

