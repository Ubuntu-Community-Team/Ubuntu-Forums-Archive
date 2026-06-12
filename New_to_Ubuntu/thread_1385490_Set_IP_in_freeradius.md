---
title: "Set IP in freeradius??"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by tha_minkee on 2010-01-19
Greetings All;
 
I have successfully installed freeradius/mysql/daloradius packages (thanks google) and all those who have written succinct how-to's.
 
All tutorials however instruct on how to configure servers to connect to localhost (127.0.0.1). I was hoping someone has some insight as to how to give the setup the ability to communicate with something other than my own pc, which I have statically assigned as 192.168.1.3.
 
Any help would be greatly appreaciated

---

### Post by tha_minkee on 2010-01-19
Perhaps a few more details might elicit a response.... all works fine after some minor tweaking (freeradius -X returns a "ready to accept....") which tells me that freeradius is working fine with the mysql modules.
 
Radtest works both through the daloradius gui and at the cli successfully authenticating my test user... :D . The radius server ip is 127.0.0.1
mysql ip is 127.0.0.1 both of which I need changed to a 192.168.x.x. 
 
I have a nas (separate box) which has its own localhost ip addy so it obv is not communicating with the freeradius/mysql localhost current config.
 
Is it just a matter of finding the right config files in mysql and FR ??[-o<
Any help would be grrrreat. TYTY I would ship $5 on Full Tilt to the first person who makes the post(s) to help me get this working

---

