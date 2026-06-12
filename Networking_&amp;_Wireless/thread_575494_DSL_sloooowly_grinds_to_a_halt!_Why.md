---
title: "DSL sloooowly grinds to a halt! Why?"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by endre on 2007-10-14
Hey community, I have a small itch with a DSL network that I was hoping that you could help me with.

I've rented myself a room in south London while I'm in school here, and the landlord promised to offer wifi. Fine, he did, but it came in the form of a Netgear wireless router situated in the basement (with me on the top floor). Now I have solved the initial problem of distance and weak signal by having the router moved and buying a booster antenna for it, but it still has huge problems. Because every now and then, the internet connection, that is, not the connection to the router, but the internet itself completely grinds to a halt. The only thing that seems to work to fix it is to rip out the power cord to the router, wait a few minutes, and then restart it. Then it (usually) is back up again, for a while at least.

Although it may sound like this is a hardware problem not related to Ubuntu, I have found that it is much more prone to happen when I am running Ubuntu rather than Windows. Windows apparently needs a stronger signal, so until I got the booster antenna Ubuntu was doing this much better, but now that the signal problem is resolved, Ubuntu is lagging behind again.(although this morning rebooting the router helped neither system)

My system is an intel centrino laptop, running Feisty and XP - The connection is a DSL wireless from BT (British Telecom) I should also mention that other networks that are NOT based on DSL are fine, like my school wifi. That works like a charm no matter the system. There is also another tenant here sharing the same line, although I have shared DSL lines in the past with no major problem to speak of. Still, could that other person be using p2p software or something that would be messing this up?

Sorry for the long post, hope anyone has any ideas!

---

### Post by thelocust on 2007-10-14
This could be a bandwith problem since the whole building has access to it. Also if somebody is using P2P software the router trys to store all the routes and doesn't have enough memory so it freezes up. See if it has the latest firmware update.

---

### Post by endre on 2007-10-14
Ok, thanks, I agree this sounds like a bandwith problem, but the part about the routers memory clogging up/freezing also sounds very likely since rebooting it usually solves the problem. (and also, the router is pretty old, 3-4 years and I really doubt they have ever done anything to it in that time) Two more questions thoughr:

Is Ubuntu more likely to cause such clogging of the router memory than Windows? 

How do I check for the firmware? Can I do that through Ubuntu?

---

### Post by thelocust on 2007-10-14
1. Ubuntu should not be have more network activity than window if any thing I would guess the opposite.
 
2. go to the routers ip address usally 192.168.1.1 or 192.168.0.1 (just type it in the address bar on your web browser) this will either bring up some options or ask for a password if it ask for a password then do some research and find out what the default password is and hopefully they never changed it. But somewhere in the options it will tell you what the firmware version it is and you can check and see if thats the latest and greatest.

---

### Post by endre on 2007-10-14
Yea, they've changed it... Then I am basically left with yelling at the neighbors for using P2P software, or getting my own broadband connection.

Thanks anyways!

---

### Post by thelocust on 2007-10-14
If your really desperate givin the right tools no password can't be cracked.

---

### Post by endre on 2007-10-14
True, but I'll just grab hold of the landlord next time I see him, and see if he knows the password - until then I'll just have to keep pulling out that power cable and use the school network:-)

Thanks again!

---

