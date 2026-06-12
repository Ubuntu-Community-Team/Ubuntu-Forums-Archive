---
title: "connecting to nas"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by edgarzvl on 2010-08-21
Hello,

I am not only new to ubuntu but also new at network issues. 

I have ubuntu 10.04 installed sinds a few day's and i have difficulty entering my nas. In my Windows enviroment i go to [http://nas:5000](http://nas:5000) and then i get to enter my username and password and then i enter my nas.(ip 192.168.1.164)

In ubuntu however i can enter my nas only by going to "places" and choosing for "connect to server" . I then can see only my directories in the nas.  
What i want to do is enter the nas like i did in windows so that i can make some changes in the nas menu. 

I did some searches in the forum but most of them have sufficient knowledge on this matter and suggest things that i can not follow.

Can somebody help and please keep it very simple as i allready told i am very new at all this.

thx

---

### Post by gzarkadas on 2010-08-23
Try [http://192.168.1.164:5000](http://192.168.1.164:5000) from within your web browser; it should work (provided the ip, port combination you supply is accurate).

---

### Post by edgarzvl on 2010-08-24
Problem solved. Found that i had to add my IP and the name of my nas in the host file in dir /etc
After i did it everything worked well. Thanks for the input anyway.

---

