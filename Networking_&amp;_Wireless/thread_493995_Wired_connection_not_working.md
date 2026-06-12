---
title: "Wired connection not working"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by clk99 on 2007-07-06
I just replaced my old linksys router with a wireless linksys router and now for some reason I can't get a wired connection on one of my Ubuntu desktops.  The other computer running Ubuntu in the house can connect fine.  I've compared the settings in NetworkManager and they look identical to me.  

I have no idea what could be the problem. NetworkManager just sits at "No network connection" after bootup.

I wish I could give more information but I'm a little short on time right now as I have to go to work, but I'll be back later in the day.  Any help would be greatly appreciated, thanks.

---

### Post by reckless2k2 on 2007-07-06
power down everything including your cable/dsl modem. reboot the modem 1st, then the router, then check to make sure all connections to and from the PC and router are fine, then power up the "bad" machine and see if you get a connection. then power up the "good" machine and see if you get a connection.

---

### Post by clk99 on 2007-07-06
No change.

I should add that the other ubuntu computer is currently connected via wireless, but the wired *does* work on it.  I also have a laptop running archlinux and another desktop running Vista, both of which work fine.  

And, just to be sure it wasn't a problem with the router or the cable, I tried my laptop upstairs where the unconnected computer is and it worked.

---

### Post by clk99 on 2007-07-06
Okay, I've made some progress.  I thought of popping in the Ubuntu live CD to see if it would work and it turns out it doesn't.  So I'm thinking it has to be the NIC or some conflict with the new router for some reason.  I'm going to try putting in an old NIC I have laying around and see what happens.  Be back soon.

---

### Post by clk99 on 2007-07-06
The new network card works fine.  I guess this wasn't an Ubuntu problem after all.  Now I'm going to have to buy another NIC for my audio workstation which has the same motherboard. :/

---

