---
title: "What In The World Is This IP?"
date: 2015-12-16
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2015-12-16
I'm just curious about this IP I see in Terminal running a netstat -ntu | awk '/ESTABLISHED/{print $5;}' .  The IP is ::1:50884 !  I know it's not a loopback so could someone please explain this to me!

You'll see it here.

---

### Post by bab1 on 2015-12-16
> **shane_faulkinbury2 said:**
> I'm just curious about this IP I see in Terminal running a netstat -ntu | awk '/ESTABLISHED/{print $5;}' .  The IP is ::1:50884 !  I know it's not a loopback so could someone please explain this to me!

This is the IPv6 loopback address.  If you run the command without the pipe to awk (or at least add $1) you will see something like this```

netstat -ntu 
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
...
tcp6       1      0 ::1:34379               ::1:631                 CLOSE_WAIT 
```

The prefix ::1 is the truncated way of showing the loopback IPv6 address.  Everything after the : is the tcp6 port number.  The tcp/ tcp6 port is for CUPS (common unix print sever).

---

### Post by shane_faulkinbury2 on 2015-12-16
Thanks bab1!

---

