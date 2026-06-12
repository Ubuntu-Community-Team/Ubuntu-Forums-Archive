---
title: "Internet help..."
date: 2009-05-16
forum: New to Ubuntu
---

### Post by greatgreatnathan on 2009-05-16
Initially i was using ubuntu ultimate 1.8
But i feel there is a less net support for it.. as its site [www.ubuntuultimate.info]("http://www.ubuntuultimate.info") is not working for a long time.. :( i switched over to ubuntu 8.04 lts...
but now i can't connect to internet from there.!! i dont think the problem is with the net cos while installing hardy i got a dual boot with vista and i can connect to net thro vista perfectly fine...!! This post is only from vista so hope that proves  :D

can some one help me please..!!!

---

### Post by stilling on 2009-05-16
what type of connection do you have ? 
if pppoe open terminal and run sudo pppoeconf run the easy steps and that wil be all if something else post for other to know how to help you.

no offence

---

### Post by anewguy on 2009-05-16
If you are running wireless, you may just need to install the driver.  Do the following in a terminal window and post the output back here:

lspci

lsusb

lshw -C network

Dave :)

---

### Post by greatgreatnathan on 2009-05-16
no i have a bsnl broadband connection..!!
I dont know wat type it is.. sorry!! 
Its has a wired connection and i use eth port..!!

---

### Post by greatgreatnathan on 2009-05-16
> **stilling said:**
> what type of connection do you have ? 
if pppoe open terminal and run sudo pppoeconf run the easy steps and that wil be all if something else post for other to know how to help you.

no offence


Thanks a lot sir...
my problem resolved...
but can i know what i have done..??
hmmm sorry for the trouble... :)

---

### Post by stilling on 2009-05-21
you have a dsl connection that mens is pppoe type  you just triggerd that connection 
also you cand start the connection using sudo pon dsl-provider and terminated with poff

hope this help`s you

---

