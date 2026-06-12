---
title: "getting room list for yahoo in pidgin..."
date: 2009-06-27
forum: New to Ubuntu
---

### Post by muctadir on 2009-06-27
i cant get room list from yahoo using the pidgin. if i click on the get list nothing happens. how can i solve the problem...???

---

### Post by s.fox on 2009-06-28
Hi,

[This]("http://developer.pidgin.im/ticket/6304") ticket was opened a while ago discussing the same problem.  Some suggestions were made as to how to fix.

Please post back if you still have troubles.

-Ash R

---

### Post by Paul T. on 2009-06-28
I used this link to fix problems in Pidgin: [http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)

mainly concerned with connection probs but seems to resolve room list too.

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

### Post by colau on 2009-08-15
> **muctadir said:**
> i cant get room list from yahoo using the pidgin. if i click on the get list nothing happens. how can i solve the problem...???
Which version of pidgin are you using?

---

