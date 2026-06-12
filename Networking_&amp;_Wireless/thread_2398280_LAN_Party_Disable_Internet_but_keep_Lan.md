---
title: "LAN Party: Disable Internet but keep Lan"
date: 2018-08-09
forum: Networking &amp; Wireless
---

### Post by thmtrxhsu on 2018-08-09
Basically during a LAN party I want to issue a command on each computer that will turn off internet while allowing LAN hosting and LAN joining.
What is the easiest way to achieve this.
The computer LAN address are in the 192.168.2 namespace (if I used that word correctly).
I would prefer a method without IPtables.

---

### Post by QIII on 2018-08-09
Hello!

What OS?  What router?

I would be reluctant to issue commands on other people's machines unless you want to take responsibility for undoing the changes or handling phone calls from the other users when there are unintended consequences noticed after people go home.

A brute force method would be to unplug your router from the wall.

Otherwise, you would have to see if you can make changes to the settings on your router to prevent certain machines from accessing the web.  That would be something you might have to look for in your router documentation.

I wouldn't make any changes to anyone's machines directly.

---

### Post by thmtrxhsu on 2018-08-09
Yes I guess a LAN party on a switch is the best bet.  Otherwise a firewall that blocks all connections except the one the game needs would accomplish the same.  How do I create a ufw rule to only allow a connection from a specific computer (more specific than IP i.e., computer name, mac address ), please give example.  Also since this will be for both mac and linux, what kind of script is compatible with both.

---

### Post by QIII on 2018-08-09
Are you using a computer as your router, or do you have a consumer router?

Again:  I would not make changes to anyone's computer directly.

---

### Post by thmtrxhsu on 2018-08-09
I am using a consumer router.

---

### Post by QIII on 2018-08-09
Make your changes there, then.

It's not your place to ask attendees to make such changes on their machines.

---

### Post by thmtrxhsu on 2018-08-09
Preposterous.  All machines are mine.

---

### Post by CharlesA on 2018-08-09
> **thmtrxhsu said:**
> Preposterous.  All machines are mine.

Right, but do you want to give everyone admin access so they can change their own settings?

If you want the machines to have LAN-only access, just connect everyone up to a switch, or disconnect the router from the internet and go nuts.

---

### Post by QIII on 2018-08-09
Assuming that you are doing that sort of unusual "LAN party" -- a sort which I have never encountered -- then if your router can't be set that way you could set up a VLAN, and set outbound rules to block the entire subnet from anything outside.

---

