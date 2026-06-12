---
title: "SSH Timeout on New Router"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by nomexous on 2008-06-09
I have two computers: a laptop running a normal install of Hardy, and a headless desktop, running Hardy without X. The headless computer has no screen or keyboard, and is administered by SSH from my laptop. I set it all up at home on a Netgear router, plugging the headless computer directly into the router, and accessing it with the laptop on wireless.

Then comes the time to move into school. I buy a Belkin router and proceed to bring everything to school. However, after setting up the router, I find that I can no longer SSH into my headless machine. Before, I simple did "ssh 192.168.0.x" (whatever x happened to be). I do the same thing, but now it simple sits there. After a while, it will say that it timed out.

I am able to ping my headless install, but cannot SSH to it? What gives? Could it be my new router setup? I don't have a separate monitor or keyboard, so I won't be able to do anything with the headless machine unless I can get SSH working. Anyone had a similar experience with SSH and Belkin routers? Any help or insight is appreciated.

Belkin G Wireless Router (F5D7230-4)

---

### Post by paulstarr on 2008-06-09
Sounds like the SSH service has not started. 


I suggest a monitor + Keyboard and then /etc/init.d/ssh status


I dont believe that Belkin would stop ssh but allow ping.

---

### Post by nomexous on 2008-06-09
The problem is that I don't have a keyboard or monitor to plug in. Also, SSH has started up every other time. There's no reason to think that it has spontaneously stopped working.

---

### Post by paulstarr on 2008-06-10
I don't believe that your belkin is set to stop port22 traffic, however worth checking. Also does this belkin allow you to tcpdump? if so you will want to check if you see returning packets from the monitorless PC.

I believe that it is something on your machine that is dropping the traffic but until you have a monitor and keyboard then there is not a lot you can do.

---

### Post by hyper_ch on 2008-06-10
So, at school you have also a LAN where yuo and the headless server are both connected to the belkin router?

---

### Post by nomexous on 2008-06-10
Yes, both my laptop and the headless server are on the same LAN.

I don't think that the Belkin router allows tcpdump. I tried tracerouting to 192.168.0.3 (IP of the headless machine), but each packet it sent timed out. I even tried tracerouting the router. Same thing.

---

### Post by nekator on 2008-06-10
I have the same problem, been using Unison to sync several computers at work without a problem for over a year now. Sometime last week (or the week before) things stopped working. SSh sits there attempting to connect and after a couple of minutes times out. Unison attempts to connect but also times out. When I ping the server (where the files are synced to) I get routing information, packet reception and even netstat working. ssh via terminal does nothing. I though it had to do with the IT guys fiddling with the main server security packages over the weekend but now I think its just Hardy. Any help would be appreciated.

---

