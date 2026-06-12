---
title: "trying to share internet"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by dannychampion on 2007-05-23
Trying to share the internet through a main pc.
Main pc has...

**Wired ethernet card --- eth0** (connects to router which shares to a laptop)

**Wireless ethernet card --- ra1** (connects to access point)

I am able to connect to access point, and reach the internet
I tried bridging the connections using many tutorials found online but no luck

I had this setup working with Windows XP (bridged connections --- overly easy)
Now the lovly days of right clicking seem to be gone :)

If anyone can point me in the right direction I would be more than greatfull.
Thanks :)

---

### Post by blazercist on 2007-05-23
I'm extremely confused? why would you be using a pc as a gateway when you have a router?  Why does the "main" pc need two connections to the router?  Maybe I just haven't had enough coffee this morning but I dont get it.

---

### Post by dannychampion on 2007-05-23
Here is a drawing.  Hope this helps

**Also**:  The access point is remote (a friend accross the street is sharing with me)

---

### Post by arvevans on 2007-05-23
In your present configuration you will have to set the PC to support "IP Forwarding".

A better configuration would be to have the router connect directly to your Internet access device and then put your own pc, any other local PC's, and the WiFi link downstream of the router.  That way the router can serve as your firewall, IP subnet distributer, DHCP server, etc.  This way the router will look to the ISP like it is the client device instead of your PC and the router will forward Internet traffic to all the downstream devices.

Arv
_._

---

### Post by dannychampion on 2007-05-23
Is their a way to connect the router to the  remote access point wirelessly???

---

### Post by blazercist on 2007-05-23
I see your problem, thats quite interesting.  I don't see how you would get the router connected to a wireless AP without a box in the middle... i think you should follow the advice about ip forwarding... ofcourse the easiest method would be a hard wire to the AP and use the router as the front line but as you put it thats not an option.

---

### Post by dannychampion on 2007-05-23
exactly....Thanks for the insight guys....as for the ip forwarding...Im not yet well versed in using the terminal.  Im currently in college learning UNIX.  Any suggestions on a tutorial?

---

### Post by dannychampion on 2007-05-23
And would i need to create a software network bridge to allow for ip forwarding?

---

### Post by blazercist on 2007-05-23
errr have you tried asking in #ubuntu on irc.freenode.net ?

I have no experience in network bridging and ip forwarding in linux I was always hardwired to AP with router as the gateway.

---

### Post by dannychampion on 2007-05-23
thanks

Ill head over there :)

Ill still be on the post, just incase anyone else has any ideas

---

