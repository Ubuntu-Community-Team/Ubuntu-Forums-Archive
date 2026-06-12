---
title: "Ethernet Problems BCM4401-B0"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Speff on 2008-05-02
Ok, here's the situation: The ethernet controller was working when I installed Ubuntu initially. Then I decided I had it with the non-working wireless (BCM94311MCG), so I tried to fix it. Long story short, my wirelesss works now, but my wired does not. Weird, huh? 

I think it went out when I blacklisted the b43 driver (Now unblacklisted, still not working). When I restarted, I noticed I wasn't connected online anymore.

Help would be appreciated

EDIT: Sorry, I didnt mention my specs. I'm on Hardy on a Dell e1705 laptop

---

### Post by Speff on 2008-05-02
Still not resolved unfortunately. I saw in another thread the the dude's Ethernet connection wouldn't work because he blacklisted the b43 driver. I reinstalled it and it still doesn't work. This really is gettin to me.

---

### Post by Speff on 2008-05-03
Last bump before I ask this question in 3 months (Have access to a wireless spot at home, just not at the dorm)

---

### Post by Ayuthia on 2008-05-03
> **Speff said:**
> Ok, here's the situation: The ethernet controller was working when I installed Ubuntu initially. Then I decided I had it with the non-working wireless (BCM94311MCG), so I tried to fix it. Long story short, my wirelesss works now, but my wired does not. Weird, huh? 

I think it went out when I blacklisted the b43 driver (Now unblacklisted, still not working). When I restarted, I noticed I wasn't connected online anymore.

Help would be appreciated

EDIT: Sorry, I didnt mention my specs. I'm on Hardy on a Dell e1705 laptop
The module that you are most likely missing is the b44 driver.  It is removed in most of the fixes because of the ssb, but it is sometimes forgotten to be put back in. 

You will need to do a sudo modprobe b44 and your wireless should work again.  Most likely the ssb was loaded back, but b44 was not.  What should have been done was that b44 should have been put back instead of ssb.  

Hope that helps.  If I don't make any sense, please post your fix and I can tell you what needs to be fixed.

---

### Post by Speff on 2008-05-04
Ooh, that worked. When people kept alternating between b43 and b44, I got confused and just assumed that they were mixing the two up, :lolflag:. Well, it works now, thanks alot!

---

### Post by Feenix3k on 2008-05-23
On my Dell 5150 the wired card is BCM4401, my wireless is BCM4309. In Hardy it stated with the wired working. Once I get the wireless working the wired stoped working. So I dont know whats going on.

---

