---
title: "Change Default Route"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by CharlieNixon on 2007-09-12
I'd like to change my default route. I've tried the command:

route add default gw x.x.x.x

but it returns the error "SIOCADDRT: Network is unreachable". I can ping the address with no problems. What am I missing?

---

### Post by noob12 on 2007-09-13
If you have multiple interfaces and if you're connected on say eth1 or wlan0, and  eth0 is not connected, you can get that kind of error if you don't specify the interface on the command. This would be the qualified command for eth1 for example:
```

sudo route add default gw x.x.x.x eth1

```
Also make sure you are doing it as root (e.g.sudo).

---

### Post by CharlieNixon on 2007-09-13
Specifying the interface doesn't seem to change anything. I just don't understand why I get a destination unreachable error when I can clearly ping the IP. The only thing I can think of is that the architecture of the network has changed and the IP I'm specifying is no longer a router.

---

### Post by noob12 on 2007-09-13
It doesn't really go out and check if that address is a router.  Basically you need to check that the interface is UP and has an address and subnet such that the router address is on that immediate subnet.

So maybe if you post the information from **ifconfig -a**  and your router address, we'd see the specific problem.

---

### Post by mips on 2007-09-13
A default route usually means your x.x.x.x=0.0.0.0. Are you not maybe referring to a static route ?

---

### Post by noob12 on 2007-09-13
We are talking about a default gateway.  The destination is anything (anything that is not covered by any other route), the router is specific.

---

### Post by CharlieNixon on 2007-09-17
> **noob12 said:**
> It doesn't really go out and check if that address is a router.  Basically you need to check that the interface is UP and has an address and subnet such that the router address is on that immediate subnet.


I think you're right and that's what I meant. I shouldn't have said "it's no longer a router" that didn't make any sense. I should have said, the router has been moved. 

I know the interface still exists and is up (I can ping it), I think what happened is the router has been moved to a new location (network wise) on the external side of an intermediary router (so it used to look like this: me --> desired gateway and now it looks like this: me --> new gateway --> desired gateway).

Anyway, my question was just to clarify the command was correct and that the problem was not on my system. I've since used the command to succesfully change my default gateway, so I know it works (not to the original desired address, mind you). No need to post my configs and what not. I'm good to go.

Thanks for all the input!

---

