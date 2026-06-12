---
title: "ping differences between dapper and feisty"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by autoexec on 2007-07-06
hello

in dapper, im able to use firefox to go to
vista.elearning.unsw.edu.au
totally fine
but with fiesty its times out


anyone have any idea what happening?
or how i could find out?

---

### Post by autoexec on 2007-07-08
[www.timetable.unsw.edu.au](www.timetable.unsw.edu.au)
also exhibits the same behaviour.

---

### Post by autoexec on 2007-07-17
found a fix for it
go to the terminal and type:

sudo gedit /etc/sysctl.conf

then add this line:

net.ipv4.tcp_window_scaling = 0

---

### Post by mr.sp3aker on 2007-07-22
I would like to say thanks autoexec... I spent days messing about trying to figure out why my newly upgraded Ubuntu box couldn't get to timetable.unsw.edu.au - your fix worked like a charm! GOLD STAR :KS !

---

