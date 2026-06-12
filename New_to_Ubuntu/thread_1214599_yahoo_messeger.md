---
title: "yahoo messeger"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by vagelism on 2009-07-16
Hello to all.
There are days since I have a serious problem with pigin. It is not connecting to yahoo messeger. 
Do anyone know the solution to this problem?
If there is no solution, is there any alternative messeger that I can use in order to have yahoo on my pc.
Thank you all.

---

### Post by sisco311 on 2009-07-16
you have to upgrade to pidgin 2.5.8 

[http://pidgin.im/download/ubuntu/]("http://pidgin.im/download/ubuntu/")

---

### Post by zeroseven0183 on 2009-07-16
If you're using an older version than 2.5.7 of Pidgin, you'll probably gonna get the same error others encountered for the past few months. Updating it to the newest, I think it's 2.5.8 now, will help you solve the problem.

Check this out: [http://ubuntuforums.org/showthread.php?t=996366](http://ubuntuforums.org/showthread.php?t=996366)

---

### Post by vagelism on 2009-07-16
thank you it worked...!

---

### Post by brmc on 2009-07-31
yahoo people must have changed their server settings
 
 so just change advance settings
 replace scsa.msg.yahoo.com with  scs.msg.yahoo.com
 then it should be ok
 or u can install pidgin 2.5.8
 if u wana update your exciting pidgin,
 simply run these in terminal
 
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 
  echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
     sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
    
 then run the update manager 
 
 if u need more assistance 
 go to : [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)
 
 chinthaka bandara

---

### Post by llamabr on 2009-07-31
Weird.  This thread has been close for two weeks, and the solution you provide was given since that time.

---

