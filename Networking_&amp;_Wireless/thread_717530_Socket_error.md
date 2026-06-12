---
title: "Socket error"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by tgero on 2008-03-07
Hello, 
I have installed on my system Ubuntu 7.10 and i downloaded nfdump and installed it from my repository to monitor my network flow. I tried starting the nfdump netflow capture deamon on the terminal and this is the error message i got. 
 
:~$ /etc/init.d/nfdump start 
Socket error: could not open the requested socket 
Terminated due to errors. 

i also tried using the sudo but it still reported thesame error
 
Please can you assists me.

Tarini Gero

---

### Post by jeffus_il on 2008-03-07
Does it maybe need sudo? That is privileges? Try
```
sudo /etc/init.d/nfdump start 
```

---

### Post by tgero on 2008-03-07
I tried sudo but still thesame error.
Any ideas?

---

### Post by jeffus_il on 2008-03-07
Seems like there is someone else with the same problem and no response from their forum:
[http://sourceforge.net/forum/forum.php?thread_id=1960724&forum_id=407480](http://sourceforge.net/forum/forum.php?thread_id=1960724&forum_id=407480)
Is that you?
There are plenty network monitoring tools, why not try something with better support and/or ducumentation/wiki?

---

### Post by tgero on 2008-03-10
Hi Jeffus_il
Thats me alright, the thing is Nfdump is the required tool for the project i'm trying to do here so i can't go for another monitoring tool. thanks so much for ur inputs.

---

