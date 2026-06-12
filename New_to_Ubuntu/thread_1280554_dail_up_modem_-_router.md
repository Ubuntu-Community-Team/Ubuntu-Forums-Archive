---
title: "dail up modem - router"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by George7a on 2009-10-02
Hi All,

I have configured my Ubuntu to automatically dial up on Start up in the past.

Now I have bought a router a, sometimes I connect through the router using a cable (not wireless).

When I am connected through a router, the automatic dial up still dials (and I would like to keep it that way - for now), the problem is that I can not connect to the internet through the router after that. How can I manually connect through the router then?

Can I configure it to try to connect to the modem, if it fails then connect through the router automatically? 

- George

---

### Post by braddcadd on 2009-10-02
[http://ubuntuforums.org/showpost.php?p=1444283&postcount=8](http://ubuntuforums.org/showpost.php?p=1444283&postcount=8)

I had a similar problem.  The above thread fixed my problem.  I had to determine the default gateway and then change it manually.

---

### Post by George7a on 2009-10-03
Thanks,

I have tried that but i still do not have internet through the router.

I even tried to got to 192.68.0.1 from firefox and I couldn't!

I read in your thread that I should try and run pppoeconf and it told me that the access concentrator of my provider did not respond.. check the cables or another running pppoeconf!

The cables are good.. and I could not see any pppoeconf processes runnging in the system monitor..

any ideas ?

---

### Post by George7a on 2009-10-03
after reading some posts I found that this command works for me:

> sudo dhclient eth0

I will try to restart again and check what happens

- George

---

