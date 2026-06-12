---
title: "How to redirect program output?"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by thunder87l on 2010-10-27
I've made a python program, and set it to run on autostart. It's supposed to write some messages in terminal tty0. How do I redirect messages it produces into tty2 without modifying the code?

To run code at autostart I've made a bash script containing: *python location/code.py*
then changed rights with *chmod 755 script*, then put it into */etc/init.d* and run *sudo update-rc.d script defaults* Maybe there is a way to redirect output in the autostart script, or in the way it is installed in system?

---

### Post by Geoff918 on 2010-10-27
No offense, but this probably should be in another forum. This probably isn't an "Absolute Beginner Talk" level question.

---

### Post by Hippytaff on 2010-10-27
> **thunder87l said:**
> I've made a python program, and set it to run on autostart. It's supposed to write some messages in terminal tty0. How do I redirect messages it produces into tty2 without modifying the code?

To run code at autostart I've made a bash script containing: *python location/code.py*
then changed rights with *chmod 755 script*, then put it into */etc/init.d* and run *sudo update-rc.d script defaults* Maybe there is a way to redirect output in the autostart script, or in the way it is installed in system?

I tried the same thing with a bash script but it wouldn't output to a terminal, I'm not sure whether init.d is for daemons rather that interactive programmes!?

---

### Post by TiBaal89 on 2010-10-27
I'm away from my terminal to test for sure, but I think that's just a matter of redirecting (i.e. ">") into /dev/tty2.  It's a fairly common thing, I bet it is easily google-able...

---

### Post by Hippytaff on 2010-10-27
you can use > to change the sdout within the script, but the sdout is the terminal, so > would send it to a txt file for example.

---

