---
title: "Cannot ping to my Gateway"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by million on 2009-09-07
Hi
 
I have configured two virtual ubuntu servers on my ubuntu 64-bit machine. 
My host machine has additional two ip's and those are configured to my virtual servers(guest) with bridge network
 
following are the details of my configuration in two servers.
 
server 1
----------------
ip-x.x.x.125
gateway - x.x.x1
 
 
server 2
-------------------
ip-x.x.x126
gateway-x.x.x1
 
my issue is from ip 125 I can access the gateway but from ip 126 I cannot ping to gateway address.
 
Can anyone help me?

---

### Post by Penguin Guy on 2009-09-07
Removing the x's would help. I'm guessing your using 192.168.1.* rather than your global ip address? Could you also run [COLOR="Green"]ifconfig[/COLOR] and post the results back here?

---

