---
title: "Wierd ping"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by BatteryCell on 2006-08-01
Alright, I can ping places like google.com and myself, however if I try to ping a friend I get:
```

4 packets transmitted, 0 received, 100% packet loss, time 3000ms

```
The same thing happens if my friend trys to ping me.
Any ideas on why this is happening??
Oh and I'm just using the automatic configuration for my connection.

---

### Post by scxtt on 2006-08-01
i think you have to allow your box to be pingable, i can't ping my box from an IP that i have firestarter allowing ... so that seems normal ...

---

### Post by BatteryCell on 2006-08-01
Hmm the reason I ask is because he cant ssh to my computer and I was wondering if maybe the ping problem has something to do with it...

---

### Post by scxtt on 2006-08-01
i don't think so, i can ssh (from work, the allowed IP) to my box @ home - but can't ping from that IP ...

not being able to SSH could be the result of various problems (firewall, port forwarding, not having an openssh-server installed) ...

---

### Post by BatteryCell on 2006-08-02
Hmm yea I just checked and it apears my port 22 is filtered...but I dont know whats filtering it.

---

### Post by bensexson on 2006-08-02
Are you using a router?

---

### Post by BatteryCell on 2006-08-02
yes but acording to it its not filtering anything...and my firewall has port 22 open as well.

---

### Post by BatteryCell on 2006-08-02
Ah, I had to port forward it...lol Im feelin so noobish right now :-/

---

### Post by scxtt on 2006-08-02
it happens, but it should make you feel good that your router is doing its job :)

---

### Post by BatteryCell on 2006-08-03
Yea thats it, my routers doin its job :-P

---

