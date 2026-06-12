---
title: "Can't get 10.4 to connect to the network"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by mminorhsd on 2010-05-27
I recently installed 10.4 on a dell Optiplex 60 pc,devoting the entire system to ubuntu. I have ubuntu up and running and can do most things in it just fine so far.

The problem is that when I try and connect to my router, a Linksys BEFW1154, using a cable, it fails and gives me a message that the wired network is disconnected.

One post I found said to try pinging 127.0.0.1 to test the nic, and that comes back ok.

ifconfig -a seems to produce what I would expect it to.

I looked at /etc/network/interface and it shows what all of the other posts says it should. 

I have tried ifconfig eth0 down and ifconfig eth0 up, to no avail.

I have powered the router off and on several times. The router uses DHCP, and has 50 ports allocated, so I'm not out of slots on the router. I tried different cables including one that I know works, because it is the same cable the computer I'm typing on uses it.

I modified the properties of eth0 to use DHCP automatically.

I have been searching other posts on this forum site for 10 days, and still haven't found the right piece of information to get me going. I've tried so many things I found in posts, but I can't remember them all.

Any help will be greatly appreciated.

Thanks

Mike

---

### Post by mminorhsd on 2010-05-28
I found the problem. I disabled ipv6 for eth0 and it worked immediately.

---

### Post by Gone fishing on 2010-05-28
If you run ifconfig do you find eth0 and is itbeing given an ip address?

---

### Post by mminorhsd on 2010-05-28
It is now that I disabled ipv6. Thanks for your response.

---

### Post by SKhan on 2010-05-28
i installed ubuntu on dell optiplex gx270 and it connected immediately. no ipv6 problems. ;)

---

### Post by mminorhsd on 2010-05-28
Guess I was just unlucky. My son installed it on an old dell laptop, and his network cable connection worked fine, but he had trouble getting his wireless to work. He finally got that going to....

---

### Post by sadaruwan12 on 2010-05-28
> **mminorhsd said:**
> Guess I was just unlucky. My son installed it on an old dell laptop, and his network cable connection worked fine, but he had trouble getting his wireless to work. He finally got that going to....

Ahhh.... good well come to Ubuntu and like to say it seems like you've solved your problem please mark it as solved from thread tools.

---

### Post by mminorhsd on 2010-05-28
Done....still new to the group and learning the ropes.....

---

