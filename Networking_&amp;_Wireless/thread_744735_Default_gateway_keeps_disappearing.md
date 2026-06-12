---
title: "Default gateway keeps disappearing"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2008-04-03
A couple days ago my laptop started losing it's internet connection, but my service was fine I finally tracked the problem down to a route problem. Every 2-3 minutes the gateway route disappears. I thought it was a network manager problem so I disabled it and manually set up a static ip using these commands.

ifconfig eth0 1.1.1.2 up
route add default gw 1.1.1.1 eth0

But the same problem still happens and I just have to run the second command again to go online for a couple more minutes. This happens whether I am wired or wireless. I have not added any software in along time so that could not of affected this. What could of caused this and how can I stop this behavior. So I don't have to reformat before 8.04 comes out.

---

### Post by renfrew on 2008-04-04
I'm assuming this is a wireless connection in that you're on a laptop... how's your signal strength to the laptop?   have you tried changing the broadcast channel on your router?   maybe play around with the broadcasting strength of your routers antenna.  I had a new neighbour move into my area recently and had to go through these steps in order to get my grilfriends laptop to connect decently.. you could just have some competition for your local airwaves.....

---

### Post by darkshadow on 2008-04-04
That is not the problem, This occurs using both wired and wireless.

---

