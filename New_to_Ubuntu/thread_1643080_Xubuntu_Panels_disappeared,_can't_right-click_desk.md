---
title: "Xubuntu Panels disappeared, can't right-click desktop"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by campb.andrew on 2010-12-11
Hi everyone,

I installed Xubuntu 10.04 yesterday, and a few hours later when i was logging out, the panels (both top and bottom) disappeared after i clicked the log out button. I thought it was shutting down. But a few minutes later when nothing had happened, i right clicked the desktop, just trying to see what would happen, and clicked log out. The computer shut down after. 

However, later in the day, i tried logging in again, and when everything finished booting up, i couldnt see my panels, and i couldnt right click the desktop. I did some research via my phone and found out this is actually an on-going bug with Xubuntu. (You could have warned a guy :-x) I've tried the various solution people suggested about running the xfce4-panel command in terminal via "alt-f2". But the terminal opened and nothing happened. So i updated  to 10.10 via the update manager command, hoping to have the prob solved, and it didnt help. I got so frustrated that i re-installed 10.04 and here i am. 

But i would like to know what to do, to fix this problem, should it happen again. I'm new to linux on a whole and i know nothing about commands.

---

### Post by blackness on 2011-01-11
I recently had the same issue and resolved it with running the xfce4- panel command. if the problem shows up again try opening your terminal via right clicking your desktop and selecting it from the drop down list and type "xfce4-panel &" without the quotation marks. 
ps. check your auto-start entries to make sure your panels are there.

---

### Post by blackness on 2011-01-11
by auto-start I mean your start-up menu

---

