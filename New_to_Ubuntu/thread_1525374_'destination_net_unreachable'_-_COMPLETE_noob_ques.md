---
title: "'destination net unreachable' - COMPLETE noob question"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-07-06
I feel dumb for even asking this....but can someone explain to me when given this output ```
>ping 10.1.10.4

Pinging 10.1.10.4 with 32 bytes of data:

Reply from 10.1.10.4: Destination net unreachable.
Reply from 10.1.10.4: Destination net unreachable.
Reply from 10.1.10.4: Destination net unreachable.
Reply from 10.1.10.4: Destination net unreachable.

Ping statistics for 10.1.10.4:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

After trying to ping a switch, the switch itself appears to come back and say that it can't reach itself?  o.O 


My default gateway is 10.1.10.1, and it's in the same subnet, I believe.


Any help is definitely appreciated! :)

---

### Post by jtarin on 2010-07-06
[Information for edification]("http://www.firewall.cx/icmp-dest-unreachable.php")
Post teminal command results ```
route -n
```

---

### Post by B34ST1Y on 2010-07-06
It's on a windows machine. The problem has been resolved. 


For reference purposes, the issue was that the host itself wasn't allowing my (the sender) IP in the access list...and it wasn't told not to send ICMP replies.


:)

---

### Post by jtarin on 2010-07-06
Windows machine....ACCCK!

---

### Post by Iowan on 2010-07-06
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?  :)

---

