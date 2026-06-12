---
title: "Wireless Issue"
date: 2005-04-04
forum: Networking &amp; Wireless
---

### Post by silentstriker on 2005-04-04
I have two connections:

1) Connection at work with my ethernet port
2) Connection at university which is wireless

Both are DHCP, but when I hook up the wired connection at work, it works right away, like its supposed to.


At school, however, it's spotty.  Frequenty I have to disable/enable the connection for 30-40 mins, before it succesfully connects, and sometimes it never connects at all..  A lot of time, it freezes when I try to activate/deactivate it using network-admin. First I thought it was the network itself, but as soon as I boot into windows, everything just works.

What can I do?

---

### Post by Strider on 2005-04-04
Open up a terminal and run "ifdown eth0" (assuming eth0 is your wired connection), and then "ifup eth0".  It should tell you if you're having any issues obtaining a DHCP address.

---

### Post by sfw5000 on 2005-04-05
You might want to post the results of bringing the interface up, as well as your ifconfig -a and iwconfig, so we can see what your set up is like. With the wireless connection their could be a bunch of things going wrong... That's usually a good place to start.

hth,

Sam

---

