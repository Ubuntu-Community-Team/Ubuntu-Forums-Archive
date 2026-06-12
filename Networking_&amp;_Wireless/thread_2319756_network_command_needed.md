---
title: "network command needed"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by tidder2 on 2016-04-06
i have 2 interfaces bonded  how would you get the mac of the  interface for each connection
i can get all connections with :: netstat -an | grep -e  ":.*ESTABLISHED"
with out mac's

i want to have out put like :: eth0 or mac | source ip port | destination ip port

---

### Post by papibe on 2016-04-06
Hi tidder2. Welcome to the forum ):P

Try these commands:
```
ip link show

ifconfig
```
Hope it helps. Come here often and have fun.
Regards.

---

### Post by tidder2 on 2016-04-06
hi thanks 
i'm looking for something to tell me what interface each connection is going to

sumthing like this 
> 
eth0 tcp        192.168.0.101:32400     192.168.0.41:8193       ESTABLISHED
eth1 tcp        192.168.0.101:32400     192.168.0.62:37091      ESTABLISHED
eth0 tcp         192.168.0.101:4231      192.168.0.41:7609       ESTABLISHED
eth1 tcp         192.168.0.101:4231      192.168.0.41:8359       ESTABLISHED



---

### Post by papibe on 2016-04-07
This will show both macs and  IP addresses:
```
ip addr show
```
Regards.

---

