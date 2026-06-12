---
title: "Bridging and pppoe"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by damansandhu on 2007-08-14
HI , i am using dsl connection , i am using internet in linux via ppp over ethernet(pppoe)
in which username and password are stored in router , you just turn on router and internet is connected automatically , 
but i want to connect internet manually as i do in win xp via bridging which means by manually connecting by inserting username and password , just like dialup connection . 

somebody plz help me out.

---

### Post by thelinuxguy on 2007-08-14
[list="1"]
[*]Put your router in bridge mode. This is router specific and your router documentation should outline the process. But if you are already doing it with XP, this may not be necessary.
[*]Run pppoeconf. It will run a wizard with screens to configure your connection. It will also tell you what commands you need to start/stop the connection and also to view status of the connection.
[*]If pppoeconf is not able to connect via your router and reports "access concentrator" related errors, you may need the rp-pppoe protocol stack, Install rp-pppoe from [here]("http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe").
[/list]

Let me know if it works,

---

