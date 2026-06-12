---
title: "Few updates not installing"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by japhyr on 2010-03-08
Hello,

I am trying to finish installing 8.04.3 on an older computer.  It has finished updating except for 6 updates totaling 8.7MB.  The six updates are:

firefox, firefox-3.0, firefox-3.0-gnome-support, firefox-gnome-support, xulrunner-1.9, and xulrunner-1.9-gnome-support

Is there any reason these particular updates would not work?  I get a "failed to fetch" message for each of these.  I can still connect to the interent.  I notice they all come from security.ubuntu.com.

---

### Post by mörgæs on 2010-03-08
It could be a file transfer problem, plain and simple. What if you wait a  few hours and try again? 

Else: There is an 8.04.4 ready now, which will save you some updating:
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by japhyr on 2010-03-08
Waiting seems to have worked, but it led to another question.  I ran "sudo apt-get update", and it worked and installed updates.  I ran the command again, and it reported no updates.  Then I ran the update manager, and it reported 140MB of updates!  I thought "apt-get update" was the same as what the update manager was doing.  What is the difference?

---

### Post by Miljet on 2010-03-08
"sudo apt-get update" simply update the database on your computer on what is available. It does not install, or update, any programs.

"sudo apt-get upgrade" is the command to install any newer versions of programs that you already have installed.

```
man apt-get
``` is an interesting read.

---

