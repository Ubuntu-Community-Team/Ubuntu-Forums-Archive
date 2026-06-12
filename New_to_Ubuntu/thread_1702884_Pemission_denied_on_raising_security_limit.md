---
title: "Pemission denied on raising security limit"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Replicator Fifth on 2011-03-08
hello, 
I am brand new to linux and am starting on ubuntu (<3 free os!) 
Okay, Windows crashed on me 2 week ago and I installed Ubuntu 10.10. I am still learning it in my free time (between classes and HW and work o_o)  its a great OS and I love it so far but, I can't seem to figure out why it won't let me raise the security limit for my user as per instructed to install Aion on the WineHQ page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877). currently on step 4 username soft nofile 8192, ect, it returns permission denied I've tried both as root and a my regular user. can someone help me? Thanks 
 
If this has already been solved plese link me to that forum thread?
 
yes, I have wine tricks and yes, I followed the instruction on nclauncher.wikispaces.com and I think it worked >_>. 
 
thanks again 
 
Regards, 
Joanna

---

### Post by wormyblackburny on 2011-03-08
**gksudo gedit /etc/security/limits.conf** and add the lines as instructed, save and close. I imagine you were probably trying to edit the file as your regular user account. since the file is owned by root, you need to use sudo to edit it. Hope this helps :)

---

### Post by Replicator Fifth on 2011-03-08
alright, I'll try it thanks for the speedy responce.

---

### Post by Replicator Fifth on 2011-03-08
okay I had to get home to actually try it as I was at school. so I entered that and the commands and I get a window titles nofile (/home/username) - gedit, what do I do now? its showing just a text file and a whole bunch of empty windows with titles from my command line like username and soft and nofile...is that right? again thanks

---

### Post by wormyblackburny on 2011-03-10
Well, if it opened, that is a plus. I'm not sure what the format of the text file should look like as I'm not in front of my Ubuntu box, but from the looks of the instructions just add the lines to the bottom of it and save....

---

