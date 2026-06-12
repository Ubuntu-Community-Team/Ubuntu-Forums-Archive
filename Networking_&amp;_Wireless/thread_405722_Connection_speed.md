---
title: "Connection speed"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by MrZehl on 2007-04-10
My internet connection speed has lowered drasticly the last days. I phoned my provider and even with a clean reboot and no other programs started to much packages were sent.
According to the provider this points to vrus or spyware, so the advised me to check my computer for this. Of course they only support windows systems so it's up to me now.
I thought that Linux was quite safe for spyware and virusses but it seems something is filling my bandwidth. I'm using Ubuntu Feisty. 
How can I find what program is using my bandwidth?

---

### Post by koshari on 2007-04-10
i would doubt it would be spyware/virii, more likely that a peer to peer proggie plugging away at your bandwidth!

---

### Post by MrZehl on 2007-04-10
> **koshari said:**
> i would doubt it would be spyware/virii, more likely that a peer to peer proggie plugging away at your bandwidth!

I doubt it too, but something is eating my bandwidth. But as I said a clean boot with nothing started was eating my bandwith. No p2p program was active.

---

### Post by josephus on 2007-04-10
not sure if there is a better way, but you could use netstat to see your current connections
```

netstat -t -p
```
to limit to TCP connections and to show which program is using the socket.

---

