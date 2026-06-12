---
title: "Connecting two computers with one ethernet cable - no router"
date: 2020-03-19
forum: Networking &amp; Wireless
---

### Post by michael351 on 2020-03-19
I want to connect two Linux computers via one ethernet cable without a router. 
I set each NIC card's IP manually as 10.0.0.1 and 10.0.0.2
netmask as 255.255.255.0
and default gateway for both as 10.0.0.1

The NIC's show connected but ping yields 100% packet loss - no transfer of data working.

what am I missing? failing to do?

Thanks

update: found this: [https://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](https://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router)
solved my problem - thanks to this forum!

---

### Post by TheFu on 2020-03-19
>  and default gateway for both as 10.0.0.1
That's the problem.
Each system needs to point at the other for the default gateway - and both need to have GigE Nics that autosense if a regular CAT5e or cross-over CAT5e cable is being used.

if this is solved, please, please, please use the **Thread Tools button** and mark it _SOLVED_.  Don't have people waste their time.  Please.

---

### Post by The Cog on 2020-03-19
> Each system needs to point at the other for the default gateway
I disagree with that. They are both on the same subnet, so they don't even need a router. They can just ARP each other.

It may be a cabling issue. Use the command "ip address" to check the addresses are what you say, and look for LOWER_UP which means the NIC says the cable is OK. If it says UP but not LOWER_UP then there is a cable problem and the NIC thinks there's no receive signal.

---

### Post by TheFu on 2020-03-20
> **The Cog said:**
> I disagree with that. They are both on the same subnet, so they don't even need a router. They can just ARP each other. 

I've never seen this work after 20+ attempts over the decades. Yes, it should work. I agree.  When auto-negotiation became standard with the GigE specs, at least we didn't need a cross-over cable anymore.

---

### Post by michael351 on 2020-03-20
Thanks for the "thread tools button" reference. I didn't know. This problem is solved and is now indicated as such using the button. No crossover cable necessary as the NIC's autosense.

---

### Post by The Cog on 2020-03-21
Out of interest, and because it may help others with the same problem, what was the fix? Doesn't matter if it's really mundane.

---

### Post by hk42 on 2020-03-22
I totally agree with that .
It is misleading to mark a topic "solved" if there is no trace of the solution in it.

---

### Post by VMC on 2020-03-22
I think the solution he found is the #1 post at the bottom. He updated his post when the solution was found.

---

