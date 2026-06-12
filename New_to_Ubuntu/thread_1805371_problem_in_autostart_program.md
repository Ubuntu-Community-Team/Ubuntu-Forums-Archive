---
title: "problem in autostart program"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by pua06 on 2011-07-15
salmo allikm warhmat allah wabrakato

i have problem
i add motion program in auto-start menu to start in boot
when use commend line in terminal to work motion 
sudo motion
the images save in tmp/motion
but after auto start it saves in home directory i don't know why and if open tmp directory motion directory not exist 

thanks so much

---

### Post by varunendra on 2011-07-16
A Startup application is started in user mode, so it uses the user's home directory for most of its create/modify/delete activities, while "sudo" or "gksu" runs it as 'root'. I'm not 100% sure, but this should be the reason for your problem.

Try running the program without "sudo".

---

