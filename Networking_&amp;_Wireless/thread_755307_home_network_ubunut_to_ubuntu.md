---
title: "home network ubunut to ubuntu"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Lukios on 2008-04-14
Just to start off, im new to linux and ubuntu in general, so i know very little. My question is this, on windows you can set up a home network to share internet without a router, via 10/100 to 10/100 either net cards. modem ----->comp 1-------crossover cable----->comp 2. maybe i could i have missed it, but everywhere i look i cant find a set of directions or a tutorial that either gives good, newb directions that dont assume you know everything about linux, or one that just simply works. so if some one could give me some step by step instructions in settting up a home net work for my 2 ubuntu computers, i would really appreciate it.

using ubuntu 7.10 on both computers

---

### Post by dstew on 2008-04-14
[This Blog entry ]("http://www.ax697.org/sharing-internet-connection-with-a-crossover-cable-2008238.html")seems pretty straightforward. You set up the interface by editing your /etc/network/interfaces file, which is the configuration file read by the networking software.

---

### Post by Lukios on 2008-04-14
didnt work . . .

---

### Post by superprash2003 on 2008-04-14
[http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29) read this .. make sure you change eth0 or eth1 accordingly based on your setup

---

### Post by Lukios on 2008-04-14
ok so this is what i found out, so far i have been doing everything right as far as i can tell, i set seperate ips to each computer such as 192.168.0.1 and 192.168.0.2 and set the default gate way to the first computer being 192.168.0.1. in theory this all should work, however, i still cant access the internet on the other computer. I can ping each computer but i can ping websites from the second computer.

im not sure if this will help any but, i have open roam enabled on my internet conection eth0, setting up dhcp wont give me internet even on this computer. 

this kinda reminds me of windows "limited connectivity" issues, but those are usually caused by firewalls or wrong cables, and or can be fixed by repairing the connection. not sure if any of the same concepts would apply, however i can tell you i have firestarter as my firewall and i am using a crossover cable to network the two computers.

any ideas . . .

---

### Post by Lukios on 2008-04-14
alright guys, i feel like an idiot, but after leaving my last post and thinking about everything i just wrote, the only other thing that it could be is my dns, sure enough that was it. 

thank you guys for sending me those pages they were a great help.

---

