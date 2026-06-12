---
title: "pidgin is not working?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by jhedd on 2009-07-01
How come pidgin is not working in ubuntu 9.04? pidgin is pre-installed but every time I try to use it, it never connects and I can't use it. Any ideas how to fix it? :lolflag:

---

### Post by halitech on 2009-07-01
which messenger are you trying to connect to? ie. Yahoo, msn, icq?

---

### Post by jhedd on 2009-07-01
I am trying to connect to Yahoo Messenger mate :lolflag:

---

### Post by kemsiro on 2009-07-01
it's til working for me 
try modify the page server to
**cn.scs.msg.yahoo.com**

---

### Post by jhedd on 2009-07-01
how do I do that?:lolflag:

---

### Post by kemsiro on 2009-07-01
Accounts -> Manage Accounts
Select your Yahoo Account and modify
Go to Advanced tab and edit the page server as the above address.

---

### Post by taw1978 on 2009-07-01
I'm having the same issue. I followed the instructions, but yahoo instant messenger is still not working on pidgin. Also, when I try to use my IM from the web, it doesn't work then either.

---

### Post by colau on 2009-07-01
From pidgin>Manage Account>Modify>Advanced set page server [COLOR="Red"]*scsa.msg.yahoo.com*[/COLOR]

---

### Post by jhedd on 2009-07-01
thnx kemsiro I think it is working now :guitar:

---

### Post by raymondh on 2009-07-01
Yahoo is starting to retire (or has retired) messenger versions 6 - 7.5. which has affected pidgin's functionality.  During this time, a lot of users have adapted by changing the server.  Some have used the 'mud' servers.  Some have routed thru china (cn).  And some have used the IP address.  In my case, I have used the ff:

cn.scs.msg.yahoo.com
66.163.181.170
66.163.181.170 scs.msg.yahoo.com

Pidgin now released 2.5.7 which is supposed to have fixed the connectivity problem.  I am now in 2.5.7 and have had to go back to 

scs.msg.yahoo.com

References:

[http://stuff.techwhack.com/6804-yahoo-messenger-pidgin](http://stuff.techwhack.com/6804-yahoo-messenger-pidgin)
[http://www.ymessengerblog.com/blog/2009/06/09/we%E2%80%99re-retiring-versions-60-to-75/](http://www.ymessengerblog.com/blog/2009/06/09/we%E2%80%99re-retiring-versions-60-to-75/)
[http://stuff.techwhack.com/6812-pidgin-2.5.7](http://stuff.techwhack.com/6812-pidgin-2.5.7)

Good luck and happy ubuntu-ing.

---

### Post by rezaghp on 2009-07-01
Update. Yahoo issues are fixed in 2.5.8.

---

### Post by misswham on 2009-07-02
i upgraded and used the ip address above and it works almost fine, i just notice now that whomever i am conversing with see some of my responses sometimes and others dont.  vice versa.  pidgin is reallly screwed up.  now i am using meebo.

---

### Post by zshuford on 2009-07-02
This is Canocial's fault, not Pidgin's.  You see, Ubuntu only provides security updates for Pidgin.  The problem is IM clients like Pidgin are often playing cat and mouse with IM providers like Yahoo that would really prefer that you used their Yahoo IM client, not Pidgin.  So recently Yahoo retired their old authentication method, which broke Pidgin.  It's fixed in the newer version, but you won't get the newer version with the update manager.

Fortunately, the fix is easy..


```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

Run those two commands, and then run Update Manager, and you should be god.

---

