---
title: "Help please!"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by gagea on 2010-04-02
Hello, 	 	 	  


 I was working in R and after finishing my work, I wanted to quit the program. By executing the q() command, I got the following message.  
 

 > q() 
 Save workspace image? [y/n/c]: y 
 Fri Apr  2 23:04:54 2010  
 Adios 
 Error in gzfile(file, "wb") : cannot open the connection 
 In addition: Warning message: 
 In gzfile(file, "wb") : 
   cannot open compressed file '.RDataTmp', probable reason 'Permission denied' 
 

 I am not using the root acocunt, instead I opened my own account on the computer. Is there anybody can tell me what is the problem and how can I fix it? Thanks a lot.  
 

 Gagea

---

### Post by tommynz1975 on 2010-04-02
May I ask what the program R is??

If you opened a program in Terminal

one would use
sudo
in front of the program they are opening, sudo would tell the system you are in control and are allowed to edit the file  in question.

---

### Post by gagea on 2010-04-02
> **tommynz1975 said:**
> May I ask what the program R is??

If you opened a program in Terminal

one would use
sudo
in front of the program they are opening, sudo would tell the system you are in control and are allowed to edit the file  in question.


Dear friend,

Thanks a lot for advice. It is now working with sudo. Previously I call program without sudo and it did work, but could not save changes to file. But it is now working. 
This is R: [http://www.r-project.org/](http://www.r-project.org/)


Gagea

---

### Post by anewguy on 2010-04-03
Be forewarned - I don't know anything about "R" except what it basically is.  However, I'm wondering if you go to user account management if perhaps there is a group for "R" users and you just need to add your userid to that group.  "Some" packages work that way - don't know about "R".

Dave ;)

---

